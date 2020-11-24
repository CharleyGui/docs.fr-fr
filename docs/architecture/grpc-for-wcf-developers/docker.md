---
title: Docker-gRPC pour les développeurs WCF
description: Création d’images d’ancrage pour les applications ASP.NET Core gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 0a680d0918868829042e521506fa8c1a1628bf5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688443"
---
# <a name="create-docker-images"></a><span data-ttu-id="5fb81-103">Créer des images d’ancrage</span><span class="sxs-lookup"><span data-stu-id="5fb81-103">Create Docker images</span></span>

<span data-ttu-id="5fb81-104">Cette section traite de la création d’images de l’arrimeur pour les applications ASP.NET Core gRPC, prêtes à être exécutées dans les environnements d’ancrage, Kubernetes ou d’autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="5fb81-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="5fb81-105">L’exemple d’application utilisé, avec une application Web ASP.NET Core MVC et un service gRPC, est disponible sur le référentiel [dotnet-architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="5fb81-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="5fb81-106">Images de base Microsoft pour les applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5fb81-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="5fb81-107">Microsoft fournit une gamme d’images de base pour la création et l’exécution d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5fb81-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="5fb81-108">Pour créer une image ASP.NET Core 3,0, vous utilisez deux images de base :</span><span class="sxs-lookup"><span data-stu-id="5fb81-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="5fb81-109">Image du kit de développement logiciel (SDK) pour générer et publier l’application.</span><span class="sxs-lookup"><span data-stu-id="5fb81-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="5fb81-110">Image d’exécution pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="5fb81-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="5fb81-111">Image</span><span class="sxs-lookup"><span data-stu-id="5fb81-111">Image</span></span> | <span data-ttu-id="5fb81-112">Description</span><span class="sxs-lookup"><span data-stu-id="5fb81-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="5fb81-113">mcr.microsoft.com/dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="5fb81-113">mcr.microsoft.com/dotnet/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-sdk/) | <span data-ttu-id="5fb81-114">Pour créer des applications avec `docker build` .</span><span class="sxs-lookup"><span data-stu-id="5fb81-114">For building applications with `docker build`.</span></span> <span data-ttu-id="5fb81-115">À ne pas utiliser en production.</span><span class="sxs-lookup"><span data-stu-id="5fb81-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="5fb81-116">mcr.microsoft.com/dotnet/aspnet</span><span class="sxs-lookup"><span data-stu-id="5fb81-116">mcr.microsoft.com/dotnet/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | <span data-ttu-id="5fb81-117">Contient le runtime et les dépendances de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5fb81-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="5fb81-118">Pour la production.</span><span class="sxs-lookup"><span data-stu-id="5fb81-118">For production.</span></span> |

<span data-ttu-id="5fb81-119">Pour chaque image, il existe quatre variantes basées sur différentes distributions Linux, distinguées par des balises.</span><span class="sxs-lookup"><span data-stu-id="5fb81-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="5fb81-120">Balise (s) d’image</span><span class="sxs-lookup"><span data-stu-id="5fb81-120">Image tag(s)</span></span> | <span data-ttu-id="5fb81-121">Linux</span><span class="sxs-lookup"><span data-stu-id="5fb81-121">Linux</span></span> | <span data-ttu-id="5fb81-122">Notes</span><span class="sxs-lookup"><span data-stu-id="5fb81-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="5fb81-123">3,0-Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="5fb81-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="5fb81-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="5fb81-124">Debian 10</span></span> | <span data-ttu-id="5fb81-125">Image par défaut si aucun variant de système d’exploitation n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="5fb81-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="5fb81-126">3,0-Alpine</span><span class="sxs-lookup"><span data-stu-id="5fb81-126">3.0-alpine</span></span> | <span data-ttu-id="5fb81-127">Alpine 3,9</span><span class="sxs-lookup"><span data-stu-id="5fb81-127">Alpine 3.9</span></span> | <span data-ttu-id="5fb81-128">Les images de base Alpine sont plus petites que les images Debian ou Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5fb81-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="5fb81-129">3,0-Disco</span><span class="sxs-lookup"><span data-stu-id="5fb81-129">3.0-disco</span></span> | <span data-ttu-id="5fb81-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="5fb81-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="5fb81-131">3,0-Bionic</span><span class="sxs-lookup"><span data-stu-id="5fb81-131">3.0-bionic</span></span> | <span data-ttu-id="5fb81-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5fb81-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="5fb81-133">L’image de base alpine est d’environ 100 Mo, par rapport à 200 Mo pour les images Debian et Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5fb81-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="5fb81-134">Certains packages ou bibliothèques de logiciels peuvent ne pas être disponibles dans la gestion des packages de Alpine.</span><span class="sxs-lookup"><span data-stu-id="5fb81-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="5fb81-135">Si vous ne savez pas quelle image utiliser, vous devez probablement choisir le Debian par défaut.</span><span class="sxs-lookup"><span data-stu-id="5fb81-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fb81-136">Veillez à utiliser la même variante de Linux pour la build et le Runtime.</span><span class="sxs-lookup"><span data-stu-id="5fb81-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="5fb81-137">Les applications générées et publiées sur une seule variante peuvent ne pas fonctionner sur une autre.</span><span class="sxs-lookup"><span data-stu-id="5fb81-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="5fb81-138">Créer une image Docker</span><span class="sxs-lookup"><span data-stu-id="5fb81-138">Create a Docker image</span></span>

<span data-ttu-id="5fb81-139">Une image de l’ancrage est définie par un *fichier dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="5fb81-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="5fb81-140">Il s’agit d’un fichier texte qui contient toutes les commandes nécessaires à la génération de l’application et à l’installation des dépendances requises pour la génération ou l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="5fb81-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="5fb81-141">L’exemple suivant illustre la fichier dockerfile la plus simple pour une application ASP.NET Core 3,0 :</span><span class="sxs-lookup"><span data-stu-id="5fb81-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="5fb81-142">Le fichier dockerfile comporte deux parties : la première utilise l' `sdk` image de base pour générer et publier l’application ; la deuxième crée une image d’exécution à partir de la `aspnet` base.</span><span class="sxs-lookup"><span data-stu-id="5fb81-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="5fb81-143">Cela est dû au fait que l' `sdk` image est d’environ 900 Mo, par rapport à environ 200 Mo pour l’image d’exécution, et que la majeure partie de son contenu n’est pas nécessaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5fb81-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="5fb81-144">Étapes de génération</span><span class="sxs-lookup"><span data-stu-id="5fb81-144">The build steps</span></span>

| <span data-ttu-id="5fb81-145">Étape</span><span class="sxs-lookup"><span data-stu-id="5fb81-145">Step</span></span> | <span data-ttu-id="5fb81-146">Description</span><span class="sxs-lookup"><span data-stu-id="5fb81-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="5fb81-147">Déclare l’image de base et assigne l' `builder` alias.</span><span class="sxs-lookup"><span data-stu-id="5fb81-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="5fb81-148">Crée le `/src` répertoire et le définit comme répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="5fb81-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="5fb81-149">Copie tout ce qui se trouve sous le répertoire actif sur l’hôte dans le répertoire actif de l’image.</span><span class="sxs-lookup"><span data-stu-id="5fb81-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="5fb81-150">Restaure tous les packages externes (ASP.NET Core 3,0 Framework est préinstallé avec le kit de développement logiciel (SDK)).</span><span class="sxs-lookup"><span data-stu-id="5fb81-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="5fb81-151">Génère et publie une version Release.</span><span class="sxs-lookup"><span data-stu-id="5fb81-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="5fb81-152">Notez que l' `--runtime` indicateur n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5fb81-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="5fb81-153">Étapes de l’image d’exécution</span><span class="sxs-lookup"><span data-stu-id="5fb81-153">The runtime image steps</span></span>

| <span data-ttu-id="5fb81-154">Étape</span><span class="sxs-lookup"><span data-stu-id="5fb81-154">Step</span></span> | <span data-ttu-id="5fb81-155">Description</span><span class="sxs-lookup"><span data-stu-id="5fb81-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="5fb81-156">Déclare une nouvelle image de base.</span><span class="sxs-lookup"><span data-stu-id="5fb81-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="5fb81-157">Crée le `/app` répertoire et le définit comme répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="5fb81-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="5fb81-158">Copie l’application publiée à partir de l’image précédente, à l’aide `builder` de l’alias de la première `FROM` ligne.</span><span class="sxs-lookup"><span data-stu-id="5fb81-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="5fb81-159">Définit la commande à exécuter lorsque le conteneur démarre.</span><span class="sxs-lookup"><span data-stu-id="5fb81-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="5fb81-160">La `dotnet` commande dans l’image d’exécution peut uniquement exécuter des fichiers dll.</span><span class="sxs-lookup"><span data-stu-id="5fb81-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="5fb81-161">HTTPs dans l’ancrage</span><span class="sxs-lookup"><span data-stu-id="5fb81-161">HTTPS in Docker</span></span>

<span data-ttu-id="5fb81-162">Les images de base Microsoft pour l’arrimeur définissent la `ASPNETCORE_URLS` variable d’environnement sur `http://+:80` , ce qui signifie que Kestrel s’exécute sans https sur ce port.</span><span class="sxs-lookup"><span data-stu-id="5fb81-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="5fb81-163">Si vous utilisez le protocole HTTPs avec un certificat personnalisé (comme décrit dans [applications GRPC auto-hébergées](self-hosted.md)), vous devez remplacer ceci.</span><span class="sxs-lookup"><span data-stu-id="5fb81-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="5fb81-164">Définissez la variable d’environnement dans la partie création de l’image du runtime de votre fichier dockerfile.</span><span class="sxs-lookup"><span data-stu-id="5fb81-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="5fb81-165">Fichier. dockerignore</span><span class="sxs-lookup"><span data-stu-id="5fb81-165">The .dockerignore file</span></span>

<span data-ttu-id="5fb81-166">À l’instar `.gitignore` des fichiers qui excluent certains fichiers et répertoires du contrôle de code source, le `.dockerignore` fichier peut être utilisé pour exclure des fichiers et des répertoires d’être copiés dans l’image pendant la génération.</span><span class="sxs-lookup"><span data-stu-id="5fb81-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="5fb81-167">Cela permet non seulement de gagner du temps, mais également d’éviter certaines erreurs qui se produisent lors de la `obj` copie du répertoire de votre ordinateur dans l’image.</span><span class="sxs-lookup"><span data-stu-id="5fb81-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="5fb81-168">Au minimum, vous devez ajouter des entrées pour `bin` et `obj` à votre `.dockerignore` fichier.</span><span class="sxs-lookup"><span data-stu-id="5fb81-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="5fb81-169">Créer l’image</span><span class="sxs-lookup"><span data-stu-id="5fb81-169">Build the image</span></span>

<span data-ttu-id="5fb81-170">Pour une solution avec une seule application, et donc un fichier dockerfile unique, il est plus simple de placer le fichier dockerfile dans le répertoire de base.</span><span class="sxs-lookup"><span data-stu-id="5fb81-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="5fb81-171">En d’autres termes, placez-le dans le même répertoire que le `.sln` fichier.</span><span class="sxs-lookup"><span data-stu-id="5fb81-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="5fb81-172">Dans ce cas, pour générer l’image, utilisez la `docker build` commande suivante à partir du répertoire contenant fichier dockerfile.</span><span class="sxs-lookup"><span data-stu-id="5fb81-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="5fb81-173">L' `--tag` indicateur de nom confus (qui peut être raccourci `-t` ) spécifie le nom complet de l’image, y compris la balise réelle si elle est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5fb81-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="5fb81-174">Le `.` à la fin spécifie le contexte dans lequel la build sera exécutée ; le répertoire de travail actuel pour les `COPY` commandes dans fichier dockerfile.</span><span class="sxs-lookup"><span data-stu-id="5fb81-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="5fb81-175">Si vous avez plusieurs applications au sein d’une même solution, vous pouvez conserver les fichier dockerfile pour chaque application dans son propre dossier, en regard du `.csproj` fichier.</span><span class="sxs-lookup"><span data-stu-id="5fb81-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="5fb81-176">Vous devez toujours exécuter la `docker build` commande à partir du répertoire de base pour vous assurer que la solution et tous les projets sont copiés dans l’image.</span><span class="sxs-lookup"><span data-stu-id="5fb81-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="5fb81-177">Vous pouvez spécifier un fichier dockerfile sous le répertoire actif à l’aide de l' `--file` indicateur (ou `-f` ).</span><span class="sxs-lookup"><span data-stu-id="5fb81-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="5fb81-178">Exécuter l’image dans un conteneur sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="5fb81-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="5fb81-179">Pour exécuter l’image dans votre instance de l’arrimeur local, utilisez la `docker run` commande.</span><span class="sxs-lookup"><span data-stu-id="5fb81-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="5fb81-180">L' `-ti` indicateur connecte votre terminal actuel au terminal du conteneur et s’exécute en mode interactif.</span><span class="sxs-lookup"><span data-stu-id="5fb81-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="5fb81-181">Le `-p 5000:80` publie (links) le port 80 sur le conteneur vers le port 5000 sur l’interface réseau localhost.</span><span class="sxs-lookup"><span data-stu-id="5fb81-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="5fb81-182">Envoyer l’image dans un registre</span><span class="sxs-lookup"><span data-stu-id="5fb81-182">Push the image to a registry</span></span>

<span data-ttu-id="5fb81-183">Une fois que vous avez vérifié que l’image fonctionne, transmettez-la à un registre de l’arrimeur pour la rendre disponible sur d’autres systèmes.</span><span class="sxs-lookup"><span data-stu-id="5fb81-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="5fb81-184">Les réseaux internes devront approvisionner un registre Dockr.</span><span class="sxs-lookup"><span data-stu-id="5fb81-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="5fb81-185">Cela peut être aussi simple que l’exécution [de l' `registry` image de l’arrimeur](https://docs.docker.com/registry/deploying/) (le registre de l’arrimeur s’exécute dans un conteneur d’ancrage), mais il existe plusieurs solutions plus complètes disponibles.</span><span class="sxs-lookup"><span data-stu-id="5fb81-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="5fb81-186">Pour le partage externe et l’utilisation du Cloud, plusieurs registres gérés sont disponibles, tels que [Azure Container Registry](/azure/container-registry/) ou le [hub d’ancrage](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="5fb81-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="5fb81-187">Pour effectuer une transmission de type push vers le hub d’ancrage, préfixez le nom de l’image avec votre nom d’utilisateur ou d’organisation.</span><span class="sxs-lookup"><span data-stu-id="5fb81-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="5fb81-188">Pour effectuer une transmission de type push vers un registre privé, préfixez le nom de l’image avec le nom d’hôte du Registre et le nom de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="5fb81-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="5fb81-189">Une fois que l’image se trouve dans un registre, vous pouvez la déployer sur des hôtes de l’arrimeur individuel ou sur un moteur d’orchestration de conteneur comme Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="5fb81-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5fb81-190">[Précédent](self-hosted.md) 
> [Suivant](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="5fb81-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
