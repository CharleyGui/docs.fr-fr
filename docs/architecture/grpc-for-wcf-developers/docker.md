---
title: Docker-gRPC pour les développeurs WCF
description: Création d’images d’ancrage pour les applications ASP.NET Core gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: cc369da9494ade532187dfc8d19a94a3a037ebab
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846681"
---
# <a name="docker"></a><span data-ttu-id="a6656-103">Docker</span><span class="sxs-lookup"><span data-stu-id="a6656-103">Docker</span></span>

<span data-ttu-id="a6656-104">Cette section traite de la création d’images de l’arrimeur pour les applications ASP.NET Core gRPC, prêtes à être exécutées dans un environnement d’ancrage, de Kubernetes ou d’autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="a6656-104">This section will cover the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="a6656-105">L’exemple d’application utilisé, avec une application Web ASP.NET Core MVC et un service gRPC, est disponible sur le référentiel [dotnet-architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="a6656-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="a6656-106">Images de base Microsoft pour les applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a6656-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="a6656-107">Microsoft fournit une gamme d’images de base pour la création et l’exécution d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a6656-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="a6656-108">Pour créer une image ASP.NET Core 3,0, deux images de base sont utilisées : une image du kit de développement logiciel (SDK) pour générer et publier l’application, ainsi qu’une image d’exécution pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="a6656-108">To create an ASP.NET Core 3.0 image, two base images are used: an SDK image to build and publish the application, and a runtime image for deployment.</span></span>

| <span data-ttu-id="a6656-109">Image</span><span class="sxs-lookup"><span data-stu-id="a6656-109">Image</span></span> | <span data-ttu-id="a6656-110">Description</span><span class="sxs-lookup"><span data-stu-id="a6656-110">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="a6656-111">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="a6656-111">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="a6656-112">Pour créer des applications avec `docker build`.</span><span class="sxs-lookup"><span data-stu-id="a6656-112">For building applications with `docker build`.</span></span> <span data-ttu-id="a6656-113">À ne pas utiliser en production.</span><span class="sxs-lookup"><span data-stu-id="a6656-113">Not to be used in production.</span></span> |
| [<span data-ttu-id="a6656-114">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="a6656-114">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="a6656-115">Contient le runtime et les dépendances de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a6656-115">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="a6656-116">Pour la production.</span><span class="sxs-lookup"><span data-stu-id="a6656-116">For production.</span></span> |

<span data-ttu-id="a6656-117">Pour chaque image, il existe quatre variantes basées sur différentes distributions Linux, distinguées par des balises.</span><span class="sxs-lookup"><span data-stu-id="a6656-117">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="a6656-118">Balise (s) d’image</span><span class="sxs-lookup"><span data-stu-id="a6656-118">Image tag(s)</span></span> | <span data-ttu-id="a6656-119">Linux</span><span class="sxs-lookup"><span data-stu-id="a6656-119">Linux</span></span> | <span data-ttu-id="a6656-120">Notes</span><span class="sxs-lookup"><span data-stu-id="a6656-120">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="a6656-121">3,0-Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="a6656-121">3.0-buster, 3.0</span></span> | <span data-ttu-id="a6656-122">Debian 10</span><span class="sxs-lookup"><span data-stu-id="a6656-122">Debian 10</span></span> | <span data-ttu-id="a6656-123">Image par défaut si aucun variant de système d’exploitation n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="a6656-123">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="a6656-124">3,0-Alpine</span><span class="sxs-lookup"><span data-stu-id="a6656-124">3.0-alpine</span></span> | <span data-ttu-id="a6656-125">Alpine 3,9</span><span class="sxs-lookup"><span data-stu-id="a6656-125">Alpine 3.9</span></span> | <span data-ttu-id="a6656-126">Les images de base Alpine sont plus petites que les images Debian ou Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a6656-126">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="a6656-127">3,0-Disco</span><span class="sxs-lookup"><span data-stu-id="a6656-127">3.0-disco</span></span> | <span data-ttu-id="a6656-128">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="a6656-128">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="a6656-129">3,0-Bionic</span><span class="sxs-lookup"><span data-stu-id="a6656-129">3.0-bionic</span></span> | <span data-ttu-id="a6656-130">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a6656-130">Ubuntu 18.04</span></span> | |

<span data-ttu-id="a6656-131">L’image de base alpine est d’environ 100 Mo, par rapport à 200 Mo pour les images Debian et Ubuntu, mais certains packages ou bibliothèques logicielles peuvent ne pas être disponibles dans la gestion des packages de Alpine.</span><span class="sxs-lookup"><span data-stu-id="a6656-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images, but some software packages or libraries may not be available in Alpine's package management.</span></span> <span data-ttu-id="a6656-132">Si vous n’êtes pas certain de l’image à utiliser, il est préférable de respecter le Debian par défaut, sauf si vous avez besoin d’utiliser un autre distribution.</span><span class="sxs-lookup"><span data-stu-id="a6656-132">If you're not sure which image to use, it's best to stick to the default Debian unless you have a compelling need to use a different distro.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6656-133">Veillez à utiliser la même variante de Linux pour la build et le Runtime.</span><span class="sxs-lookup"><span data-stu-id="a6656-133">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="a6656-134">Les applications générées et publiées sur une seule variante peuvent ne pas fonctionner sur une autre.</span><span class="sxs-lookup"><span data-stu-id="a6656-134">Applications built and published on one variant may not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="a6656-135">Créer une image d’ancrage</span><span class="sxs-lookup"><span data-stu-id="a6656-135">Create a Docker image</span></span>

<span data-ttu-id="a6656-136">Une image de l’arrimeur est définie par un *fichier dockerfile*, un fichier texte qui contient toutes les commandes nécessaires à la génération de l’application et à l’installation des dépendances requises pour la génération ou l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="a6656-136">A Docker image is defined by a *Dockerfile*, a text file that contains all the commands that are needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="a6656-137">L’exemple suivant illustre la fichier dockerfile la plus simple pour une application ASP.NET Core 3,0 :</span><span class="sxs-lookup"><span data-stu-id="a6656-137">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="a6656-138">Le fichier dockerfile a deux parties : le premier utilise l’image de base `sdk` pour générer et publier l’application. le deuxième crée une image d’exécution à partir de la base de `aspnet`.</span><span class="sxs-lookup"><span data-stu-id="a6656-138">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="a6656-139">Cela est dû au fait que l’image `sdk` est d’environ 900 Mo par rapport à environ 200 Mo pour l’image d’exécution, et que la plupart de son contenu n’est pas nécessaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a6656-139">This is because the `sdk` image is around 900 MB compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="a6656-140">Étapes de génération</span><span class="sxs-lookup"><span data-stu-id="a6656-140">The build steps</span></span>

| <span data-ttu-id="a6656-141">Étape</span><span class="sxs-lookup"><span data-stu-id="a6656-141">Step</span></span> | <span data-ttu-id="a6656-142">Description</span><span class="sxs-lookup"><span data-stu-id="a6656-142">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="a6656-143">Déclare l’image de base et assigne l’alias de `builder` (consultez la section suivante pour obtenir des explications).</span><span class="sxs-lookup"><span data-stu-id="a6656-143">Declares the base image and assigns the `builder` alias (see next section for explanation).</span></span> |
| `WORKDIR /src` | <span data-ttu-id="a6656-144">Crée le répertoire `/src` et le définit comme répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="a6656-144">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="a6656-145">Copie tout ce qui se trouve sous le répertoire actif sur l’hôte dans le répertoire actif de l’image.</span><span class="sxs-lookup"><span data-stu-id="a6656-145">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="a6656-146">Restaure tous les packages externes (ASP.NET Core 3,0 Framework est préinstallé avec le kit de développement logiciel (SDK)).</span><span class="sxs-lookup"><span data-stu-id="a6656-146">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="a6656-147">Génère et publie une version Release.</span><span class="sxs-lookup"><span data-stu-id="a6656-147">Builds and publishes a Release build.</span></span> <span data-ttu-id="a6656-148">Notez que l’indicateur `--runtime` n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="a6656-148">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="a6656-149">Étapes de l’image d’exécution</span><span class="sxs-lookup"><span data-stu-id="a6656-149">The runtime image steps</span></span>

| <span data-ttu-id="a6656-150">Étape</span><span class="sxs-lookup"><span data-stu-id="a6656-150">Step</span></span> | <span data-ttu-id="a6656-151">Description</span><span class="sxs-lookup"><span data-stu-id="a6656-151">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="a6656-152">Déclare une nouvelle image de base.</span><span class="sxs-lookup"><span data-stu-id="a6656-152">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="a6656-153">Crée le répertoire `/app` et le définit comme répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="a6656-153">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="a6656-154">Copie l’application publiée à partir de l’image précédente, à l’aide de l’alias `builder` de la première ligne de `FROM`.</span><span class="sxs-lookup"><span data-stu-id="a6656-154">Copies the published application from the previous image, using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="a6656-155">Définit la commande à exécuter lorsque le conteneur démarre.</span><span class="sxs-lookup"><span data-stu-id="a6656-155">Sets the command to run when the container starts.</span></span> <span data-ttu-id="a6656-156">La commande `dotnet` dans l’image d’exécution peut uniquement exécuter des fichiers DLL.</span><span class="sxs-lookup"><span data-stu-id="a6656-156">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="a6656-157">HTTPs dans l’ancrage</span><span class="sxs-lookup"><span data-stu-id="a6656-157">HTTPS in Docker</span></span>

<span data-ttu-id="a6656-158">Les images de base de Microsoft pour l’arrimeur définissent la variable d’environnement `ASPNETCORE_URLS` sur `http://+:80`, ce qui signifie que Kestrel s’exécutera sans HTTPs sur ce port.</span><span class="sxs-lookup"><span data-stu-id="a6656-158">Microsoft's base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel will run without HTTPS on that port.</span></span> <span data-ttu-id="a6656-159">Si vous utilisez le protocole HTTPs avec un certificat personnalisé (comme décrit dans [la section précédente](self-hosted.md)), vous devez le remplacer en définissant la variable **d’environnement dans la partie création** de l’image du runtime de votre fichier dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a6656-159">If you're using HTTPS with a custom certificate (as described in [the previous section](self-hosted.md)), you should override this by setting the environment variable **in the runtime image creation part** of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="a6656-160">Fichier. dockerignore</span><span class="sxs-lookup"><span data-stu-id="a6656-160">The .dockerignore file</span></span>

<span data-ttu-id="a6656-161">À l’instar des fichiers `.gitignore` qui excluent certains fichiers et répertoires du contrôle de code source, le fichier `.dockerignore` peut être utilisé pour exclure des fichiers et des répertoires d’être copiés dans l’image pendant la génération.</span><span class="sxs-lookup"><span data-stu-id="a6656-161">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="a6656-162">Cela permet non seulement de gagner du temps, mais également d’éviter certaines erreurs confuses dues à l’utilisation (en particulier) du répertoire `obj` de votre ordinateur copié dans l’image.</span><span class="sxs-lookup"><span data-stu-id="a6656-162">This not only saves time copying, but can also avoid some confusing errors that arise from having (particularly) the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="a6656-163">Vous devez ajouter au moins des entrées pour `bin` et `obj` à votre fichier `.dockerignore`.</span><span class="sxs-lookup"><span data-stu-id="a6656-163">You should add at least entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="a6656-164">Générer l’image</span><span class="sxs-lookup"><span data-stu-id="a6656-164">Build the image</span></span>

<span data-ttu-id="a6656-165">Pour une solution avec une seule application, et donc une seule fichier dockerfile, il est plus simple de placer le fichier dockerfile dans le répertoire de base. autrement dit, le même répertoire que le fichier `.sln`.</span><span class="sxs-lookup"><span data-stu-id="a6656-165">For a solution with a single application, and thus a single Dockerfile, it is simplest to put the Dockerfile in the base directory; that is, the same directory as the `.sln` file.</span></span> <span data-ttu-id="a6656-166">Dans ce cas, pour générer l’image, utilisez la commande `docker build` suivante à partir du répertoire contenant le fichier dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a6656-166">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="a6656-167">L’indicateur `--tag` portant un nom confus (qui peut être abrégé en `-t`) spécifie le nom complet de l’image, *y compris* la balise réelle si elle est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a6656-167">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, *including* the actual tag if specified.</span></span> <span data-ttu-id="a6656-168">Le `.` à la fin spécifie le *contexte* dans lequel la build sera exécutée ; Répertoire de travail actuel pour les commandes `COPY` dans fichier dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a6656-168">The `.` at the end specifies the *context* in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="a6656-169">Si vous avez plusieurs applications au sein d’une même solution, vous pouvez conserver le fichier dockerfile pour chaque application dans son propre dossier, en regard du fichier `.csproj`, mais vous devez toujours exécuter la commande `docker build` à partir du répertoire de base pour vous assurer que la solution et tous les les projets sont copiés dans l’image.</span><span class="sxs-lookup"><span data-stu-id="a6656-169">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file, but you should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="a6656-170">Vous pouvez spécifier un fichier dockerfile sous le répertoire actif à l’aide de l’indicateur `--file` (ou `-f`).</span><span class="sxs-lookup"><span data-stu-id="a6656-170">You can specify a Dockerfile below the current directory using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="a6656-171">Exécuter l’image dans un conteneur sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="a6656-171">Run the image in a container on your machine</span></span>

<span data-ttu-id="a6656-172">Pour exécuter l’image dans votre instance de l’arrimeur local, utilisez la commande `docker run`.</span><span class="sxs-lookup"><span data-stu-id="a6656-172">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="a6656-173">L’indicateur `-ti` connecte votre terminal actuel au terminal du conteneur et s’exécute en mode interactif.</span><span class="sxs-lookup"><span data-stu-id="a6656-173">The `-ti` flag connects your current terminal to the container's terminal and runs in interactive mode.</span></span> <span data-ttu-id="a6656-174">Le `-p 5000:80` publie (links) le port 80 sur le conteneur vers le port 80 sur l’interface réseau localhost.</span><span class="sxs-lookup"><span data-stu-id="a6656-174">The `-p 5000:80` publishes (links) port 80 on the container to port 80 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="a6656-175">Envoyer l’image vers un registre</span><span class="sxs-lookup"><span data-stu-id="a6656-175">Push the image to a registry</span></span>

<span data-ttu-id="a6656-176">Une fois que vous avez vérifié que l’image fonctionne, vous devez la transmettre à un registre de l’arrimeur pour la rendre disponible sur d’autres systèmes.</span><span class="sxs-lookup"><span data-stu-id="a6656-176">Once you've verified that the image works, you need to push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="a6656-177">Les réseaux internes devront approvisionner un registre Dockr.</span><span class="sxs-lookup"><span data-stu-id="a6656-177">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="a6656-178">Cela peut être aussi simple que l’exécution [de l’image `registry` de l’arrimeur](https://docs.docker.com/registry/deploying/) (ce qui est correct, le registre de l’arrimeur s’exécute dans un conteneur d’ancrage), mais il existe plusieurs solutions plus complètes disponibles.</span><span class="sxs-lookup"><span data-stu-id="a6656-178">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (that's right, the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="a6656-179">Pour le partage externe et l’utilisation du Cloud, plusieurs registres gérés sont disponibles, tels que [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) ou le [hub d’ancrage](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="a6656-179">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="a6656-180">Pour effectuer une transmission de type push vers le Hub Dockr, préfixez le nom de l’image avec votre nom d’utilisateur ou d’organisation.</span><span class="sxs-lookup"><span data-stu-id="a6656-180">To push to the Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="a6656-181">Pour effectuer une transmission de type push vers un registre privé, préfixez le nom de l’image avec le nom d’hôte du Registre et le nom de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="a6656-181">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="a6656-182">Une fois que l’image se trouve dans un registre, vous pouvez la déployer sur des hôtes de l’arrimeur ou sur un moteur d’orchestration de conteneur comme Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a6656-182">Once the image is in a registry, you can deploy it to individual Docker hosts or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a6656-183">[Précédent](self-hosted.md)
>[Suivant](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="a6656-183">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
