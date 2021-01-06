---
title: Docker-gRPC pour les développeurs WCF
description: Création d’images d’ancrage pour les applications ASP.NET Core gRPC
ms.date: 12/15/2020
ms.openlocfilehash: f662dbd67f00b828f3e1dfa47359a450dd1c5900
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938414"
---
# <a name="create-docker-images"></a><span data-ttu-id="e6e76-103">Créer des images d’ancrage</span><span class="sxs-lookup"><span data-stu-id="e6e76-103">Create Docker images</span></span>

<span data-ttu-id="e6e76-104">Cette section traite de la création d’images de l’arrimeur pour les applications ASP.NET Core gRPC, prêtes à être exécutées dans les environnements d’ancrage, Kubernetes ou d’autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="e6e76-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="e6e76-105">L’exemple d’application utilisé, avec une application Web ASP.NET Core MVC et un service gRPC, est disponible sur le référentiel [dotnet-architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="e6e76-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="e6e76-106">Images de base Microsoft pour les applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e6e76-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="e6e76-107">Microsoft fournit une gamme d’images de base pour la création et l’exécution d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e6e76-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="e6e76-108">Pour créer une image ASP.NET Core 3,0, vous utilisez deux images de base :</span><span class="sxs-lookup"><span data-stu-id="e6e76-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="e6e76-109">Image du kit de développement logiciel (SDK) pour générer et publier l’application.</span><span class="sxs-lookup"><span data-stu-id="e6e76-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="e6e76-110">Image d’exécution pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="e6e76-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="e6e76-111">Image</span><span class="sxs-lookup"><span data-stu-id="e6e76-111">Image</span></span> | <span data-ttu-id="e6e76-112">Description</span><span class="sxs-lookup"><span data-stu-id="e6e76-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="e6e76-113">mcr.microsoft.com/dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="e6e76-113">mcr.microsoft.com/dotnet/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-sdk/) | <span data-ttu-id="e6e76-114">Pour créer des applications avec `docker build` .</span><span class="sxs-lookup"><span data-stu-id="e6e76-114">For building applications with `docker build`.</span></span> <span data-ttu-id="e6e76-115">À ne pas utiliser en production.</span><span class="sxs-lookup"><span data-stu-id="e6e76-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="e6e76-116">mcr.microsoft.com/dotnet/aspnet</span><span class="sxs-lookup"><span data-stu-id="e6e76-116">mcr.microsoft.com/dotnet/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | <span data-ttu-id="e6e76-117">Contient le runtime et les dépendances de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e6e76-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="e6e76-118">Pour la production.</span><span class="sxs-lookup"><span data-stu-id="e6e76-118">For production.</span></span> |

<span data-ttu-id="e6e76-119">Pour chaque image, il existe quatre variantes basées sur différentes distributions Linux, distinguées par des balises.</span><span class="sxs-lookup"><span data-stu-id="e6e76-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="e6e76-120">Balise (s) d’image</span><span class="sxs-lookup"><span data-stu-id="e6e76-120">Image tag(s)</span></span> | <span data-ttu-id="e6e76-121">Linux</span><span class="sxs-lookup"><span data-stu-id="e6e76-121">Linux</span></span> | <span data-ttu-id="e6e76-122">Notes</span><span class="sxs-lookup"><span data-stu-id="e6e76-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="e6e76-123">5,0-Buster, 5,0</span><span class="sxs-lookup"><span data-stu-id="e6e76-123">5.0-buster, 5.0</span></span> | <span data-ttu-id="e6e76-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="e6e76-124">Debian 10</span></span> | <span data-ttu-id="e6e76-125">Image par défaut si aucun variant de système d’exploitation n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="e6e76-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="e6e76-126">5,0-Alpine</span><span class="sxs-lookup"><span data-stu-id="e6e76-126">5.0-alpine</span></span> | <span data-ttu-id="e6e76-127">Alpine 3,9</span><span class="sxs-lookup"><span data-stu-id="e6e76-127">Alpine 3.9</span></span> | <span data-ttu-id="e6e76-128">Les images de base Alpine sont plus petites que les images Debian ou Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e6e76-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="e6e76-129">5,0-Disco</span><span class="sxs-lookup"><span data-stu-id="e6e76-129">5.0-disco</span></span> | <span data-ttu-id="e6e76-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="e6e76-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="e6e76-131">5,0-Bionic</span><span class="sxs-lookup"><span data-stu-id="e6e76-131">5.0-bionic</span></span> | <span data-ttu-id="e6e76-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e6e76-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="e6e76-133">L’image de base alpine est d’environ 100 Mo, par rapport à 200 Mo pour les images Debian et Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e6e76-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="e6e76-134">Certains packages ou bibliothèques de logiciels peuvent ne pas être disponibles dans la gestion des packages de Alpine.</span><span class="sxs-lookup"><span data-stu-id="e6e76-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="e6e76-135">Si vous ne savez pas quelle image utiliser, vous devez probablement choisir le Debian par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6e76-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6e76-136">Veillez à utiliser la même variante de Linux pour la build et le Runtime.</span><span class="sxs-lookup"><span data-stu-id="e6e76-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="e6e76-137">Les applications générées et publiées sur une seule variante peuvent ne pas fonctionner sur une autre.</span><span class="sxs-lookup"><span data-stu-id="e6e76-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="e6e76-138">Créer une image Docker</span><span class="sxs-lookup"><span data-stu-id="e6e76-138">Create a Docker image</span></span>

<span data-ttu-id="e6e76-139">Une image de l’ancrage est définie par un *fichier dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="e6e76-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="e6e76-140">Ce *fichier dockerfile* est un fichier texte qui contient toutes les commandes nécessaires à la génération de l’application et à l’installation des dépendances nécessaires à la création ou à l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="e6e76-140">This *Dockerfile* is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="e6e76-141">L’exemple suivant illustre la fichier dockerfile la plus simple pour une application ASP.NET Core 5,0 :</span><span class="sxs-lookup"><span data-stu-id="e6e76-141">The following example shows the simplest Dockerfile for an ASP.NET Core 5.0 application:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /src

COPY ./StockKube.sln .
COPY ./src/StockData/StockData.csproj ./src/StockData/
COPY ./src/StockWeb/StockWeb.csproj ./src/StockWeb/

RUN dotnet restore

COPY . .

RUN dotnet publish --no-restore -c Release -o /published src/StockData/StockData.csproj

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="e6e76-142">Le fichier dockerfile comporte deux parties : la première utilise l' `sdk` image de base pour générer et publier l’application ; la deuxième crée une image d’exécution à partir de la `aspnet` base.</span><span class="sxs-lookup"><span data-stu-id="e6e76-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="e6e76-143">Cela est dû au fait que l' `sdk` image est d’environ 900 Mo, par rapport à environ 200 Mo pour l’image d’exécution, et que la majeure partie de son contenu n’est pas nécessaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6e76-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="e6e76-144">Étapes de génération</span><span class="sxs-lookup"><span data-stu-id="e6e76-144">The build steps</span></span>

| <span data-ttu-id="e6e76-145">Étape</span><span class="sxs-lookup"><span data-stu-id="e6e76-145">Step</span></span> | <span data-ttu-id="e6e76-146">Description</span><span class="sxs-lookup"><span data-stu-id="e6e76-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="e6e76-147">Déclare l’image de base et assigne l' `builder` alias.</span><span class="sxs-lookup"><span data-stu-id="e6e76-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="e6e76-148">Crée le `/src` répertoire et le définit comme répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="e6e76-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="e6e76-149">Copie tout ce qui se trouve sous le répertoire actif sur l’hôte dans le répertoire actif de l’image.</span><span class="sxs-lookup"><span data-stu-id="e6e76-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="e6e76-150">Restaure tous les packages externes (ASP.NET Core 3,0 Framework est préinstallé avec le kit de développement logiciel (SDK)).</span><span class="sxs-lookup"><span data-stu-id="e6e76-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="e6e76-151">Génère et publie une version Release.</span><span class="sxs-lookup"><span data-stu-id="e6e76-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="e6e76-152">Notez que l' `--runtime` indicateur n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e6e76-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="e6e76-153">Étapes de l’image d’exécution</span><span class="sxs-lookup"><span data-stu-id="e6e76-153">The runtime image steps</span></span>

| <span data-ttu-id="e6e76-154">Étape</span><span class="sxs-lookup"><span data-stu-id="e6e76-154">Step</span></span> | <span data-ttu-id="e6e76-155">Description</span><span class="sxs-lookup"><span data-stu-id="e6e76-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="e6e76-156">Déclare une nouvelle image de base.</span><span class="sxs-lookup"><span data-stu-id="e6e76-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="e6e76-157">Crée le `/app` répertoire et le définit comme répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="e6e76-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="e6e76-158">Copie l’application publiée à partir de l’image précédente, à l’aide `builder` de l’alias de la première `FROM` ligne.</span><span class="sxs-lookup"><span data-stu-id="e6e76-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="e6e76-159">Définit la commande à exécuter lorsque le conteneur démarre.</span><span class="sxs-lookup"><span data-stu-id="e6e76-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="e6e76-160">La `dotnet` commande dans l’image d’exécution peut uniquement exécuter des fichiers dll.</span><span class="sxs-lookup"><span data-stu-id="e6e76-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="e6e76-161">HTTPs dans l’ancrage</span><span class="sxs-lookup"><span data-stu-id="e6e76-161">HTTPS in Docker</span></span>

<span data-ttu-id="e6e76-162">Les images de base Microsoft pour l’arrimeur définissent la `ASPNETCORE_URLS` variable d’environnement sur `http://+:80` , ce qui signifie que Kestrel s’exécute sans https sur ce port.</span><span class="sxs-lookup"><span data-stu-id="e6e76-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="e6e76-163">Si vous utilisez le protocole HTTPs avec un certificat personnalisé (comme décrit dans [applications GRPC auto-hébergées](self-hosted.md)), vous devez remplacer cette configuration.</span><span class="sxs-lookup"><span data-stu-id="e6e76-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this configuration.</span></span> <span data-ttu-id="e6e76-164">Définissez la variable d’environnement dans la partie création de l’image du runtime de votre fichier dockerfile.</span><span class="sxs-lookup"><span data-stu-id="e6e76-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:5.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="e6e76-165">Fichier. dockerignore</span><span class="sxs-lookup"><span data-stu-id="e6e76-165">The .dockerignore file</span></span>

<span data-ttu-id="e6e76-166">À l’instar `.gitignore` des fichiers qui excluent certains fichiers et répertoires du contrôle de code source, le `.dockerignore` fichier peut être utilisé pour exclure des fichiers et des répertoires d’être copiés dans l’image pendant la génération.</span><span class="sxs-lookup"><span data-stu-id="e6e76-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="e6e76-167">Ce fichier permet non seulement de gagner du temps, mais également d’éviter certaines erreurs qui se produisent lors de la `obj` copie du répertoire de votre ordinateur dans l’image.</span><span class="sxs-lookup"><span data-stu-id="e6e76-167">This file not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="e6e76-168">Au minimum, vous devez ajouter des entrées pour `bin` et `obj` à votre `.dockerignore` fichier.</span><span class="sxs-lookup"><span data-stu-id="e6e76-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="e6e76-169">Créer l’image</span><span class="sxs-lookup"><span data-stu-id="e6e76-169">Build the image</span></span>

<span data-ttu-id="e6e76-170">Pour une `StockKube.sln` solution contenant deux applications différentes `StockData` et `StockWeb` , il est plus simple de placer les fichier dockerfile pour chacune d’elles dans le répertoire de base.</span><span class="sxs-lookup"><span data-stu-id="e6e76-170">For a `StockKube.sln` solution containing two different applications `StockData` and `StockWeb`, it's simplest to put the Dockerfile for each one of them in the base directory.</span></span> <span data-ttu-id="e6e76-171">Dans ce cas, pour générer l’image, utilisez la `docker build` commande suivante à partir du répertoire où `.sln` se trouve le fichier.</span><span class="sxs-lookup"><span data-stu-id="e6e76-171">In that case, to build the image, use the following `docker build` command from the same directory where `.sln` file resides.</span></span>

```console
docker build -t stockdata:1.0.0 -f .\src\StockData\Dockerfile .
```

<span data-ttu-id="e6e76-172">L' `--tag` indicateur de nom confus (qui peut être raccourci `-t` ) spécifie le nom complet de l’image, y compris la balise réelle si elle est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e6e76-172">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="e6e76-173">Le `.` à la fin spécifie le contexte dans lequel la build sera exécutée ; le répertoire de travail actuel pour les `COPY` commandes dans fichier dockerfile.</span><span class="sxs-lookup"><span data-stu-id="e6e76-173">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="e6e76-174">Si vous avez plusieurs applications au sein d’une même solution, vous pouvez conserver les fichier dockerfile pour chaque application dans son propre dossier, en regard du `.csproj` fichier.</span><span class="sxs-lookup"><span data-stu-id="e6e76-174">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="e6e76-175">Vous devez toujours exécuter la `docker build` commande à partir du répertoire de base pour vous assurer que la solution et tous les projets sont copiés dans l’image.</span><span class="sxs-lookup"><span data-stu-id="e6e76-175">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="e6e76-176">Vous pouvez spécifier un fichier dockerfile sous le répertoire actif à l’aide de l' `--file` indicateur (ou `-f` ).</span><span class="sxs-lookup"><span data-stu-id="e6e76-176">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build -t stockdata:1.0.0 -f .\src\StockData\Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="e6e76-177">Exécuter l’image dans un conteneur sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="e6e76-177">Run the image in a container on your machine</span></span>

<span data-ttu-id="e6e76-178">Pour exécuter l’image dans votre instance de l’arrimeur local, utilisez la `docker run` commande.</span><span class="sxs-lookup"><span data-stu-id="e6e76-178">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata:1.0.0
```

<span data-ttu-id="e6e76-179">L' `-ti` indicateur connecte votre terminal actuel au terminal du conteneur et s’exécute en mode interactif.</span><span class="sxs-lookup"><span data-stu-id="e6e76-179">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="e6e76-180">Le `-p 5000:80` publie (links) le port 80 sur le conteneur vers le port 5000 sur l’interface réseau localhost.</span><span class="sxs-lookup"><span data-stu-id="e6e76-180">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="e6e76-181">Envoyer l’image dans un registre</span><span class="sxs-lookup"><span data-stu-id="e6e76-181">Push the image to a registry</span></span>

<span data-ttu-id="e6e76-182">Une fois que vous avez vérifié que l’image fonctionne, transmettez-la à un registre de l’arrimeur pour la rendre disponible sur d’autres systèmes.</span><span class="sxs-lookup"><span data-stu-id="e6e76-182">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="e6e76-183">Les réseaux internes devront approvisionner un registre Dockr.</span><span class="sxs-lookup"><span data-stu-id="e6e76-183">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="e6e76-184">Cette activité peut être aussi simple que l’exécution [de l' `registry` image de l’arrimeur](https://docs.docker.com/registry/deploying/) (le registre de l’arrimeur s’exécute dans un conteneur d’ancrage), mais il existe plusieurs solutions plus complètes disponibles.</span><span class="sxs-lookup"><span data-stu-id="e6e76-184">This activity can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="e6e76-185">Pour le partage externe et l’utilisation du Cloud, plusieurs registres gérés sont disponibles, tels que [Azure Container Registry](/azure/container-registry/) ou le [hub d’ancrage](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="e6e76-185">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="e6e76-186">Pour effectuer une transmission de type push vers le hub d’ancrage, préfixez le nom de l’image avec votre nom d’utilisateur ou d’organisation.</span><span class="sxs-lookup"><span data-stu-id="e6e76-186">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata:1.0.0 <myorg>/stockdata:1.0.0
docker push <myorg>/stockdata:1.0.0
```

<span data-ttu-id="e6e76-187">Pour effectuer une transmission de type push vers un registre privé, préfixez le nom de l’image avec le nom d’hôte du Registre et le nom de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="e6e76-187">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata <internal-registry:5000>/<myorg>/stockdata:1.0.0
docker push <internal-registry:5000>/<myorg>/stockdata:1.0.0
```

<span data-ttu-id="e6e76-188">Une fois que l’image se trouve dans un registre, vous pouvez la déployer sur des hôtes de l’arrimeur individuel ou sur un moteur d’orchestration de conteneur comme Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="e6e76-188">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e6e76-189">[Précédent](self-hosted.md) 
> [Suivant](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="e6e76-189">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
