---
title: Définition de votre application à plusieurs conteneurs avec docker-compose.yml
description: Comment spécifier la composition des microservices pour une application multiconteneur avec docker-compose.yml.
ms.date: 01/30/2020
ms.openlocfilehash: 66775b573c46041475e9cddc622bbde78ae44bc4
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805607"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="bcf35-103">Définition de votre application à plusieurs conteneurs avec docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="bcf35-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="bcf35-104">Dans ce guide, le fichier [docker-compose.yml](https://docs.docker.com/compose/compose-file/) a été introduit dans la section [Étape 4. Définissez vos services dans docker-compose.yml lors de la construction d’une application Docker multi-conteneurs](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="bcf35-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="bcf35-105">Toutefois, il existe d’autres modes d’utilisation des fichiers docker-compose qui méritent d’être abordés plus en détail.</span><span class="sxs-lookup"><span data-stu-id="bcf35-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="bcf35-106">Par exemple, vous pouvez décrire explicitement la façon dont vous souhaitez déployer votre application à plusieurs conteneurs dans le fichier docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="bcf35-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="bcf35-107">Éventuellement, vous pouvez également décrire la façon dont vous allez générer vos images Docker personnalisées.</span><span class="sxs-lookup"><span data-stu-id="bcf35-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="bcf35-108">(Vous pouvez également générer des images Docker personnalisées avec l’interface de ligne de commande Docker CLI.)</span><span class="sxs-lookup"><span data-stu-id="bcf35-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="bcf35-109">Pour l’essentiel, vous définissez chacun des conteneurs à déployer, ainsi que certaines caractéristiques relatives à chaque déploiement de conteneur.</span><span class="sxs-lookup"><span data-stu-id="bcf35-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="bcf35-110">Une fois que vous disposez d’un fichier de description de déploiement à plusieurs conteneurs, vous pouvez déployer l’ensemble de la solution en une seule action orchestrée par la commande CLI [docker-compose up](https://docs.docker.com/compose/overview/), ou la déployer de manière transparente à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcf35-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="bcf35-111">Sinon, vous devez utiliser l’interface CLI Docker pour effectuer un déploiement conteneur par conteneur en plusieurs étapes à l’aide de la commande `docker run` à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bcf35-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="bcf35-112">Ainsi, chaque service défini dans docker-compose.yml doit spécifier une seule image ou une seule build.</span><span class="sxs-lookup"><span data-stu-id="bcf35-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="bcf35-113">Les autres clés sont facultatives et sont analogues à leurs homologues de ligne de commande `docker run`.</span><span class="sxs-lookup"><span data-stu-id="bcf35-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="bcf35-114">Le code YAML suivant représente la définition d’un éventuel fichier docker-compose.yml global mais unique pour l’exemple eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="bcf35-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="bcf35-115">Il ne s’agit pas du fichier docker-compose réel d’eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="bcf35-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="bcf35-116">Il s’agit plutôt d’une version simplifiée et centralisée dans un fichier unique, ce qui n’est pas la meilleure façon d’utiliser les fichiers docker-compose, comme cela sera expliqué plus tard.</span><span class="sxs-lookup"><span data-stu-id="bcf35-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
      - BasketUrl=http://basket-api
    ports:
      - "5100:80"
    depends_on:
      - catalog-api
      - ordering-api
      - basket-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  basket-api:
    image: eshop/basket-api
    environment:
      - ConnectionString=sqldata
    ports:
      - "5103:80"
    depends_on:
      - sqldata

  sqldata:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basketdata:
    image: redis
```

<span data-ttu-id="bcf35-117">La clé racine de ce fichier est services.</span><span class="sxs-lookup"><span data-stu-id="bcf35-117">The root key in this file is services.</span></span> <span data-ttu-id="bcf35-118">Sous cette clé, vous définissez les services que `docker-compose up` vous souhaitez déployer et exécuter lorsque vous exécutez la commande ou lorsque vous vous déployez à partir de Visual Studio en utilisant ce fichier docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="bcf35-118">Under that key, you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="bcf35-119">Dans le cas présent, plusieurs services sont définis pour le fichier docker-compose.yml, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="bcf35-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="bcf35-120">Nom du service</span><span class="sxs-lookup"><span data-stu-id="bcf35-120">Service name</span></span> | <span data-ttu-id="bcf35-121">Description</span><span class="sxs-lookup"><span data-stu-id="bcf35-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="bcf35-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="bcf35-122">webmvc</span></span>       | <span data-ttu-id="bcf35-123">Conteneur incluant l’application ASP.NET Core MVC qui consomme les microservices à partir du code C\# côté serveur</span><span class="sxs-lookup"><span data-stu-id="bcf35-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="bcf35-124">catalogue-api</span><span class="sxs-lookup"><span data-stu-id="bcf35-124">catalog-api</span></span>  | <span data-ttu-id="bcf35-125">Conteneur incluant le microservice Catalog de l’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bcf35-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="bcf35-126">commande-api</span><span class="sxs-lookup"><span data-stu-id="bcf35-126">ordering-api</span></span> | <span data-ttu-id="bcf35-127">Conteneur incluant le microservice Ordering de l’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bcf35-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="bcf35-128">Sqldata</span><span class="sxs-lookup"><span data-stu-id="bcf35-128">sqldata</span></span>     | <span data-ttu-id="bcf35-129">Conteneur exécutant SQL Server pour Linux et contenant les bases de données de microservices</span><span class="sxs-lookup"><span data-stu-id="bcf35-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="bcf35-130">panier-api</span><span class="sxs-lookup"><span data-stu-id="bcf35-130">basket-api</span></span>   | <span data-ttu-id="bcf35-131">Conteneur incluant le microservice Basket de l’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bcf35-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="bcf35-132">basketdata</span><span class="sxs-lookup"><span data-stu-id="bcf35-132">basketdata</span></span>  | <span data-ttu-id="bcf35-133">Conteneur exécutant le service de cache REDIS, avec la base de données du panier comme cache REDIS</span><span class="sxs-lookup"><span data-stu-id="bcf35-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="bcf35-134">Conteneur d’API de service web simple</span><span class="sxs-lookup"><span data-stu-id="bcf35-134">A simple Web Service API container</span></span>

<span data-ttu-id="bcf35-135">Se concentrant sur un seul conteneur, le catalogue-api conteneur-microservice a une définition simple:</span><span class="sxs-lookup"><span data-stu-id="bcf35-135">Focusing on a single container, the catalog-api container-microservice has a straightforward definition:</span></span>

```yml
  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata
```

<span data-ttu-id="bcf35-136">Ce service conteneurisé a la configuration de base suivante :</span><span class="sxs-lookup"><span data-stu-id="bcf35-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="bcf35-137">Il est basé sur l’image **eshop/catalogue-api** personnalisée.</span><span class="sxs-lookup"><span data-stu-id="bcf35-137">It is based on the custom **eshop/catalog-api** image.</span></span> <span data-ttu-id="bcf35-138">Pour l’amour de la simplicité, il n’y a pas de build: réglage de clé dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="bcf35-138">For simplicity's sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="bcf35-139">Cela signifie que l’image doit avoir été préalablement générée (avec docker build) ou téléchargée (avec la commande docker pull) à partir du registre Docker.</span><span class="sxs-lookup"><span data-stu-id="bcf35-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="bcf35-140">Il définit une variable d’environnement nommée ConnectionString à l’aide de la chaîne de connexion à utiliser par Entity Framework pour accéder à l’instance SQL Server qui contient le modèle de données du catalogue.</span><span class="sxs-lookup"><span data-stu-id="bcf35-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="bcf35-141">Dans le cas présent, le même conteneur SQL Server contient plusieurs bases de données.</span><span class="sxs-lookup"><span data-stu-id="bcf35-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="bcf35-142">Vous avez donc besoin de moins de mémoire sur votre machine de développement pour Docker.</span><span class="sxs-lookup"><span data-stu-id="bcf35-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="bcf35-143">Toutefois, vous pouvez également déployer un conteneur SQL Server pour chaque base de données de microservice.</span><span class="sxs-lookup"><span data-stu-id="bcf35-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="bcf35-144">Le nom SQL Server est **sqldata**, qui est le même nom utilisé pour le conteneur qui est en cours d’exécution de l’instance SQL Server pour Linux.</span><span class="sxs-lookup"><span data-stu-id="bcf35-144">The SQL Server name is **sqldata**, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="bcf35-145">C’est pratique; être en mesure d’utiliser cette résolution de nom (interne à l’hôte Docker) résoudra l’adresse réseau de sorte que vous n’avez pas besoin de connaître la propriété intellectuelle interne pour les conteneurs que vous accédez à partir d’autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="bcf35-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don't need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="bcf35-146">Dans la mesure où la chaîne de connexion est définie par une variable d’environnement, vous pouvez définir cette variable via un autre mécanisme et à un autre moment.</span><span class="sxs-lookup"><span data-stu-id="bcf35-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="bcf35-147">Par exemple, vous pouvez définir une chaîne de connexion distincte durant le déploiement en production sur les hôtes finaux, ou à partir de vos pipelines d’intégration continue/de livraison continue dans Azure DevOps Services ou votre système DevOps préféré.</span><span class="sxs-lookup"><span data-stu-id="bcf35-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="bcf35-148">Il expose le port 80 pour un accès interne au service **catalogue-api** au sein de l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="bcf35-148">It exposes port 80 for internal access to the **catalog-api** service within the Docker host.</span></span> <span data-ttu-id="bcf35-149">L’hôte est une machine virtuelle Linux, car elle est basée sur une image Docker pour Linux, mais vous pouvez configurer le conteneur pour qu’il s’exécute plutôt sur une image Windows.</span><span class="sxs-lookup"><span data-stu-id="bcf35-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="bcf35-150">Il réachemine le port 80 exposé sur le conteneur vers le port 5101 de la machine hôte Docker (machine virtuelle Linux).</span><span class="sxs-lookup"><span data-stu-id="bcf35-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="bcf35-151">Il relie le service web au service **sqldata** (l’exemple SQL Server pour la base de données Linux en cours d’exécution dans un conteneur).</span><span class="sxs-lookup"><span data-stu-id="bcf35-151">It links the web service to the **sqldata** service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="bcf35-152">Lorsque vous spécifiez cette dépendance, le conteneur catalogue-api ne démarre pas tant que le conteneur sqldata n’aura pas déjà commencé; c’est important parce que le catalogue-api a besoin d’avoir la base de données SQL Server en place et en cours d’exécution en premier.</span><span class="sxs-lookup"><span data-stu-id="bcf35-152">When you specify this dependency, the catalog-api container will not start until the sqldata container has already started; this is important because catalog-api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="bcf35-153">Toutefois, ce genre de dépendance de conteneur ne suffit pas dans la plupart des cas, car Docker effectue uniquement une vérification au niveau du conteneur.</span><span class="sxs-lookup"><span data-stu-id="bcf35-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="bcf35-154">Parfois, le service (dans le cas présent, SQL Server) n’est peut-être pas encore prêt. Il est donc conseillé d’implémenter une logique de réexécution avec interruption exponentielle dans vos microservices clients.</span><span class="sxs-lookup"><span data-stu-id="bcf35-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="bcf35-155">Ainsi, si un conteneur de dépendances n’est pas prêt pendant une courte période, l’application reste résiliente.</span><span class="sxs-lookup"><span data-stu-id="bcf35-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="bcf35-156">Il est configuré pour permettre l’accès à des serveurs externes : le paramètre d’hôtes supplémentaire\_vous permet d’accéder à des serveurs ou des machines externes en dehors de l’hôte Docker (c’est-à-dire en dehors de la VM Linux par défaut, qui est un hôte Docker de développement), comme une instance locale SQL Server sur votre PC de développement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM, which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="bcf35-157">Il y a également `docker-compose.yml` d’autres paramètres plus avancés dont nous discuterons dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="bcf35-157">There are also other, more advanced `docker-compose.yml` settings that we'll discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="bcf35-158">Utilisation de fichiers docker-compose pour cibler plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="bcf35-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="bcf35-159">Les `docker-compose.*.yml` fichiers sont des fichiers de définition et peuvent être utilisés par plusieurs infrastructures qui comprennent ce format.</span><span class="sxs-lookup"><span data-stu-id="bcf35-159">The `docker-compose.*.yml` files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="bcf35-160">L’outil le plus simple est la commande docker-compose.</span><span class="sxs-lookup"><span data-stu-id="bcf35-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="bcf35-161">Ainsi, à l’aide de la commande docker-compose, vous pouvez cibler les principaux scénarios suivants.</span><span class="sxs-lookup"><span data-stu-id="bcf35-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="bcf35-162">Environnements de développement</span><span class="sxs-lookup"><span data-stu-id="bcf35-162">Development environments</span></span>

<span data-ttu-id="bcf35-163">Quand vous développez des applications, il est important de pouvoir les exécuter dans un environnement de développement isolé.</span><span class="sxs-lookup"><span data-stu-id="bcf35-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="bcf35-164">Vous pouvez utiliser la commande CLI docker-compose pour créer cet environnement ou Visual Studio, qui utilise docker-compose sous les couvertures.</span><span class="sxs-lookup"><span data-stu-id="bcf35-164">You can use the docker-compose CLI command to create that environment or Visual Studio, which uses docker-compose under the covers.</span></span>

<span data-ttu-id="bcf35-165">Le fichier docker-compose.yml vous permet de configurer et de documenter toutes les dépendances de service de votre application (autres services, cache, bases de données, files d’attente, etc.).</span><span class="sxs-lookup"><span data-stu-id="bcf35-165">The docker-compose.yml file allows you to configure and document all your application's service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="bcf35-166">À l’aide de la commande CLI docker-compose, vous pouvez créer et démarrer un ou plusieurs conteneurs pour chaque dépendance avec une seule commande (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="bcf35-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="bcf35-167">Les fichiers docker-compose.yml sont des fichiers config interprétés par le moteur Docker. Toutefois, ils servent également de fichiers de documentation pratiques sur la composition de votre application à plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="bcf35-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="bcf35-168">Environnements de test</span><span class="sxs-lookup"><span data-stu-id="bcf35-168">Testing environments</span></span>

<span data-ttu-id="bcf35-169">Les tests unitaires et les tests d’intégration sont une partie importante d’un processus de déploiement continu ou d’intégration continue (CI).</span><span class="sxs-lookup"><span data-stu-id="bcf35-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="bcf35-170">Ces tests automatisés nécessitent un environnement isolé de sorte qu’ils ne sont pas touchés par les utilisateurs ou tout autre changement dans les données de l’application.</span><span class="sxs-lookup"><span data-stu-id="bcf35-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application's data.</span></span>

<span data-ttu-id="bcf35-171">Avec Docker Compose, vous pouvez créer et détruire cet environnement isolé très facilement dans quelques commandes de votre invite de commande ou des scripts, comme les commandes suivantes:</span><span class="sxs-lookup"><span data-stu-id="bcf35-171">With Docker Compose, you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="bcf35-172">Déploiements de production</span><span class="sxs-lookup"><span data-stu-id="bcf35-172">Production deployments</span></span>

<span data-ttu-id="bcf35-173">Vous pouvez également utiliser Compose pour effectuer un déploiement sur un moteur Docker distant.</span><span class="sxs-lookup"><span data-stu-id="bcf35-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="bcf35-174">Il est assez courant d’effectuer un déploiement sur une seule instance d’hôte Docker (par exemple une machine virtuelle de production ou un serveur provisionné avec [Docker Machine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="bcf35-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="bcf35-175">Si vous utilisez un autre orchestrateur (Azure Service Fabric, Kubernetes, etc.), vous devrez peut-être ajouter des paramètres d’installation et de configuration de métadonnées comme ceux de docker-compose.yml, mais dans le format demandé par l’autre orchestrateur.</span><span class="sxs-lookup"><span data-stu-id="bcf35-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="bcf35-176">Dans tous les cas, docker-compose est un outil pratique et un format de métadonnées adapté aux workflows de développement, de test et de production, même si le workflow de production peut varier selon l’orchestrateur utilisé.</span><span class="sxs-lookup"><span data-stu-id="bcf35-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="bcf35-177">Utilisation de plusieurs fichiers docker-compose pour prendre en charge plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="bcf35-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="bcf35-178">Quand vous ciblez des environnements différents, vous devez utiliser plusieurs fichiers Compose.</span><span class="sxs-lookup"><span data-stu-id="bcf35-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="bcf35-179">Cela vous permet de créer plusieurs variantes de configuration en fonction de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="bcf35-180">Remplacement du fichier docker-compose de base</span><span class="sxs-lookup"><span data-stu-id="bcf35-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="bcf35-181">Vous pouvez utiliser un fichier docker-compose.yml unique comme dans les exemples simplifiés présentés dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="bcf35-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="bcf35-182">Toutefois, cela n’est pas recommandé pour la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="bcf35-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="bcf35-183">Par défaut, Compose lit deux fichiers, un fichier docker-compose.yml et un fichier docker-compose.override.yml facultatif.</span><span class="sxs-lookup"><span data-stu-id="bcf35-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="bcf35-184">Comme indiqué dans la figure 6-11, quand vous utilisez Visual Studio et que vous activez la prise en charge de Docker, Visual Studio crée également un fichier docker-compose.vs.debug.g.yml supplémentaires pour le débogage de l’application, vous pouvez examiner ce fichier dans le dossier obj\\Docker\\ du dossier de solution principal.</span><span class="sxs-lookup"><span data-stu-id="bcf35-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Les fichiers dans un projet de composition docker.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

<span data-ttu-id="bcf35-186">**Figure 6-11.**</span><span class="sxs-lookup"><span data-stu-id="bcf35-186">**Figure 6-11**.</span></span> <span data-ttu-id="bcf35-187">dossiers docker-compose dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bcf35-187">docker-compose files in Visual Studio 2019</span></span>

<span data-ttu-id="bcf35-188">structure de fichier de projet **docker-compose** :</span><span class="sxs-lookup"><span data-stu-id="bcf35-188">**docker-compose** project file structure:</span></span>

- <span data-ttu-id="bcf35-189">*.dockerignore* - utilisé pour ignorer les fichiers</span><span class="sxs-lookup"><span data-stu-id="bcf35-189">*.dockerignore* - used to ignore files</span></span>
- <span data-ttu-id="bcf35-190">*docker-compose.yml* - utilisé pour composer des microservices</span><span class="sxs-lookup"><span data-stu-id="bcf35-190">*docker-compose.yml* - used to compose microservices</span></span>
- <span data-ttu-id="bcf35-191">*docker-compose.override.yml* - utilisé pour configurer l’environnement des microservices</span><span class="sxs-lookup"><span data-stu-id="bcf35-191">*docker-compose.override.yml* - used to configure microservices environment</span></span>

<span data-ttu-id="bcf35-192">Vous pouvez modifier les fichiers docker-compose à l’aide de n’importe quel éditeur, comme Visual Studio Code ou Sublime, et exécuter l’application avec la commande docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="bcf35-192">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="bcf35-193">Par convention, le fichier docker-compose.yml contient votre configuration de base et d’autres paramètres statiques.</span><span class="sxs-lookup"><span data-stu-id="bcf35-193">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="bcf35-194">Cela signifie que la configuration du service ne doit pas changer en fonction de l’environnement de déploiement ciblé.</span><span class="sxs-lookup"><span data-stu-id="bcf35-194">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="bcf35-195">Comme son nom l’indique, le fichier docker-compose.override.yml contient des paramètres de configuration qui remplacent la configuration de base par une configuration dépendante de l’environnement de déploiement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-195">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="bcf35-196">Vous pouvez également avoir plusieurs fichiers de substitution avec des noms différents.</span><span class="sxs-lookup"><span data-stu-id="bcf35-196">You can have multiple override files with different names also.</span></span> <span data-ttu-id="bcf35-197">Les fichiers de substitution contiennent généralement des informations supplémentaires nécessaires à l’application mais spécifiques à un environnement ou un déploiement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-197">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="bcf35-198">Ciblage de plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="bcf35-198">Targeting multiple environments</span></span>

<span data-ttu-id="bcf35-199">Il est courant de définir plusieurs fichiers Compose pour cibler plusieurs environnements : production, préproduction, intégration continue (CI) ou développement, par exemple.</span><span class="sxs-lookup"><span data-stu-id="bcf35-199">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="bcf35-200">Pour permettre la prise en charge de ces différences, vous pouvez diviser votre configuration Compose en plusieurs fichiers, comme le montre la figure 6-12.</span><span class="sxs-lookup"><span data-stu-id="bcf35-200">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Diagramme de trois fichiers docker-compose réglés pour remplacer le fichier de base.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

<span data-ttu-id="bcf35-202">**Figure 6-12.**</span><span class="sxs-lookup"><span data-stu-id="bcf35-202">**Figure 6-12**.</span></span> <span data-ttu-id="bcf35-203">Plusieurs fichiers docker-compose remplaçant des valeurs du fichier docker-compose.yml de base</span><span class="sxs-lookup"><span data-stu-id="bcf35-203">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="bcf35-204">Vous pouvez combiner plusieurs fichiers docker-compose.yml pour gérer différents environnements.</span><span class="sxs-lookup"><span data-stu-id="bcf35-204">You can combine multiple docker-compose\*.yml files to handle different environments.</span></span> <span data-ttu-id="bcf35-205">Vous commencez avec le fichier docker-compose.yml de base.</span><span class="sxs-lookup"><span data-stu-id="bcf35-205">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="bcf35-206">Ce fichier de base doit contenir les paramètres de configuration de base ou statiques qui ne changent pas en fonction de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-206">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="bcf35-207">Par exemple, l’eShopOnContainers a le fichier docker-compose.yml suivant (simplifié avec moins de services) comme fichier de base.</span><span class="sxs-lookup"><span data-stu-id="bcf35-207">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with fewer services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket-api:
    image: eshop/basket-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basketdata
      - identity-api
      - rabbitmq

  catalog-api:
    image: eshop/catalog-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sqldata
      - rabbitmq

  marketing-api:
    image: eshop/marketing-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sqldata
      - nosqldata
      - identity-api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog-api
      - ordering-api
      - identity-api
      - basket-api
      - marketing-api

  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest

  nosqldata:
    image: mongo

  basketdata:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="bcf35-208">Les valeurs du fichier docker-compose.yml de base ne doivent pas changer malgré les différents environnements de déploiement cibles.</span><span class="sxs-lookup"><span data-stu-id="bcf35-208">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="bcf35-209">Si vous vous concentrez sur la définition de service webmvc, par exemple, vous pouvez constater que les informations sont les mêmes, quel que soit l’environnement ciblé.</span><span class="sxs-lookup"><span data-stu-id="bcf35-209">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="bcf35-210">Vous disposez des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="bcf35-210">You have the following information:</span></span>

- <span data-ttu-id="bcf35-211">Nom du service : webmvc</span><span class="sxs-lookup"><span data-stu-id="bcf35-211">The service name: webmvc.</span></span>

- <span data-ttu-id="bcf35-212">L’image personnalisée du conteneur : eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="bcf35-212">The container's custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="bcf35-213">Commande de génération de l’image Docker personnalisée, indiquant quel fichier Docker utiliser</span><span class="sxs-lookup"><span data-stu-id="bcf35-213">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="bcf35-214">Dépendances avec d’autres services, pour empêcher ce conteneur de démarrer avant les autres conteneurs de dépendances</span><span class="sxs-lookup"><span data-stu-id="bcf35-214">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="bcf35-215">Vous pouvez avoir une configuration supplémentaire, mais le point important est que le fichier docker-compose.yml de base vous sert simplement à définir les informations communes aux environnements.</span><span class="sxs-lookup"><span data-stu-id="bcf35-215">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="bcf35-216">Ensuite, dans le fichier docker-compose.override.yml ou les fichiers similaires de production ou de préproduction, vous devez placer une configuration spécifique à chaque environnement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-216">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="bcf35-217">En règle générale, le fichier docker-compose.override.yml est utilisé pour votre environnement de développement, comme dans l’exemple suivant d’eShopOnContainers :</span><span class="sxs-lookup"><span data-stu-id="bcf35-217">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basketdata}
      - identityUrl=http://identity-api
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

  catalog-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
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

  marketing-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity-api
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
      - CatalogUrlHC=http://catalog-api/hc
      - OrderingUrlHC=http://ordering-api/hc
      - IdentityUrlHC=http://identity-api/hc
      - BasketUrlHC=http://basket-api/hc
      - MarketingUrlHC=http://marketing-api/hc
      - PaymentUrlHC=http://payment-api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
  basketdata:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="bcf35-218">Dans cet exemple, la configuration de substitution de l’environnement de développement expose certains ports à l’hôte, définit les variables d’environnement à l’aide d’URL de redirection et spécifie les chaînes de connexion de l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-218">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="bcf35-219">Ces paramètres concernent juste l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-219">These settings are all just for the development environment.</span></span>

<span data-ttu-id="bcf35-220">Quand vous exécutez `docker-compose up`, ou quand vous lancez cette commande à partir de Visual Studio, elle lit automatiquement les remplacements comme si elle fusionnait les deux fichiers.</span><span class="sxs-lookup"><span data-stu-id="bcf35-220">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="bcf35-221">Supposons que vous voulez un autre fichier Compose pour l’environnement de production, avec différentes valeurs de configuration, ports ou chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="bcf35-221">Suppose that you want another Compose file for the production environment, with different configuration values, ports, or connection strings.</span></span> <span data-ttu-id="bcf35-222">Vous pouvez créer un autre fichier de substitution, par exemple le fichier nommé `docker-compose.prod.yml`, avec d’autres paramètres et variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-222">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="bcf35-223">Ce fichier peut être stocké dans un autre dépôt Git, ou être géré et sécurisé par une autre équipe.</span><span class="sxs-lookup"><span data-stu-id="bcf35-223">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="bcf35-224">Comment effectuer un déploiement avec un fichier de substitution spécifique</span><span class="sxs-lookup"><span data-stu-id="bcf35-224">How to deploy with a specific override file</span></span>

<span data-ttu-id="bcf35-225">Pour utiliser plusieurs fichiers de substitution ou un fichier de substitution avec un autre nom, vous pouvez spécifier l’option -f avec la commande docker-compose et les fichiers souhaités.</span><span class="sxs-lookup"><span data-stu-id="bcf35-225">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="bcf35-226">Compose fusionne les fichiers dans l’ordre indiqué sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bcf35-226">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="bcf35-227">L’exemple suivant montre comment effectuer un déploiement avec des fichiers de substitution.</span><span class="sxs-lookup"><span data-stu-id="bcf35-227">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="bcf35-228">Utilisation de variables d’environnement dans les fichiers docker-compose</span><span class="sxs-lookup"><span data-stu-id="bcf35-228">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="bcf35-229">Il est pratique, surtout dans les environnements de production, d’obtenir des informations de configuration à partir de variables d’environnement, comme nous l’avons montré dans les exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="bcf35-229">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="bcf35-230">Vous pouvez référencer une variable d’environnement dans vos fichiers docker-compose à l’aide de la syntaxe ${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="bcf35-230">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="bcf35-231">La ligne suivante d’un fichier docker-compose.prod.yml montre comment référencer la valeur d’une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-231">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="bcf35-232">Les variables d’environnement sont créées et initialisées de différentes manières, en fonction de votre environnement hôte (Linux, Windows, cluster Cloud, etc.).</span><span class="sxs-lookup"><span data-stu-id="bcf35-232">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="bcf35-233">Toutefois, une approche pratique consiste à utiliser un fichier .env.</span><span class="sxs-lookup"><span data-stu-id="bcf35-233">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="bcf35-234">Les fichiers docker-compose prennent en charge la déclaration de variables d’environnement par défaut dans le fichier .env.</span><span class="sxs-lookup"><span data-stu-id="bcf35-234">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="bcf35-235">Ces valeurs de variables d’environnement sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="bcf35-235">These values for the environment variables are the default values.</span></span> <span data-ttu-id="bcf35-236">Toutefois, elles peuvent être remplacées par les valeurs que vous avez définies dans chacun de vos environnements (OS hôte ou variables d’environnement de votre cluster).</span><span class="sxs-lookup"><span data-stu-id="bcf35-236">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="bcf35-237">Vous placez ce fichier .env dans le dossier à partir duquel la commande docker-compose est exécutée.</span><span class="sxs-lookup"><span data-stu-id="bcf35-237">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="bcf35-238">L’exemple suivant illustre un fichier .env semblable au fichier [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) de l’application eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="bcf35-238">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="bcf35-239">Docker-compose s’attend à ce que chaque ligne d’un fichier .env soit au format \<variable\>=\<valeurs\>.</span><span class="sxs-lookup"><span data-stu-id="bcf35-239">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="bcf35-240">Les valeurs définies dans l’environnement de run-time l’emportent toujours sur les valeurs définies à l’intérieur du fichier .env.</span><span class="sxs-lookup"><span data-stu-id="bcf35-240">The values set in the run-time environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="bcf35-241">De la même manière, les valeurs transmises par l’intermédiaire d’arguments de ligne de commande l’emportent également sur les valeurs par défaut définies dans le fichier .env.</span><span class="sxs-lookup"><span data-stu-id="bcf35-241">In a similar way, values passed via command-line arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="bcf35-242">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="bcf35-242">Additional resources</span></span>

- <span data-ttu-id="bcf35-243">**Vue d’ensemble de Docker Compose** </span><span class="sxs-lookup"><span data-stu-id="bcf35-243">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="bcf35-244">**Fichiers Composition multiples** </span><span class="sxs-lookup"><span data-stu-id="bcf35-244">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="bcf35-245">Génération d’images Docker ASP.NET Core optimisées</span><span class="sxs-lookup"><span data-stu-id="bcf35-245">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="bcf35-246">Si vous recherchez des sources relatives à Docker et .NET Core sur Internet, vous trouverez des fichiers Docker qui illustrent la simplicité de la génération d’une image Docker. En effet, il vous suffit de copier votre source dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="bcf35-246">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="bcf35-247">Ces exemples suggèrent qu’à l’aide d’une configuration toute simple, vous pouvez disposer d’une image Docker où l’environnement et votre application font partie d’un même package.</span><span class="sxs-lookup"><span data-stu-id="bcf35-247">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="bcf35-248">L’exemple suivant montre un fichier Docker de ce genre.</span><span class="sxs-lookup"><span data-stu-id="bcf35-248">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="bcf35-249">Un fichier Docker comme celui-ci va fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="bcf35-249">A Dockerfile like this will work.</span></span> <span data-ttu-id="bcf35-250">Toutefois, vous pouvez considérablement optimiser vos images, en particulier vos images de production.</span><span class="sxs-lookup"><span data-stu-id="bcf35-250">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="bcf35-251">Dans le modèle reposant sur un conteneur et des microservices, vous démarrez constamment des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="bcf35-251">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="bcf35-252">En règle générale, l’utilisation de conteneurs n’entraîne pas le redémarrage d’un conteneur en veille, car le conteneur peut être supprimé.</span><span class="sxs-lookup"><span data-stu-id="bcf35-252">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="bcf35-253">Les orchestrateurs (comme Kubernetes et Azure Service Fabric) créent simplement des instances d’images.</span><span class="sxs-lookup"><span data-stu-id="bcf35-253">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="bcf35-254">Cela signifie que vous devez effectuer une optimisation en précompilant l’application au moment de sa génération pour accélérer le processus d’instanciation.</span><span class="sxs-lookup"><span data-stu-id="bcf35-254">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="bcf35-255">Une fois que le conteneur a démarré, il est prêt à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="bcf35-255">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="bcf35-256">Ne restaurez pas et ne compilez pas au moment de l’exécution en utilisant les commandes et `dotnet restore` `dotnet build` CLI comme vous pouvez le voir dans les messages de blog sur .NET Core et Docker.</span><span class="sxs-lookup"><span data-stu-id="bcf35-256">Don't restore and compile at run time using the `dotnet restore` and `dotnet build` CLI commands as you may see in blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="bcf35-257">L’équipe .NET a effectué un travail important pour faire de .NET Core et d’ASP.NET Core un framework optimisé pour les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="bcf35-257">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="bcf35-258">.NET Core n’est pas seulement un framework léger doté d’une faible empreinte mémoire. L’équipe s’est concentrée sur des images Docker optimisées pour trois grands scénarios et les a publiées dans le registre Docker Hub à l’emplacement *dotnet/core*, à compter de la version 2.1 :</span><span class="sxs-lookup"><span data-stu-id="bcf35-258">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="bcf35-259">**Développement**: La priorité est la capacité d’itérer rapidement et de déboquer rapidement les changements, et où la taille est secondaire.</span><span class="sxs-lookup"><span data-stu-id="bcf35-259">**Development**: The priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="bcf35-260">**Construire**: La priorité est de compiler l’application, et l’image comprend des binaires et d’autres dépendances pour optimiser les binaires.</span><span class="sxs-lookup"><span data-stu-id="bcf35-260">**Build**: The priority is compiling the application, and the image includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="bcf35-261">**Production**: L’accent est mis sur le déploiement rapide et le démarrage des conteneurs, de sorte que ces images sont limitées aux binaires et au contenu nécessaire à l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="bcf35-261">**Production**: The focus is fast deploying and starting of containers, so these images are limited to the binaries and content needed to run the application.</span></span>

<span data-ttu-id="bcf35-262">L’équipe .NET fournit quatre variantes de base en [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (chez Docker Hub) :</span><span class="sxs-lookup"><span data-stu-id="bcf35-262">The .NET team provides four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="bcf35-263">**sdk** : pour les scénarios de développement et de build</span><span class="sxs-lookup"><span data-stu-id="bcf35-263">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="bcf35-264">**aspnet** : pour les scénarios de production ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bcf35-264">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="bcf35-265">**runtime** : pour les scénarios de production .NET</span><span class="sxs-lookup"><span data-stu-id="bcf35-265">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="bcf35-266">**runtime-deps**: pour les scénarios de production [d’applications autonomes](../../../core/deploying/index.md#publish-self-contained)</span><span class="sxs-lookup"><span data-stu-id="bcf35-266">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#publish-self-contained)</span></span>

<span data-ttu-id="bcf35-267">Pour accélérer le démarrage, les images de runtime définissent aussi automatiquement aspnetcore\_urls sur le port 80 et utilisent Ngen pour créer un cache d’image native d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="bcf35-267">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="bcf35-268">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="bcf35-268">Additional resources</span></span>

- <span data-ttu-id="bcf35-269">**Génération d’images Docker optimisées avec ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="bcf35-269">**Building Optimized Docker Images with ASP.NET Core**</span></span>  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- <span data-ttu-id="bcf35-270">**Création d’images Docker pour les applications .NET Core**</span><span class="sxs-lookup"><span data-stu-id="bcf35-270">**Building Docker Images for .NET Core Applications**</span></span>  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> <span data-ttu-id="bcf35-271">[Suivant précédent](data-driven-crud-microservice.md)
> [Next](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="bcf35-271">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
