---
title: Docker - gRPC pour WCF Developers
description: Création d’images Docker pour ASP.NET applications Core gRPC
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148112"
---
# <a name="create-docker-images"></a><span data-ttu-id="5ce59-103">Créez des images Docker</span><span class="sxs-lookup"><span data-stu-id="5ce59-103">Create Docker images</span></span>

<span data-ttu-id="5ce59-104">Cette section couvre la création d’images Docker pour ASP.NET applications Core gRPC, prêtes à fonctionner dans des environnements Docker, Kubernetes ou autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="5ce59-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="5ce59-105">L’application d’échantillon utilisée, avec une application Web ASP.NET Core MVC et un service gRPC, est disponible sur le référentiel [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="5ce59-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="5ce59-106">Images de base Microsoft pour les applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5ce59-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="5ce59-107">Microsoft fournit une gamme d’images de base pour la construction et l’exécution d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ce59-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="5ce59-108">Pour créer une image ASP.NET Core 3.0, vous utilisez deux images de base :</span><span class="sxs-lookup"><span data-stu-id="5ce59-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="5ce59-109">Une image SDK pour construire et publier l’application.</span><span class="sxs-lookup"><span data-stu-id="5ce59-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="5ce59-110">Une image de temps d’exécution pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="5ce59-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="5ce59-111">Image</span><span class="sxs-lookup"><span data-stu-id="5ce59-111">Image</span></span> | <span data-ttu-id="5ce59-112">Description</span><span class="sxs-lookup"><span data-stu-id="5ce59-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="5ce59-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="5ce59-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="5ce59-114">Pour les `docker build`applications de construction avec .</span><span class="sxs-lookup"><span data-stu-id="5ce59-114">For building applications with `docker build`.</span></span> <span data-ttu-id="5ce59-115">Ne pas être utilisé en production.</span><span class="sxs-lookup"><span data-stu-id="5ce59-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="5ce59-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="5ce59-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="5ce59-117">Contient l’heure d’exécution et ASP.NET dépendances de base.</span><span class="sxs-lookup"><span data-stu-id="5ce59-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="5ce59-118">Pour la production.</span><span class="sxs-lookup"><span data-stu-id="5ce59-118">For production.</span></span> |

<span data-ttu-id="5ce59-119">Pour chaque image, il existe quatre variantes basées sur différentes distributions Linux, distinguées par des balises.</span><span class="sxs-lookup"><span data-stu-id="5ce59-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="5ce59-120">Étiquette d’image(s)</span><span class="sxs-lookup"><span data-stu-id="5ce59-120">Image tag(s)</span></span> | <span data-ttu-id="5ce59-121">Linux</span><span class="sxs-lookup"><span data-stu-id="5ce59-121">Linux</span></span> | <span data-ttu-id="5ce59-122">Notes</span><span class="sxs-lookup"><span data-stu-id="5ce59-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="5ce59-123">3.0-buster, 3.0</span><span class="sxs-lookup"><span data-stu-id="5ce59-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="5ce59-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="5ce59-124">Debian 10</span></span> | <span data-ttu-id="5ce59-125">L’image par défaut si aucune variante OS n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5ce59-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="5ce59-126">3.0-alpine</span><span class="sxs-lookup"><span data-stu-id="5ce59-126">3.0-alpine</span></span> | <span data-ttu-id="5ce59-127">Alpine 3.9</span><span class="sxs-lookup"><span data-stu-id="5ce59-127">Alpine 3.9</span></span> | <span data-ttu-id="5ce59-128">Les images de base alpines sont beaucoup plus petites que les images de base de Debian ou d’Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5ce59-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="5ce59-129">3.0-disco</span><span class="sxs-lookup"><span data-stu-id="5ce59-129">3.0-disco</span></span> | <span data-ttu-id="5ce59-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="5ce59-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="5ce59-131">3.0-bionique</span><span class="sxs-lookup"><span data-stu-id="5ce59-131">3.0-bionic</span></span> | <span data-ttu-id="5ce59-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5ce59-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="5ce59-133">L’image de base alpine est d’environ 100 Mo, contre 200 Mo pour les images Debian et Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5ce59-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="5ce59-134">Certains progiciels ou bibliothèques peuvent ne pas être disponibles dans la gestion des paquets d’Alpine.</span><span class="sxs-lookup"><span data-stu-id="5ce59-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="5ce59-135">Si vous ne savez pas quelle image utiliser, vous devez probablement choisir le Debian par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ce59-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ce59-136">Assurez-vous d’utiliser la même variante de Linux pour la construction et le temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5ce59-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="5ce59-137">Les applications construites et publiées sur une variante peuvent ne pas fonctionner sur une autre.</span><span class="sxs-lookup"><span data-stu-id="5ce59-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="5ce59-138">Créer une image Docker</span><span class="sxs-lookup"><span data-stu-id="5ce59-138">Create a Docker image</span></span>

<span data-ttu-id="5ce59-139">Une image Docker est définie par un *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="5ce59-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="5ce59-140">Il s’agit d’un fichier texte qui contient toutes les commandes nécessaires pour construire l’application et installer toutes les dépendances qui sont nécessaires pour la construction ou l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="5ce59-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="5ce59-141">L’exemple suivant montre le Dockerfile le plus simple pour une application ASP.NET Core 3.0 :</span><span class="sxs-lookup"><span data-stu-id="5ce59-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="5ce59-142">Le Dockerfile comporte deux parties `sdk` : la première utilise l’image de base pour construire et publier l’application ; la seconde crée une image `aspnet` de temps d’exécution à partir de la base.</span><span class="sxs-lookup"><span data-stu-id="5ce59-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="5ce59-143">C’est `sdk` parce que l’image est d’environ 900 Mo, par rapport à environ 200 Mo pour l’image de temps d’exécution, et la plupart de son contenu sont inutiles au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5ce59-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="5ce59-144">Les étapes de construction</span><span class="sxs-lookup"><span data-stu-id="5ce59-144">The build steps</span></span>

| <span data-ttu-id="5ce59-145">Étape</span><span class="sxs-lookup"><span data-stu-id="5ce59-145">Step</span></span> | <span data-ttu-id="5ce59-146">Description</span><span class="sxs-lookup"><span data-stu-id="5ce59-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="5ce59-147">Déclare l’image de base `builder` et assigne l’alias.</span><span class="sxs-lookup"><span data-stu-id="5ce59-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="5ce59-148">Crée `/src` le répertoire et le définit comme le répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="5ce59-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="5ce59-149">Copie tout en dessous de l’annuaire actuel sur l’hôte dans l’annuaire actuel sur l’image.</span><span class="sxs-lookup"><span data-stu-id="5ce59-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="5ce59-150">Restaure tous les paquets externes (ASP.NET cadre Core 3.0 est préinstallé avec le SDK).</span><span class="sxs-lookup"><span data-stu-id="5ce59-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="5ce59-151">Construit et publie une version release.</span><span class="sxs-lookup"><span data-stu-id="5ce59-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="5ce59-152">Notez `--runtime` que le drapeau n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5ce59-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="5ce59-153">Les étapes d’image de temps d’exécution</span><span class="sxs-lookup"><span data-stu-id="5ce59-153">The runtime image steps</span></span>

| <span data-ttu-id="5ce59-154">Étape</span><span class="sxs-lookup"><span data-stu-id="5ce59-154">Step</span></span> | <span data-ttu-id="5ce59-155">Description</span><span class="sxs-lookup"><span data-stu-id="5ce59-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="5ce59-156">Déclare une nouvelle image de base.</span><span class="sxs-lookup"><span data-stu-id="5ce59-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="5ce59-157">Crée `/app` le répertoire et le définit comme le répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="5ce59-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="5ce59-158">Copie de l’application publiée de `builder` l’image `FROM` précédente, en utilisant le pseudonyme de la première ligne.</span><span class="sxs-lookup"><span data-stu-id="5ce59-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="5ce59-159">Définit la commande pour fonctionner lorsque le conteneur démarre.</span><span class="sxs-lookup"><span data-stu-id="5ce59-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="5ce59-160">La `dotnet` commande dans l’image de temps d’exécution ne peut exécuter que des fichiers DLL.</span><span class="sxs-lookup"><span data-stu-id="5ce59-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="5ce59-161">HTTPS à Docker</span><span class="sxs-lookup"><span data-stu-id="5ce59-161">HTTPS in Docker</span></span>

<span data-ttu-id="5ce59-162">Les images de base `ASPNETCORE_URLS` de `http://+:80`Microsoft pour Docker définissent la variable d’environnement à , ce qui signifie que Kestrel fonctionne sans HTTPS sur ce port.</span><span class="sxs-lookup"><span data-stu-id="5ce59-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="5ce59-163">Si vous utilisez HTTPS avec un certificat personnalisé (tel que décrit dans [les applications IPM),](self-hosted.md)vous devez passer outre à ce sujet.</span><span class="sxs-lookup"><span data-stu-id="5ce59-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="5ce59-164">Définissez la variable d’environnement dans la partie de création d’images en temps d’exécution de votre Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="5ce59-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="5ce59-165">Le fichier .dockerignore</span><span class="sxs-lookup"><span data-stu-id="5ce59-165">The .dockerignore file</span></span>

<span data-ttu-id="5ce59-166">Tout `.gitignore` comme les fichiers qui excluent certains `.dockerignore` fichiers et répertoires du contrôle source, le fichier peut être utilisé pour exclure les fichiers et les répertoires d’être copiés à l’image pendant la construction.</span><span class="sxs-lookup"><span data-stu-id="5ce59-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="5ce59-167">Cela permet non seulement d’économiser la copie de temps, mais peut également éviter certaines erreurs qui découlent d’avoir le `obj` répertoire de votre PC copié dans l’image.</span><span class="sxs-lookup"><span data-stu-id="5ce59-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="5ce59-168">Au minimum, vous devez `bin` ajouter `obj` des `.dockerignore` entrées pour et à votre fichier.</span><span class="sxs-lookup"><span data-stu-id="5ce59-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="5ce59-169">Créer l’image</span><span class="sxs-lookup"><span data-stu-id="5ce59-169">Build the image</span></span>

<span data-ttu-id="5ce59-170">Pour une solution avec une seule application, et donc un seul Dockerfile, il est plus simple de mettre le Dockerfile dans le répertoire de base.</span><span class="sxs-lookup"><span data-stu-id="5ce59-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="5ce59-171">En d’autres termes, mettez-le `.sln` dans le même répertoire que le fichier.</span><span class="sxs-lookup"><span data-stu-id="5ce59-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="5ce59-172">Dans ce cas, pour construire l’image, utilisez la commande suivante `docker build` de l’annuaire contenant le Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="5ce59-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="5ce59-173">Le drapeau `--tag` de façon confuse (qui `-t`peut être raccourci à ) spécifie le nom entier de l’image, y compris l’étiquette réelle si spécifié.</span><span class="sxs-lookup"><span data-stu-id="5ce59-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="5ce59-174">La `.` fin précise le contexte dans lequel la construction sera exécutée; l’annuaire de travail `COPY` actuel pour les commandes dans le Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="5ce59-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="5ce59-175">Si vous avez plusieurs applications dans une seule solution, vous pouvez conserver le Dockerfile pour chaque application dans son propre dossier, à côté du `.csproj` fichier.</span><span class="sxs-lookup"><span data-stu-id="5ce59-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="5ce59-176">Vous devez toujours `docker build` exécuter la commande à partir du répertoire de base pour vous assurer que la solution et tous les projets sont copiés dans l’image.</span><span class="sxs-lookup"><span data-stu-id="5ce59-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="5ce59-177">Vous pouvez spécifier un Dockerfile `--file` en `-f`dessous de l’annuaire actuel en utilisant le (ou) drapeau.</span><span class="sxs-lookup"><span data-stu-id="5ce59-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="5ce59-178">Exécutez l’image dans un conteneur sur votre machine</span><span class="sxs-lookup"><span data-stu-id="5ce59-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="5ce59-179">Pour exécuter l’image dans votre `docker run` instance Docker locale, utilisez la commande.</span><span class="sxs-lookup"><span data-stu-id="5ce59-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="5ce59-180">Le `-ti` drapeau relie votre terminal actuel au terminal du conteneur et fonctionne en mode interactif.</span><span class="sxs-lookup"><span data-stu-id="5ce59-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="5ce59-181">Le `-p 5000:80` port 80 publie (liens) sur le conteneur jusqu’au port 5000 sur l’interface réseau localhost.</span><span class="sxs-lookup"><span data-stu-id="5ce59-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="5ce59-182">Envoyer l’image dans un registre</span><span class="sxs-lookup"><span data-stu-id="5ce59-182">Push the image to a registry</span></span>

<span data-ttu-id="5ce59-183">Une fois que vous avez vérifié que l’image fonctionne, poussez-la à un registre Docker pour la rendre disponible sur d’autres systèmes.</span><span class="sxs-lookup"><span data-stu-id="5ce59-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="5ce59-184">Les réseaux internes devront fournir un registre Docker.</span><span class="sxs-lookup"><span data-stu-id="5ce59-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="5ce59-185">Cela peut être aussi simple que [l’exécution `registry` de l’image de Docker](https://docs.docker.com/registry/deploying/) (le registre Docker fonctionne dans un conteneur Docker), mais il existe diverses solutions plus complètes disponibles.</span><span class="sxs-lookup"><span data-stu-id="5ce59-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="5ce59-186">Pour le partage externe et l’utilisation du cloud, il existe différents registres gérés disponibles, tels que [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) ou [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="5ce59-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="5ce59-187">Pour vous en rendre à Docker Hub, préfixez le nom de l’image avec votre nom d’utilisateur ou d’organisation.</span><span class="sxs-lookup"><span data-stu-id="5ce59-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="5ce59-188">Pour passer à un registre privé, préfixer le nom de l’image avec le nom de l’hôte du registre et le nom de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="5ce59-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="5ce59-189">Une fois que l’image est dans un registre, vous pouvez la déployer à des hôtes Docker individuels, ou à un moteur d’orchestration de conteneurs comme Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="5ce59-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5ce59-190">[Suivant précédent](self-hosted.md)
>[Next](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="5ce59-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
