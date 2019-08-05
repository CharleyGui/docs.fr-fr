---
title: Définition de votre application à plusieurs conteneurs avec docker-compose.yml
description: Comment spécifier la composition des microservices pour une application multiconteneur avec docker-compose.yml.
ms.date: 10/02/2018
ms.openlocfilehash: 6f526a951f50bad673a44cfd6c53664a13211a32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675956"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="67486-103">Définition de votre application à plusieurs conteneurs avec docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="67486-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="67486-104">Dans ce guide, le fichier [docker-compose.yml](https://docs.docker.com/compose/compose-file/) a été introduit dans la section [Étape 4. Définir vos services dans docker-compose.yml au moment de générer une application Docker à plusieurs conteneurs](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="67486-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="67486-105">Toutefois, il existe d’autres modes d’utilisation des fichiers docker-compose qui méritent d’être abordés plus en détail.</span><span class="sxs-lookup"><span data-stu-id="67486-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="67486-106">Par exemple, vous pouvez décrire explicitement la façon dont vous souhaitez déployer votre application à plusieurs conteneurs dans le fichier docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="67486-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="67486-107">Éventuellement, vous pouvez également décrire la façon dont vous allez générer vos images Docker personnalisées.</span><span class="sxs-lookup"><span data-stu-id="67486-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="67486-108">(Vous pouvez également générer des images Docker personnalisées avec l’interface de ligne de commande Docker CLI.)</span><span class="sxs-lookup"><span data-stu-id="67486-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="67486-109">Pour l’essentiel, vous définissez chacun des conteneurs à déployer, ainsi que certaines caractéristiques relatives à chaque déploiement de conteneur.</span><span class="sxs-lookup"><span data-stu-id="67486-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="67486-110">Une fois que vous disposez d’un fichier de description de déploiement à plusieurs conteneurs, vous pouvez déployer l’ensemble de la solution en une seule action orchestrée par la commande CLI [docker-compose up](https://docs.docker.com/compose/overview/), ou la déployer de manière transparente à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67486-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="67486-111">Sinon, vous devez utiliser l’interface CLI Docker pour effectuer un déploiement conteneur par conteneur en plusieurs étapes à l’aide de la commande `docker run` à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="67486-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="67486-112">Ainsi, chaque service défini dans docker-compose.yml doit spécifier une seule image ou une seule build.</span><span class="sxs-lookup"><span data-stu-id="67486-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="67486-113">Les autres clés sont facultatives et sont analogues à leurs homologues de ligne de commande `docker run`.</span><span class="sxs-lookup"><span data-stu-id="67486-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="67486-114">Le code YAML suivant représente la définition d’un éventuel fichier docker-compose.yml global mais unique pour l’exemple eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="67486-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="67486-115">Il ne s’agit pas du fichier docker-compose réel d’eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="67486-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="67486-116">Il s’agit plutôt d’une version simplifiée et centralisée dans un fichier unique, ce qui n’est pas la meilleure façon d’utiliser les fichiers docker-compose, comme cela sera expliqué plus tard.</span><span class="sxs-lookup"><span data-stu-id="67486-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

<span data-ttu-id="67486-117">La clé racine de ce fichier est services.</span><span class="sxs-lookup"><span data-stu-id="67486-117">The root key in this file is services.</span></span> <span data-ttu-id="67486-118">Sous cette clé, vous définissez les services que vous souhaitez déployer et exécuter quand vous exécutez la commande `docker-compose up` ou quand vous effectuez un déploiement à partir de Visual Studio à l’aide du fichier docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="67486-118">Under that key you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="67486-119">Dans le cas présent, plusieurs services sont définis pour le fichier docker-compose.yml, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="67486-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="67486-120">Nom du service</span><span class="sxs-lookup"><span data-stu-id="67486-120">Service name</span></span> | <span data-ttu-id="67486-121">Description</span><span class="sxs-lookup"><span data-stu-id="67486-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="67486-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="67486-122">webmvc</span></span>       | <span data-ttu-id="67486-123">Conteneur incluant l’application ASP.NET Core MVC qui consomme les microservices à partir du code C\# côté serveur</span><span class="sxs-lookup"><span data-stu-id="67486-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="67486-124">catalog.api</span><span class="sxs-lookup"><span data-stu-id="67486-124">catalog.api</span></span>  | <span data-ttu-id="67486-125">Conteneur incluant le microservice Catalog de l’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67486-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="67486-126">ordering.api</span><span class="sxs-lookup"><span data-stu-id="67486-126">ordering.api</span></span> | <span data-ttu-id="67486-127">Conteneur incluant le microservice Ordering de l’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67486-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="67486-128">sql.data</span><span class="sxs-lookup"><span data-stu-id="67486-128">sql.data</span></span>     | <span data-ttu-id="67486-129">Conteneur exécutant SQL Server pour Linux et contenant les bases de données de microservices</span><span class="sxs-lookup"><span data-stu-id="67486-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="67486-130">basket.api</span><span class="sxs-lookup"><span data-stu-id="67486-130">basket.api</span></span>   | <span data-ttu-id="67486-131">Conteneur incluant le microservice Basket de l’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67486-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="67486-132">basket.data</span><span class="sxs-lookup"><span data-stu-id="67486-132">basket.data</span></span>  | <span data-ttu-id="67486-133">Conteneur exécutant le service de cache REDIS, avec la base de données du panier comme cache REDIS</span><span class="sxs-lookup"><span data-stu-id="67486-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="67486-134">Conteneur d’API de service web simple</span><span class="sxs-lookup"><span data-stu-id="67486-134">A simple Web Service API container</span></span>

<span data-ttu-id="67486-135">Dans la mesure où il se concentre sur un seul conteneur, le microservice du conteneur catalog.api a une définition simple :</span><span class="sxs-lookup"><span data-stu-id="67486-135">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

<span data-ttu-id="67486-136">Ce service conteneurisé a la configuration de base suivante :</span><span class="sxs-lookup"><span data-stu-id="67486-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="67486-137">Il est basé sur l’image personnalisée eshop/catalog.api.</span><span class="sxs-lookup"><span data-stu-id="67486-137">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="67486-138">Par souci de simplicité, il n’existe aucun paramètre de clé build: dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="67486-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="67486-139">Cela signifie que l’image doit avoir été préalablement générée (avec docker build) ou téléchargée (avec la commande docker pull) à partir du registre Docker.</span><span class="sxs-lookup"><span data-stu-id="67486-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="67486-140">Il définit une variable d’environnement nommée ConnectionString à l’aide de la chaîne de connexion à utiliser par Entity Framework pour accéder à l’instance SQL Server qui contient le modèle de données du catalogue.</span><span class="sxs-lookup"><span data-stu-id="67486-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="67486-141">Dans le cas présent, le même conteneur SQL Server contient plusieurs bases de données.</span><span class="sxs-lookup"><span data-stu-id="67486-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="67486-142">Vous avez donc besoin de moins de mémoire sur votre machine de développement pour Docker.</span><span class="sxs-lookup"><span data-stu-id="67486-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="67486-143">Toutefois, vous pouvez également déployer un conteneur SQL Server pour chaque base de données de microservice.</span><span class="sxs-lookup"><span data-stu-id="67486-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="67486-144">Le nom SQL Server est sql.data, le même nom que celui utilisé pour le conteneur qui exécute l’instance SQL Server pour Linux.</span><span class="sxs-lookup"><span data-stu-id="67486-144">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="67486-145">Cela est très pratique, car cette résolution de noms (interne à l’hôte Docker) permet de résoudre l’adresse réseau, ce qui vous évite d’avoir à connaître l’adresse IP interne des conteneurs auxquels vous accédez à partir d’autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="67486-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="67486-146">Dans la mesure où la chaîne de connexion est définie par une variable d’environnement, vous pouvez définir cette variable via un autre mécanisme et à un autre moment.</span><span class="sxs-lookup"><span data-stu-id="67486-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="67486-147">Par exemple, vous pouvez définir une chaîne de connexion distincte durant le déploiement en production sur les hôtes finaux, ou à partir de vos pipelines d’intégration continue/de livraison continue dans Azure DevOps Services ou votre système DevOps préféré.</span><span class="sxs-lookup"><span data-stu-id="67486-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="67486-148">Il expose le port 80 pour l’accès interne au service catalog.api dans l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="67486-148">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="67486-149">L’hôte est une machine virtuelle Linux, car elle est basée sur une image Docker pour Linux, mais vous pouvez configurer le conteneur pour qu’il s’exécute plutôt sur une image Windows.</span><span class="sxs-lookup"><span data-stu-id="67486-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="67486-150">Il réachemine le port 80 exposé sur le conteneur vers le port 5101 de la machine hôte Docker (machine virtuelle Linux).</span><span class="sxs-lookup"><span data-stu-id="67486-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="67486-151">Il lie le service web au service sql.data (instance SQL Server pour la base de données Linux s’exécutant dans un conteneur).</span><span class="sxs-lookup"><span data-stu-id="67486-151">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="67486-152">Quand vous spécifiez cette dépendance, le conteneur catalog.api ne démarre pas tant que le conteneur sql.data n’a pas démarré. Cela est important, car catalog.api a besoin que la base de données SQL Server soit d’abord opérationnelle.</span><span class="sxs-lookup"><span data-stu-id="67486-152">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="67486-153">Toutefois, ce genre de dépendance de conteneur ne suffit pas dans la plupart des cas, car Docker effectue uniquement une vérification au niveau du conteneur.</span><span class="sxs-lookup"><span data-stu-id="67486-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="67486-154">Parfois, le service (dans le cas présent, SQL Server) n’est peut-être pas encore prêt. Il est donc conseillé d’implémenter une logique de réexécution avec interruption exponentielle dans vos microservices clients.</span><span class="sxs-lookup"><span data-stu-id="67486-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="67486-155">Ainsi, si un conteneur de dépendances n’est pas prêt pendant une courte période, l’application reste résiliente.</span><span class="sxs-lookup"><span data-stu-id="67486-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="67486-156">Il est configuré pour autoriser l’accès aux serveurs externes : le paramètre extra\_hosts vous permet d’accéder à des serveurs ou machines externes à l’hôte Docker (c’est-à-dire, situées en dehors de la machine virtuelle Linux par défaut qui est un hôte Docker de développement), par exemple une instance SQL Server locale sur votre PC de développement.</span><span class="sxs-lookup"><span data-stu-id="67486-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="67486-157">Il existe également d’autres paramètres docker-compose.yml plus avancés que nous aborderons dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="67486-157">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="67486-158">Utilisation de fichiers docker-compose pour cibler plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="67486-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="67486-159">Les fichiers docker-compose.yml sont des fichiers de définition. Ils peuvent être utilisés par plusieurs infrastructures qui comprennent ce format.</span><span class="sxs-lookup"><span data-stu-id="67486-159">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="67486-160">L’outil le plus simple est la commande docker-compose.</span><span class="sxs-lookup"><span data-stu-id="67486-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="67486-161">Ainsi, à l’aide de la commande docker-compose, vous pouvez cibler les principaux scénarios suivants.</span><span class="sxs-lookup"><span data-stu-id="67486-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="67486-162">Environnements de développement</span><span class="sxs-lookup"><span data-stu-id="67486-162">Development environments</span></span>

<span data-ttu-id="67486-163">Quand vous développez des applications, il est important de pouvoir les exécuter dans un environnement de développement isolé.</span><span class="sxs-lookup"><span data-stu-id="67486-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="67486-164">Vous pouvez vous servir de la commande CLI docker-compose pour créer cet environnement, ou utiliser Visual Studio qui exécute docker-compose de manière interne.</span><span class="sxs-lookup"><span data-stu-id="67486-164">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="67486-165">Le fichier docker-compose.yml vous permet de configurer et de documenter toutes les dépendances de service de votre application (autres services, mises en cache, bases de données, files d’attente, etc.).</span><span class="sxs-lookup"><span data-stu-id="67486-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="67486-166">À l’aide de la commande CLI docker-compose, vous pouvez créer et démarrer un ou plusieurs conteneurs pour chaque dépendance avec une seule commande (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="67486-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="67486-167">Les fichiers docker-compose.yml sont des fichiers config interprétés par le moteur Docker. Toutefois, ils servent également de fichiers de documentation pratiques sur la composition de votre application à plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="67486-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="67486-168">Environnements de test</span><span class="sxs-lookup"><span data-stu-id="67486-168">Testing environments</span></span>

<span data-ttu-id="67486-169">Les tests unitaires et les tests d’intégration sont une partie importante d’un processus de déploiement continu ou d’intégration continue (CI).</span><span class="sxs-lookup"><span data-stu-id="67486-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="67486-170">Ces tests automatisés nécessitent un environnement isolé pour ne pas être impactés par les utilisateurs ou par tout autre changement dans les données de l’application.</span><span class="sxs-lookup"><span data-stu-id="67486-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="67486-171">Avec Docker Compose, vous pouvez créer et détruire très facilement cet environnement isolé en quelques commandes, à partir de votre invite de commandes ou de vos scripts, à l’image des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="67486-171">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="67486-172">Déploiements de production</span><span class="sxs-lookup"><span data-stu-id="67486-172">Production deployments</span></span>

<span data-ttu-id="67486-173">Vous pouvez également utiliser Compose pour effectuer un déploiement sur un moteur Docker distant.</span><span class="sxs-lookup"><span data-stu-id="67486-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="67486-174">Il est assez courant d’effectuer un déploiement sur une seule instance d’hôte Docker (par exemple une machine virtuelle de production ou un serveur provisionné avec [Docker Machine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="67486-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="67486-175">Si vous utilisez un autre orchestrateur (Azure Service Fabric, Kubernetes, etc.), vous devrez peut-être ajouter des paramètres d’installation et de configuration de métadonnées comme ceux de docker-compose.yml, mais dans le format demandé par l’autre orchestrateur.</span><span class="sxs-lookup"><span data-stu-id="67486-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="67486-176">Dans tous les cas, docker-compose est un outil pratique et un format de métadonnées adapté aux workflows de développement, de test et de production, même si le workflow de production peut varier selon l’orchestrateur utilisé.</span><span class="sxs-lookup"><span data-stu-id="67486-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="67486-177">Utilisation de plusieurs fichiers docker-compose pour prendre en charge plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="67486-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="67486-178">Quand vous ciblez des environnements différents, vous devez utiliser plusieurs fichiers Compose.</span><span class="sxs-lookup"><span data-stu-id="67486-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="67486-179">Cela vous permet de créer plusieurs variantes de configuration en fonction de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="67486-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="67486-180">Remplacement du fichier docker-compose de base</span><span class="sxs-lookup"><span data-stu-id="67486-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="67486-181">Vous pouvez utiliser un fichier docker-compose.yml unique comme dans les exemples simplifiés présentés dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="67486-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="67486-182">Toutefois, cela n’est pas recommandé pour la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="67486-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="67486-183">Par défaut, Compose lit deux fichiers, un fichier docker-compose.yml et un fichier docker-compose.override.yml facultatif.</span><span class="sxs-lookup"><span data-stu-id="67486-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="67486-184">Comme indiqué dans la figure 6-11, quand vous utilisez Visual Studio et que vous activez la prise en charge de Docker, Visual Studio crée également un fichier docker-compose.vs.debug.g.yml supplémentaires pour le débogage de l’application, vous pouvez examiner ce fichier dans le dossier obj\\Docker\\ du dossier de solution principal.</span><span class="sxs-lookup"><span data-stu-id="67486-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Structure du fichier projet docker-compose : .dockerignore, pour ignorer les fichiers ; docker-compose.yml, pour composer des microservices ; docker-compose.override.yml, pour configurer l’environnement des microservices.](./media/image12.png)

<span data-ttu-id="67486-186">**Figure 6-11.**</span><span class="sxs-lookup"><span data-stu-id="67486-186">**Figure 6-11**.</span></span> <span data-ttu-id="67486-187">Fichiers docker-compose dans Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="67486-187">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="67486-188">Vous pouvez modifier les fichiers docker-compose à l’aide de n’importe quel éditeur, comme Visual Studio Code ou Sublime, et exécuter l’application avec la commande docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="67486-188">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="67486-189">Par convention, le fichier docker-compose.yml contient votre configuration de base et d’autres paramètres statiques.</span><span class="sxs-lookup"><span data-stu-id="67486-189">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="67486-190">Cela signifie que la configuration du service ne doit pas changer en fonction de l’environnement de déploiement ciblé.</span><span class="sxs-lookup"><span data-stu-id="67486-190">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="67486-191">Comme son nom l’indique, le fichier docker-compose.override.yml contient des paramètres de configuration qui remplacent la configuration de base par une configuration dépendante de l’environnement de déploiement.</span><span class="sxs-lookup"><span data-stu-id="67486-191">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="67486-192">Vous pouvez également avoir plusieurs fichiers de substitution avec des noms différents.</span><span class="sxs-lookup"><span data-stu-id="67486-192">You can have multiple override files with different names also.</span></span> <span data-ttu-id="67486-193">Les fichiers de substitution contiennent généralement des informations supplémentaires nécessaires à l’application mais spécifiques à un environnement ou un déploiement.</span><span class="sxs-lookup"><span data-stu-id="67486-193">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="67486-194">Ciblage de plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="67486-194">Targeting multiple environments</span></span>

<span data-ttu-id="67486-195">Il est courant de définir plusieurs fichiers Compose pour cibler plusieurs environnements : production, préproduction, intégration continue (CI) ou développement, par exemple.</span><span class="sxs-lookup"><span data-stu-id="67486-195">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="67486-196">Pour permettre la prise en charge de ces différences, vous pouvez diviser votre configuration Compose en plusieurs fichiers, comme le montre la figure 6-12.</span><span class="sxs-lookup"><span data-stu-id="67486-196">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Vous pouvez combiner plusieurs fichiers docker-compose\*.fml pour gérer différents environnements.](./media/image13.png)

<span data-ttu-id="67486-198">**Figure 6-12.**</span><span class="sxs-lookup"><span data-stu-id="67486-198">**Figure 6-12**.</span></span> <span data-ttu-id="67486-199">Plusieurs fichiers docker-compose remplaçant des valeurs du fichier docker-compose.yml de base</span><span class="sxs-lookup"><span data-stu-id="67486-199">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="67486-200">Vous commencez avec le fichier docker-compose.yml de base.</span><span class="sxs-lookup"><span data-stu-id="67486-200">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="67486-201">Ce fichier de base doit contenir les paramètres de configuration de base ou statiques qui ne changent pas en fonction de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="67486-201">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="67486-202">Par exemple, eShopOnContainers a le fichier de base docker-compose.yml suivant (simplifié avec moins de services) comme fichier de base.</span><span class="sxs-lookup"><span data-stu-id="67486-202">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with less services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="67486-203">Les valeurs du fichier docker-compose.yml de base ne doivent pas changer malgré les différents environnements de déploiement cibles.</span><span class="sxs-lookup"><span data-stu-id="67486-203">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="67486-204">Si vous vous concentrez sur la définition de service webmvc, par exemple, vous pouvez constater que les informations sont les mêmes, quel que soit l’environnement ciblé.</span><span class="sxs-lookup"><span data-stu-id="67486-204">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="67486-205">Vous disposez des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="67486-205">You have the following information:</span></span>

- <span data-ttu-id="67486-206">Nom du service : webmvc</span><span class="sxs-lookup"><span data-stu-id="67486-206">The service name: webmvc.</span></span>

- <span data-ttu-id="67486-207">Image personnalisée du conteneur : eshop/webmvc</span><span class="sxs-lookup"><span data-stu-id="67486-207">The container’s custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="67486-208">Commande de génération de l’image Docker personnalisée, indiquant quel fichier Docker utiliser</span><span class="sxs-lookup"><span data-stu-id="67486-208">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="67486-209">Dépendances avec d’autres services, pour empêcher ce conteneur de démarrer avant les autres conteneurs de dépendances</span><span class="sxs-lookup"><span data-stu-id="67486-209">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="67486-210">Vous pouvez avoir une configuration supplémentaire, mais le point important est que le fichier docker-compose.yml de base vous sert simplement à définir les informations communes aux environnements.</span><span class="sxs-lookup"><span data-stu-id="67486-210">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="67486-211">Ensuite, dans le fichier docker-compose.override.yml ou les fichiers similaires de production ou de préproduction, vous devez placer une configuration spécifique à chaque environnement.</span><span class="sxs-lookup"><span data-stu-id="67486-211">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="67486-212">En règle générale, le fichier docker-compose.override.yml est utilisé pour votre environnement de développement, comme dans l’exemple suivant d’eShopOnContainers :</span><span class="sxs-lookup"><span data-stu-id="67486-212">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity.api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="67486-213">Dans cet exemple, la configuration de substitution de l’environnement de développement expose certains ports à l’hôte, définit les variables d’environnement à l’aide d’URL de redirection et spécifie les chaînes de connexion de l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="67486-213">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="67486-214">Ces paramètres concernent juste l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="67486-214">These settings are all just for the development environment.</span></span>

<span data-ttu-id="67486-215">Quand vous exécutez `docker-compose up`, ou quand vous lancez cette commande à partir de Visual Studio, elle lit automatiquement les remplacements comme si elle fusionnait les deux fichiers.</span><span class="sxs-lookup"><span data-stu-id="67486-215">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="67486-216">Supposons que vous souhaitiez un autre fichier Compose pour l’environnement de production, avec d’autres valeurs de configuration, ports ou chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="67486-216">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="67486-217">Vous pouvez créer un autre fichier de substitution, par exemple le fichier nommé `docker-compose.prod.yml`, avec d’autres paramètres et variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="67486-217">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="67486-218">Ce fichier peut être stocké dans un autre dépôt Git, ou être géré et sécurisé par une autre équipe.</span><span class="sxs-lookup"><span data-stu-id="67486-218">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="67486-219">Comment effectuer un déploiement avec un fichier de substitution spécifique</span><span class="sxs-lookup"><span data-stu-id="67486-219">How to deploy with a specific override file</span></span>

<span data-ttu-id="67486-220">Pour utiliser plusieurs fichiers de substitution ou un fichier de substitution avec un autre nom, vous pouvez spécifier l’option -f avec la commande docker-compose et les fichiers souhaités.</span><span class="sxs-lookup"><span data-stu-id="67486-220">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="67486-221">Compose fusionne les fichiers dans l’ordre indiqué sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="67486-221">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="67486-222">L’exemple suivant montre comment effectuer un déploiement avec des fichiers de substitution.</span><span class="sxs-lookup"><span data-stu-id="67486-222">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="67486-223">Utilisation de variables d’environnement dans les fichiers docker-compose</span><span class="sxs-lookup"><span data-stu-id="67486-223">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="67486-224">Il est pratique, surtout dans les environnements de production, d’obtenir des informations de configuration à partir de variables d’environnement, comme nous l’avons montré dans les exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="67486-224">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="67486-225">Vous pouvez référencer une variable d’environnement dans vos fichiers docker-compose à l’aide de la syntaxe ${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="67486-225">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="67486-226">La ligne suivante d’un fichier docker-compose.prod.yml montre comment référencer la valeur d’une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="67486-226">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="67486-227">Les variables d’environnement sont créées et initialisées de différentes manières, en fonction de votre environnement hôte (Linux, Windows, cluster Cloud, etc.).</span><span class="sxs-lookup"><span data-stu-id="67486-227">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="67486-228">Toutefois, une approche pratique consiste à utiliser un fichier .env.</span><span class="sxs-lookup"><span data-stu-id="67486-228">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="67486-229">Les fichiers docker-compose prennent en charge la déclaration de variables d’environnement par défaut dans le fichier .env.</span><span class="sxs-lookup"><span data-stu-id="67486-229">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="67486-230">Ces valeurs de variables d’environnement sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="67486-230">These values for the environment variables are the default values.</span></span> <span data-ttu-id="67486-231">Toutefois, elles peuvent être remplacées par les valeurs que vous avez définies dans chacun de vos environnements (OS hôte ou variables d’environnement de votre cluster).</span><span class="sxs-lookup"><span data-stu-id="67486-231">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="67486-232">Vous placez ce fichier .env dans le dossier à partir duquel la commande docker-compose est exécutée.</span><span class="sxs-lookup"><span data-stu-id="67486-232">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="67486-233">L’exemple suivant illustre un fichier .env semblable au fichier [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) de l’application eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="67486-233">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="67486-234">Docker-compose s’attend à ce que chaque ligne d’un fichier .env soit au format \<variable\>=\<valeurs\>.</span><span class="sxs-lookup"><span data-stu-id="67486-234">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="67486-235">Notez que les valeurs définies dans l’environnement d’exécution remplacent toujours les valeurs définies dans le fichier .env.</span><span class="sxs-lookup"><span data-stu-id="67486-235">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="67486-236">De même, les valeurs passées via les arguments de ligne de commande remplacent également les valeurs par défaut définies dans le fichier .env.</span><span class="sxs-lookup"><span data-stu-id="67486-236">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="67486-237">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67486-237">Additional resources</span></span>

- <span data-ttu-id="67486-238">**Vue d’ensemble de Docker Compose** </span><span class="sxs-lookup"><span data-stu-id="67486-238">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="67486-239">**Fichiers Compose multiples** </span><span class="sxs-lookup"><span data-stu-id="67486-239">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="67486-240">Génération d’images Docker ASP.NET Core optimisées</span><span class="sxs-lookup"><span data-stu-id="67486-240">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="67486-241">Si vous recherchez des sources relatives à Docker et .NET Core sur Internet, vous trouverez des fichiers Docker qui illustrent la simplicité de la génération d’une image Docker. En effet, il vous suffit de copier votre source dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="67486-241">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="67486-242">Ces exemples suggèrent qu’à l’aide d’une configuration toute simple, vous pouvez disposer d’une image Docker où l’environnement et votre application font partie d’un même package.</span><span class="sxs-lookup"><span data-stu-id="67486-242">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="67486-243">L’exemple suivant montre un fichier Docker de ce genre.</span><span class="sxs-lookup"><span data-stu-id="67486-243">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="67486-244">Un fichier Docker comme celui-ci va fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="67486-244">A Dockerfile like this will work.</span></span> <span data-ttu-id="67486-245">Toutefois, vous pouvez considérablement optimiser vos images, en particulier vos images de production.</span><span class="sxs-lookup"><span data-stu-id="67486-245">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="67486-246">Dans le modèle reposant sur un conteneur et des microservices, vous démarrez constamment des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="67486-246">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="67486-247">En règle générale, l’utilisation de conteneurs n’entraîne pas le redémarrage d’un conteneur en veille, car le conteneur peut être supprimé.</span><span class="sxs-lookup"><span data-stu-id="67486-247">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="67486-248">Les orchestrateurs (comme Kubernetes et Azure Service Fabric) créent simplement des instances d’images.</span><span class="sxs-lookup"><span data-stu-id="67486-248">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="67486-249">Cela signifie que vous devez effectuer une optimisation en précompilant l’application au moment de sa génération pour accélérer le processus d’instanciation.</span><span class="sxs-lookup"><span data-stu-id="67486-249">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="67486-250">Une fois que le conteneur a démarré, il est prêt à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="67486-250">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="67486-251">N’effectuez pas d’opérations de restauration ou de compilation au moment de l’exécution à l’aide des commandes `dotnet restore` et `dotnet build` à partir de l’interface CLI dotnet, comme indiqué dans de nombreux billets de blog sur .NET Core et Docker.</span><span class="sxs-lookup"><span data-stu-id="67486-251">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="67486-252">L’équipe .NET a effectué un travail important pour faire de .NET Core et d’ASP.NET Core un framework optimisé pour les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="67486-252">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="67486-253">.NET Core n’est pas seulement un framework léger doté d’une faible empreinte mémoire. L’équipe s’est concentrée sur des images Docker optimisées pour trois grands scénarios et les a publiées dans le registre Docker Hub à l’emplacement *dotnet/core*, à compter de la version 2.1 :</span><span class="sxs-lookup"><span data-stu-id="67486-253">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="67486-254">**Développement** : la priorité est donnée à la rapidité des itérations et du débogage des modifications, la taille étant secondaire.</span><span class="sxs-lookup"><span data-stu-id="67486-254">**Development**: Where the priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="67486-255">**Génération** : la priorité est la compilation de l’application, et cela inclut les fichiers binaires et les autres dépendances pour optimiser les fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="67486-255">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="67486-256">**Production** : l’objectif étant de déployer et de lancer rapidement les conteneurs, ces images sont limitées aux binaires et au contenu nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="67486-256">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content needed to run the application.</span></span>

<span data-ttu-id="67486-257">Pour cela, l’équipe .NET fournit trois variantes de base dans [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (sur Docker Hub) :</span><span class="sxs-lookup"><span data-stu-id="67486-257">To achieve this, the .NET team is providing four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="67486-258">**sdk** : pour les scénarios de développement et de build</span><span class="sxs-lookup"><span data-stu-id="67486-258">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="67486-259">**aspnet** : pour les scénarios de production ASP.NET</span><span class="sxs-lookup"><span data-stu-id="67486-259">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="67486-260">**runtime** : pour les scénarios de production .NET</span><span class="sxs-lookup"><span data-stu-id="67486-260">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="67486-261">**runtime-deps** : pour les scénarios de production des [applications autonomes](../../../core/deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="67486-261">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#self-contained-deployments-scd).</span></span>

<span data-ttu-id="67486-262">Pour accélérer le démarrage, les images de runtime définissent aussi automatiquement aspnetcore\_urls sur le port 80 et utilisent Ngen pour créer un cache d’image native d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="67486-262">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="67486-263">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67486-263">Additional resources</span></span>

- <span data-ttu-id="67486-264">**Génération d’images Docker optimisées avec ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="67486-264">**Building Optimized Docker Images with ASP.NET Core** </span></span>\
    <https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/>

- <span data-ttu-id="67486-265">**Création d’images Docker pour les applications .NET Core** </span><span class="sxs-lookup"><span data-stu-id="67486-265">**Building Docker Images for .NET Core Applications** </span></span>\
    [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

> [!div class="step-by-step"]
> <span data-ttu-id="67486-266">[Précédent](data-driven-crud-microservice.md)
> [Suivant](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="67486-266">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
