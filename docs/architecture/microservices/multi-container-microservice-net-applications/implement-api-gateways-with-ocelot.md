---
title: Implémentation de passerelles d’API avec Ocelot
description: Découvrez comment implémenter des passerelles d’API avec Ocelot et comment utiliser Ocelot dans un environnement basé sur un conteneur.
ms.date: 10/02/2018
ms.openlocfilehash: cb452c330712ecf536cdf09f41fdbf828a4e9314
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771184"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="dc2d2-103">Implémenter des passerelles API avec Ocelot</span><span class="sxs-lookup"><span data-stu-id="dc2d2-103">Implement API Gateways with Ocelot</span></span>

<span data-ttu-id="dc2d2-104">L’application de microservices de référence [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) utilise [Ocelot](https://github.com/ThreeMammals/Ocelot), une passerelle API simple et légère que vous pouvez déployer n’importe où avec vos microservices/conteneurs, comme dans les environnements suivants utilisés par eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is using [Ocelot](https://github.com/ThreeMammals/Ocelot), a simple and lightweight API Gateway that you can deploy anywhere along with your microservices/containers, such as in any of the following environments used by eShopOnContainers.</span></span>

- <span data-ttu-id="dc2d2-105">Hôte Docker, sur votre PC de développement local, localement ou dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-105">Docker host, in your local dev PC, on-premises or in the cloud.</span></span>
- <span data-ttu-id="dc2d2-106">Cluster Kubernetes, localement ou dans le cloud managé, tel qu’Azure Kubernetes Service (AKS).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-106">Kubernetes cluster, on-premises or in managed cloud such as Azure Kubernetes Service (AKS).</span></span>
- <span data-ttu-id="dc2d2-107">Cluster Service Fabric, localement ou dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-107">Service Fabric cluster, on-premises or in the cloud.</span></span>
- <span data-ttu-id="dc2d2-108">Cloud Service Fabric, comme PaaS/Serverless dans Azure.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-108">Service Fabric mesh, as PaaS/Serverless in Azure.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="dc2d2-109">Structurer et concevoir les passerelles d’API</span><span class="sxs-lookup"><span data-stu-id="dc2d2-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="dc2d2-110">Le diagramme d’architecture suivant illustre l’implémentation de passerelles d’API avec Ocelot dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-110">The following architecture diagram shows how API Gateways are implemented with Ocelot in eShopOnContainers.</span></span>

![Diagramme d’architecture eShopOnContainers illustrant les applications clientes, les microservices et les passerelles d’API intermédiaires](./media/image28.png)

<span data-ttu-id="dc2d2-112">**Figure 6-28.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-112">**Figure 6-28**.</span></span> <span data-ttu-id="dc2d2-113">Architecture d’eShopOnContainers avec passerelles d’API</span><span class="sxs-lookup"><span data-stu-id="dc2d2-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="dc2d2-114">Ce diagramme montre comment l’application entière est déployée sur un PC de développement ou hôte Docker unique avec « Docker pour Windows » ou « Docker pour Mac ».</span><span class="sxs-lookup"><span data-stu-id="dc2d2-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with “Docker for Windows” or “Docker for Mac”.</span></span> <span data-ttu-id="dc2d2-115">Toutefois, le déploiement dans un autre orchestrateur serait assez similaire, mais n’importe quel conteneur dans le diagramme pourrait être monté en charge dans l’orchestrateur.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-115">However, deploying into any orchestrator would be pretty similar but any container in the diagram could be scaled-out in the orchestrator.</span></span>

<span data-ttu-id="dc2d2-116">De plus, les ressources de l’infrastructure telles que les bases de données, le cache et les répartiteurs de messages doivent être déchargées à partir de l’orchestrateur et déployées dans des systèmes hautement disponibles pour l’infrastructure, tels qu’Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus ou toute solution de clustering à haute disponibilité en local.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="dc2d2-117">Comme vous pouvez le constater dans le diagramme, l’utilisation de plusieurs passerelles d’API permet à plusieurs équipes de développement d’être autonomes (dans ce cas, les fonctionnalités de marketing et les fonctionnalités d’achat) lors du développement et du déploiement de leurs microservices, ainsi que de leurs passerelles d’API associées.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="dc2d2-118">Si vous aviez une passerelle d’API monolithique unique, cela signifierait qu’un point unique serait mis à jour par plusieurs équipes de développement, ce qui associerait tous les microservices à une seule partie de l’application.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="dc2d2-119">En allant beaucoup plus loin dans la conception, parfois, une passerelle d’API de granularité fine peut également être limitée à un seul microservice métier selon l’architecture choisie.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="dc2d2-120">Le fait que les limites de la passerelle d’API soient dictées par le métier ou le domaine vous aide à obtenir une meilleure conception.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-120">Having the API Gateway’s boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="dc2d2-121">Par exemple, une granularité fine au niveau de la passerelle d’API peut être particulièrement utile pour les applications d’interface utilisateur composites plus avancées qui sont basées sur des microservices, car le concept d’une passerelle d’API à granularité fine est similaire à un service de composition d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="dc2d2-122">Nous approfondissons davantage dans la section précédente, [Création d’une interface utilisateur composite basée sur des microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-122">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="dc2d2-123">Comme élément clé à retenir, pour de nombreuses applications moyennes ou grandes, l’utilisation d’un produit de passerelle d’API personnalisée constitue généralement une bonne approche. Toutefois, pas comme agrégateur monolithique unique ni comme passerelle d’API personnalisée, centrale, unique, sauf si cette passerelle API autorise plusieurs zones de configuration indépendantes pour les équipes de développement qui créent des microservices autonomes.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a><span data-ttu-id="dc2d2-124">Exemples de microservices/conteneurs à rerouter par le biais des passerelles API</span><span class="sxs-lookup"><span data-stu-id="dc2d2-124">Sample microservices/containers to re-route through the API Gateways</span></span>

<span data-ttu-id="dc2d2-125">Par exemple, eShopOnContainers a environ six types de microservices internes qui doivent être publiés par le biais des passerelles API, comme illustré à la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-125">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Seuls les microservices Basket, Catalog, Location, Marketing, Ordering et Payment sont publiés par le biais de la passerelle API.](./media/image29.png)

<span data-ttu-id="dc2d2-127">**Figure 6-29.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-127">**Figure 6-29**.</span></span> <span data-ttu-id="dc2d2-128">Dossiers de microservices dans une solution eShopOnContainers dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc2d2-128">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="dc2d2-129">En ce qui concerne le service Identity, dans sa conception, il est tenu à l’écart du routage de passerelle API, car il est le seul problème transversal du système, même si Ocelot permet également de l’inclure dans le cadre des listes de reroutages.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-129">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="dc2d2-130">Tous ces services sont actuellement implémentés en tant que services d’API web ASP.NET Core, comme vous pouvez le voir dans le code.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-130">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="dc2d2-131">Concentrons-nous sur l’un de ces microservices, tel que le code du microservice de catalogue (Catalog).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-131">Let’s focus on one of the microservices like the Catalog microservice code.</span></span>

![Vue Explorateur de solutions du projet Catalog.API.](./media/image30.png)

<span data-ttu-id="dc2d2-133">**Figure 6-30.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-133">**Figure 6-30**.</span></span> <span data-ttu-id="dc2d2-134">Exemple de microservice d’API web (microservice Catalog)</span><span class="sxs-lookup"><span data-stu-id="dc2d2-134">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="dc2d2-135">Vous pouvez voir que le microservice Catalog est un projet d’API web ASP.NET Core standard avec plusieurs contrôleurs et méthodes, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-135">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

<span data-ttu-id="dc2d2-136">La requête HTTP finit par exécuter ce type de code C# qui accède à la base de données du microservice ainsi que toute autre action supplémentaire nécessaire.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-136">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="dc2d2-137">En ce qui concerne l’URL de microservice, quand les conteneurs sont déployés sur votre PC de développement local (hôte Docker local), le conteneur de chaque microservice a toujours un port interne (généralement le port 80), spécifié dans son fichier Dockerfile, comme dans le fichier Dockerfile suivant :</span><span class="sxs-lookup"><span data-stu-id="dc2d2-137">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice’s container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="dc2d2-138">Le port 80 indiqué dans le code est interne à l’hôte Docker et n’est donc pas accessible par les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-138">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="dc2d2-139">Les applications clientes peuvent uniquement accéder aux ports externes (le cas échéant) publiés lors du déploiement avec `docker-compose`.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-139">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="dc2d2-140">Ces ports externes ne doivent pas être publiés lors du déploiement dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-140">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="dc2d2-141">C’est précisément la raison pour laquelle vous souhaitez utiliser la passerelle d’API, afin d’éviter la communication directe entre les applications clientes et les microservices.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-141">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="dc2d2-142">Toutefois, lors du développement, vous souhaitez accéder directement au microservice/conteneur et l’exécuter via Swagger.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-142">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="dc2d2-143">C’est pourquoi dans eShopOnContainers, les ports externes sont encore spécifiés même quand ils ne sont pas utilisés par la passerelle d’API ou les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-143">That’s why in eShopOnContainers, the external ports are still specified even when they won’t be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="dc2d2-144">Voici un exemple de fichier `docker-compose.override.yml` pour le microservice Catalog :</span><span class="sxs-lookup"><span data-stu-id="dc2d2-144">Here’s an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="dc2d2-145">Vous pouvez voir dans la configuration docker-compose.override.yml que le port interne pour le conteneur Catalog est le port 80, mais que le port 5101 est utilisé pour l’accès externe.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-145">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="dc2d2-146">Toutefois, ce port ne doit pas être utilisé par l’application lors de l’utilisation d’une passerelle d’API, mais seulement pour déboguer, exécuter et tester le seul microservice Catalog.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-146">But this port shouldn’t be used by the application when using an API Gateway, only to debug, run and test just the Catalog microservice.</span></span>

<span data-ttu-id="dc2d2-147">Normalement, vous n’effectuez pas de déploiement avec docker-compose dans un environnement de production, car le bon environnement de déploiement en production pour les microservices est un orchestrateur comme Kubernetes ou Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-147">Normally, you won’t be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="dc2d2-148">Lors du déploiement dans ces environnements, vous utilisez des fichiers de configuration différents dans lesquels vous ne publiez directement aucun port externe pour les microservices, mais vous utilisez toujours le proxy inverse à partir de la passerelle d’API.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-148">When deploying to those environments you use different configuration files where you won’t publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="dc2d2-149">Exécutez le microservice de catalogue sur votre hôte Docker local, soit en exécutant la solution eShopOnContainers complète à partir de Visual Studio (elle exécute tous les services dans les fichiers docker-compose), soit en démarrant simplement le microservice Catalog avec la commande docker-compose suivante dans CMD ou PowerShell positionné dans le dossier contenant les fichiers `docker-compose.yml` et docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-149">Run the catalog microservice in your local Docker host either by running the full eShopOnContainers solution from Visual Studio (it’ll run all the services in the docker-compose files) or just starting the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and docker-compose.override.yml are placed.</span></span>

```console
docker-compose run --service-ports catalog.api
```

<span data-ttu-id="dc2d2-150">Cette commande exécute uniquement le conteneur de service catalog.api, ainsi que les dépendances qui sont spécifiées dans docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-150">This command only runs the catalog.api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="dc2d2-151">Dans ce cas, le conteneur SQL Server et le conteneur RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-151">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="dc2d2-152">Ensuite, vous pouvez accéder directement au microservice Catalog et voir ses méthodes par le biais de l’interface utilisateur Swagger, en accédant directement via ce port « externe » ; dans le cas présent, `http://localhost:5101/swagger` :</span><span class="sxs-lookup"><span data-stu-id="dc2d2-152">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that “external” port, in this case `http://localhost:5101/swagger`:</span></span>

![Affichage dans le navigateur de la page d’interface utilisateur Swagger pour l’API REST Catalog.API.](./media/image31.png)

<span data-ttu-id="dc2d2-154">**Figure 6-31.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-154">**Figure 6-31**.</span></span> <span data-ttu-id="dc2d2-155">Test du microservice Catalog avec son interface utilisateur Swagger</span><span class="sxs-lookup"><span data-stu-id="dc2d2-155">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="dc2d2-156">À ce stade, vous pouvez définir un point d’arrêt dans le code C# dans Visual Studio, tester le microservice avec les méthodes exposées dans l’interface utilisateur Swagger et enfin tout nettoyer avec la commande `docker-compose down`.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-156">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="dc2d2-157">Toutefois, la communication à accès direct au microservice, dans le cas présent via le port externe 5101, est précisément ce que vous voulez éviter dans votre application.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-157">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="dc2d2-158">Et vous pouvez l’éviter en définissant le niveau supplémentaire d’indirection de la passerelle d’API (dans ce cas, Ocelot).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-158">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="dc2d2-159">De cette façon, l’application cliente n’accédera pas directement au microservice.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-159">That way, the client app won’t directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="dc2d2-160">Implémentation des passerelles d’API avec Ocelot</span><span class="sxs-lookup"><span data-stu-id="dc2d2-160">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="dc2d2-161">Ocelot est essentiellement un ensemble de middlewares que vous pouvez appliquer dans un ordre spécifique.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-161">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="dc2d2-162">Ocelot est conçu pour fonctionner uniquement avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-162">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="dc2d2-163">Il cible netstandard2.0 et peut donc être utilisé partout où .NET Standard 2.0 est pris en charge, notamment le runtime .NET Core 2.0 et le runtime .NET Framework 4.6.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-163">It targets netstandard2.0 so it can be used anywhere .NET Standard 2.0 is supported, including .NET Core 2.0 runtime and .NET Framework 4.6.1 runtime and up.</span></span>

<span data-ttu-id="dc2d2-164">Installez Ocelot et ses dépendances dans votre projet ASP.NET Core avec le [package NuGet d’Ocelot](https://www.nuget.org/packages/Ocelot/), à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-164">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="dc2d2-165">Dans eShopOnContainers, son implémentation des passerelles d’API est un projet WebHost ASP.NET Core simple et les middlewares d’Ocelot traitent toutes les fonctionnalités des passerelles d’API, comme illustré dans l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="dc2d2-165">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middlewares handle all the API Gateway features, as shown in the following image:</span></span>

![Vue Explorateur de solutions du projet passerelle API Ocelot.](./media/image32.png)

<span data-ttu-id="dc2d2-167">**Figure 6-32.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-167">**Figure 6-32**.</span></span> <span data-ttu-id="dc2d2-168">Projet de base OcelotApiGw dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="dc2d2-168">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="dc2d2-169">Ce projet WebHost ASP.NET Core est essentiellement généré avec deux fichiers simples : `Program.cs` et `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-169">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="dc2d2-170">Le fichier Program.cs doit simplement créer et configurer la fonction BuildWebHost ASP.NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-170">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

<span data-ttu-id="dc2d2-171">Le point important ici pour Ocelot est le fichier `configuration.json` que vous devez fournir au générateur via la méthode `AddJsonFile()`.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-171">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="dc2d2-172">Ce fichier `configuration.json` vous permet de spécifier tous les réacheminements des passerelles d’API, ce qui signifie les points de terminaison externes avec des ports spécifiques et les points de terminaison internes corrélés, généralement à l’aide de ports différents.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-172">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="dc2d2-173">La configuration comprend deux sections.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-173">There are two sections to the configuration.</span></span> <span data-ttu-id="dc2d2-174">Un tableau de réacheminements et une configuration globale.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-174">An array of Re-Routes and a GlobalConfiguration.</span></span> <span data-ttu-id="dc2d2-175">Les réacheminements sont les objets qui indiquent à Ocelot comment traiter une demande en amont.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-175">The Re-Routes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="dc2d2-176">La configuration globale permet le remplacement des paramètres spécifiques aux réacheminements.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-176">The Global configuration allows overrides of Re-Route specific settings.</span></span> <span data-ttu-id="dc2d2-177">Elle est utile si vous ne souhaitez pas gérer un grand nombre de paramètres spécifiques aux réacheminements.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-177">It’s useful if you don’t want to manage lots of Re-Route specific settings.</span></span>

<span data-ttu-id="dc2d2-178">Voici un exemple simplifié de [fichier de configuration des reroutages (ReRoutes)](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) de l’une des passerelles API d’eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-178">Here’s a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

<span data-ttu-id="dc2d2-179">La fonctionnalité principale d’une passerelle d’API Ocelot consiste à prendre les requêtes HTTP entrantes et à les transférer vers un service en aval, actuellement sous la forme d’une autre requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-179">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="dc2d2-180">Ocelot décrit le routage d’une demande vers une autre en tant que réacheminement.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-180">Ocelot’s describes the routing of one request to another as a Re-Route.</span></span>

<span data-ttu-id="dc2d2-181">Par exemple, concentrons-nous sur l’un des réacheminements dans le fichier configuration.json mentionné plus haut, la configuration pour le microservice de panier d’achat (Basket).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-181">For instance, let’s focus on one of the Re-Routes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

<span data-ttu-id="dc2d2-182">Les éléments DownstreamPathTemplate, Scheme et DownstreamHostAndPorts composent l’URL de microservice interne vers laquelle cette demande sera transmise.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-182">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="dc2d2-183">Le port est le port interne utilisé par le service.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-183">The port is the internal port used by the service.</span></span> <span data-ttu-id="dc2d2-184">Lorsque vous utilisez des conteneurs, le port spécifié dans son fichier Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-184">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="dc2d2-185">L’élément `Host` est un nom de service qui dépend de la résolution de noms de service que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-185">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="dc2d2-186">Lors de l’utilisation de docker-compose, les noms des services sont fournis par l’hôte Docker, lequel utilise les noms de service fournis dans les fichiers docker-compose.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-186">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="dc2d2-187">Si vous utilisez un orchestrateur comme Kubernetes ou Service Fabric, ce nom doit être résolu par la résolution de noms ou DNS fournie par chaque orchestrateur.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-187">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="dc2d2-188">DownstreamHostAndPorts est un tableau qui contient l’hôte et le port de tous les services en aval vers lesquels vous souhaitez transférer des demandes.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-188">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="dc2d2-189">Généralement, il contient uniquement une entrée, mais vous pouvez parfois équilibrer la charge des demandes à vos services en aval, et Ocelot vous permet d’ajouter plusieurs entrées puis de sélectionner un équilibreur de charge.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-189">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="dc2d2-190">Toutefois, si vous utilisez Azure et un orchestrateur quelconque, il est probablement plus judicieux d’équilibrer la charge avec l’infrastructure d’orchestrateur et le cloud.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-190">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="dc2d2-191">UpstreamPathTemplate est l’URL dont Ocelot se servira pour identifier l’URL DownstreamPathTemplate à utiliser pour une demande donnée à partir du client.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-191">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="dc2d2-192">Enfin, la méthode UpstreamHttpMethod est utilisée pour qu’Ocelot puisse faire la distinction entre les différentes demandes (GET, POST, PUT) sur la même URL.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-192">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="dc2d2-193">À ce stade, vous pourriez avoir une seule passerelle d’API Ocelot (WebHost ASP.NET Core) utilisant un ou [plusieurs fichiers configuration.json fusionnés](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) ou vous pouvez également stocker la [configuration dans un magasin Consul KV](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-193">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="dc2d2-194">Toutefois, comme indiqué dans la section d’architecture et de conception, si vous voulez vraiment avoir des microservices autonomes, il peut être préférable de diviser cette passerelle d’API monolithique en plusieurs passerelles d’API et/ou BFF (backend for frontend).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-194">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="dc2d2-195">Pour ce faire, voyons comment implémenter cette approche avec des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-195">For that purpose, let’s see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="dc2d2-196">Utilisation d’une image de conteneur Docker individuelle pour exécuter différents types de conteneur de passerelles d’API/BFF</span><span class="sxs-lookup"><span data-stu-id="dc2d2-196">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="dc2d2-197">Dans eShopOnContainers, nous utilisons une seule image conteneur Docker avec la passerelle API Ocelot, mais au moment de l’exécution, nous créons différents conteneurs/services pour chaque type de passerelle API/BFF. Pour cela, nous fournissons un fichier configuration.json différent, en utilisant un volume Docker pour accéder à un dossier de PC différent pour chaque service.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-197">In eShopOnContainers we’re using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Une seule image Docker pour la passerelle API Ocelot est utilisée pour les quatre passerelles API](./media/image33.png)

<span data-ttu-id="dc2d2-199">**Figure 6-33.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-199">**Figure 6-33**.</span></span> <span data-ttu-id="dc2d2-200">Réutilisation d’une image Docker d’Ocelot unique sur plusieurs types de passerelle API</span><span class="sxs-lookup"><span data-stu-id="dc2d2-200">Re-using a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="dc2d2-201">Dans eShopOnContainers, « l’image Docker de passerelle d’API Ocelot générique » est créée avec le projet nommé « OcelotApiGw » et le nom d’image « eshop/ocelotapigw » qui est spécifié dans le fichier docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-201">In eShopOnContainers, the “Generic Ocelot API Gateway Docker Image” is created with the project named 'OcelotApiGw' and the image name “eshop/ocelotapigw” that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="dc2d2-202">Ensuite, lors du déploiement sur Docker, quatre conteneurs de passerelle d’API sont créés à partir de cette même image Docker, comme indiqué dans l’extrait suivant du fichier docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-202">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

<span data-ttu-id="dc2d2-203">De plus, comme vous pouvez le voir dans le fichier docker-compose.override.yml suivant, la seule différence entre ces conteneurs de passerelle API est le fichier de configuration Ocelot, qui est différent pour chaque conteneur de service et qui est spécifié au moment de l’exécution par le biais d’un volume Docker.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-203">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="dc2d2-204">En raison de ce code précédent et comme l’indique l’Explorateur Visual Studio ci-dessous, le seul fichier nécessaire pour définir chaque passerelle d’API d’entreprise/BFF spécifique est un fichier configuration.json, étant donné que les quatre passerelles d’API reposent sur la même image Docker.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-204">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![La seule différence entre toutes les passerelles API est un fichier configuration.json sur chacune d’elle.](./media/image34.png)

<span data-ttu-id="dc2d2-206">**Figure 6-34.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-206">**Figure 6-34**.</span></span> <span data-ttu-id="dc2d2-207">Le seul fichier nécessaire pour définir chaque passerelle d’API / BFF avec Ocelot est un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="dc2d2-207">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="dc2d2-208">En divisant la passerelle d’API en plusieurs passerelles d’API, différentes équipes de développement portant sur différents sous-ensembles de microservices peuvent gérer leurs propres passerelles d’API à l’aide de fichiers de configuration Ocelot indépendants.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-208">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="dc2d2-209">De plus, en même temps, elles peuvent réutiliser la même image Docker d’Ocelot.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-209">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="dc2d2-210">Maintenant, si vous exécutez eShopOnContainers avec les passerelles d’API (incluses par défaut dans Visual Studio lorsque vous ouvrez la solution eShopOnContainers-ServicesAndWebApps.sln ou si vous exécutez « docker-compose up »), les exemples d’itinéraires suivants sont effectués.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-210">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running “docker-compose up”), the following sample routes will be performed.</span></span>

<span data-ttu-id="dc2d2-211">Par exemple, lors de la visite de l’URL en amont `http://localhost:5202/api/v1/c/catalog/items/2/` prise en charge par la passerelle API webshoppingapigw, vous obtenez le même résultat à partir de l’URL interne en aval `http://catalog.api/api/v1/2` dans l’hôte Docker, comme dans le navigateur suivant.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-211">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog.api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![Vue du navigateur d’une réponse de Catalog.api passant par la passerelle API.](./media/image35.png)

<span data-ttu-id="dc2d2-213">**Figure 6-35.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-213">**Figure 6-35**.</span></span> <span data-ttu-id="dc2d2-214">Accès à un microservice via une URL fournie par la passerelle d’API</span><span class="sxs-lookup"><span data-stu-id="dc2d2-214">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="dc2d2-215">En raisons des tests ou du débogage, si vous souhaitez accéder directement au conteneur Docker Catalog (uniquement dans l’environnement de développement) sans passer par la passerelle d’API, dans la mesure où « catalog.api » est une résolution DNS interne à l’hôte Docker (découverte de service gérée par les noms de service docker-compose), la seule façon d’accéder directement au conteneur est via le port externe publié dans le fichier docker-compose.override.yml, qui est fourni uniquement pour les tests de développement, comme `http://localhost:5101/api/v1/Catalog/items/1` dans le navigateur suivant.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-215">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog.api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Vue du navigateur d’une réponse de Catalog.api allant directement vers Catalog.api, identique à celle passant par la passerelle API.](./media/image36.png)

<span data-ttu-id="dc2d2-217">**Figure 6-36.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-217">**Figure 6-36**.</span></span> <span data-ttu-id="dc2d2-218">Accès direct à un microservice à des fins de test</span><span class="sxs-lookup"><span data-stu-id="dc2d2-218">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="dc2d2-219">Toutefois, l’application est configurée pour pouvoir accéder à tous les microservices via les passerelles d’API et non pas via les « raccourcis » des ports directs.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-219">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port “shortcuts”.</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="dc2d2-220">Modèle d’agrégation de passerelle dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="dc2d2-220">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="dc2d2-221">Comme expliqué précédemment, une manière souple d’implémenter l’agrégation des demandes est d’utiliser les services personnalisés, par code.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-221">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="dc2d2-222">Vous pouvez également implémenter l’agrégation des demandes avec la [fonctionnalité d’agrégation des demandes dans Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), mais elle peut ne pas être aussi flexible que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-222">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="dc2d2-223">Par conséquent, la manière sélectionnée pour implémenter l’agrégation dans eShopOnContainers consiste à utiliser un service API web ASP.NET Core explicite pour chaque agrégateur.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-223">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API services for each aggregator.</span></span>

<span data-ttu-id="dc2d2-224">Selon cette approche, le diagramme de composition de passerelle API est en réalité un peu plus étendu quand les services d’agrégation qui ne figurent pas dans le diagramme d’architecture globale simplifiée illustrée précédemment sont pris en compte.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-224">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="dc2d2-225">Dans le diagramme suivant, vous pouvez également voir les services d’agrégation fonctionner avec leurs passerelles d’API associées.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-225">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Architecture d’eShopOnContainers, montrant les services d’agrégation.](./media/image37.png)

<span data-ttu-id="dc2d2-227">**Figure 6-37.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-227">**Figure 6-37**.</span></span> <span data-ttu-id="dc2d2-228">Architecture eShopOnContainers avec services d’agrégation</span><span class="sxs-lookup"><span data-stu-id="dc2d2-228">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="dc2d2-229">En faisant un zoom avant sur le secteur d’activité « Shopping » (Achat) dans l’image suivante, vous pouvez voir que les échanges entre les applications clientes et les microservices sont réduits quand vous utilisez les services d’agrégation dans les passerelles API.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-229">Zooming in further, on the “Shopping” business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![eShopOnContainers architecture zoom in, qui montre les services d’agrégation, qui « assemble » une réponse « joignant » la réponse de plusieurs microservices pour réduire les échanges excessifs avec le client final.](./media/image38.png)

<span data-ttu-id="dc2d2-231">**Figure 6-38.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-231">**Figure 6-38**.</span></span> <span data-ttu-id="dc2d2-232">Vision agrandie des services d’agrégation</span><span class="sxs-lookup"><span data-stu-id="dc2d2-232">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="dc2d2-233">Vous pouvez remarquer que le diagramme peut se compliquer lorsqu’il montre les demandes possibles provenant des passerelles d’API.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-233">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get pretty complex.</span></span> <span data-ttu-id="dc2d2-234">Vous pouvez voir comment les flèches en bleu seraient simplifiées, du point de vue des applications clientes, lors de l’utilisation du modèle d’agrégation en réduisant les échanges et la latence de la communication, et en améliorant finalement considérablement l’expérience utilisateur pour les applications distantes (applications mobiles et SPA), en particulier.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-234">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="dc2d2-235">Dans le cas du secteur d’activité « Marketing » et des microservices, il s’agit d’un cas d’usage très simple, et il n’était pas nécessaire d’utiliser des agrégateurs, bien que cela soit possible, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-235">In the case of the “Marketing” business area and microservices, it is a very simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="dc2d2-236">Authentification et autorisation dans les passerelles d’API Ocelot</span><span class="sxs-lookup"><span data-stu-id="dc2d2-236">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="dc2d2-237">Dans une passerelle d’API Ocelot, vous pouvez placer le service d’authentification, tel qu’un service API web ASP.NET Core avec [IdentityServer](https://identityserver.io/) pour fournir le jeton d’authentification, à l’extérieur ou à l’intérieur de la passerelle d’API.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-237">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="dc2d2-238">Comme eShopOnContainers utilise plusieurs passerelles d’API avec des limites basées sur des secteurs d’activité et BFF, le service d’identité ou d’authentification est tenu à l’écart des passerelles d’API, tel qu’indiqué en jaune dans le diagramme suivant.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-238">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![Diagramme de l’architecture d’eShopOnContainers montrant le microservice Identity sous la passerelle API.](./media/image39.png)

<span data-ttu-id="dc2d2-240">**Figure 6-39.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-240">**Figure 6-39**.</span></span> <span data-ttu-id="dc2d2-241">Position du service d’identité dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="dc2d2-241">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="dc2d2-242">Toutefois, Ocelot prend également en charge le placement du microservice d’identité/d’authentification dans les limites de la passerelle API, comme dans cet autre diagramme.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-242">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![L’authentification avec le microservice Identity sous la passerelle API (AG) : 1) AG demande un jeton d’authentification au microservice d’identité. 2) Le microservice Identity retourne le jeton à AG. 3-4) AG émet des requêtes aux microservices à l’aide du jeton d’authentification.](./media/image40.png)

<span data-ttu-id="dc2d2-244">**Figure 6-40.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-244">**Figure 6-40**.</span></span> <span data-ttu-id="dc2d2-245">Authentification dans Ocelot</span><span class="sxs-lookup"><span data-stu-id="dc2d2-245">Authentication in Ocelot</span></span>

<span data-ttu-id="dc2d2-246">Étant donné que l’application eShopOnContainers a divisé la passerelle d’API en plusieurs passerelles d’API BFF (Backend for Frontend) et de secteurs d’activité, une autre option aurait été de créer une passerelle d’API supplémentaire pour les problèmes transversaux.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would had been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="dc2d2-247">Ce choix serait juste dans une architecture basée sur des microservices plus complexes avec plusieurs microservices de problèmes transversaux.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="dc2d2-248">Comme un seul problème transversal figure dans eShopOnContainers, il a été décidé de gérer simplement le service de sécurité hors du domaine des passerelles d’API, par souci de simplicité.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity’s sake.</span></span>

<span data-ttu-id="dc2d2-249">Dans tous les cas, si l’application est sécurisée au niveau des passerelles d’API, le module d’authentification de la passerelle d’API Ocelot est consulté dans un premier temps lorsque vous tentez d’utiliser un microservice sécurisé quelconque.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="dc2d2-250">Cela redirige la requête HTTP pour consulter le microservice d’identité ou d’authentification afin d’obtenir le jeton d’accès permettant de consulter les services protégés avec le jeton d’accès.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-250">That re-directs the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="dc2d2-251">La manière de sécuriser par authentification n’importe quel service au niveau de la passerelle d’API consiste à définir l’élément AuthenticationProviderKey dans ses paramètres associés, dans le fichier configuration.json.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

<span data-ttu-id="dc2d2-252">Quand Ocelot s’exécute, il examine les réacheminements AuthenticationOptions.AuthenticationProviderKey et vérifie qu’il existe un fournisseur d’authentification enregistré avec la clé donnée.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-252">When Ocelot runs, it will look at the Re-Routes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="dc2d2-253">S’il n’en existe pas, Ocelot ne démarre pas.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="dc2d2-254">S’il en existe, le réacheminement utilise ce fournisseur lorsqu’il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="dc2d2-255">Étant donné que la méthode WebHost d’Ocelot est configurée avec `authenticationProviderKey = "IdentityApiKey"`, elle nécessite une authentification chaque fois que ce service a des demandes quelconques sans jeton d’authentification.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

<span data-ttu-id="dc2d2-256">Ensuite, vous devez également définir une autorisation avec l’attribut [Authorize] sur une ressource quelconque accessible comme les microservices, comme dans le contrôleur de microservice de panier d’achat (Basket) suivant.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

<span data-ttu-id="dc2d2-257">Les éléments ValidAudiences tels que « basket » sont mis en corrélation avec l’audience définie dans chaque microservice avec `AddJwtBearer()` dans la fonction ConfigureServices() de la classe Startup, comme dans le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-257">The ValidAudiences such as “basket” are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

<span data-ttu-id="dc2d2-258">Si vous essayez d’accéder à un microservice sécurisé, par exemple le microservice Basket avec une URL de reroutage basée sur la passerelle API comme `http://localhost:5202/api/v1/b/basket/1`, vous obtenez une erreur 401 Non autorisé, sauf si vous fournissez un jeton valide.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-258">If you try to access any secured microservice, like the Basket microservice with a Re-Route URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you’ll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="dc2d2-259">En revanche, si une URL de réacheminement est authentifiée, Ocelot appelle tout schéma en aval qui lui est associé (URL de microservice interne).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-259">On the other hand, if a Re-Route URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="dc2d2-260">**Autorisation au niveau des reroutages d’Ocelot.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-260">**Authorization at Ocelot’s ReRoutes tier.**</span></span>  <span data-ttu-id="dc2d2-261">Ocelot prend en charge l’autorisation basée sur les revendications évaluée après l’authentification.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="dc2d2-262">Vous définissez l’autorisation au niveau d’une route en ajoutant les lignes suivantes à la configuration des reroutages (ReRoutes).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="dc2d2-263">Dans cet exemple, quand l’intergiciel d’autorisation est appelé, Ocelot détermine si l’utilisateur a le type de revendication « UserType » dans le jeton, et si la valeur de cette revendication est « employee ».</span><span class="sxs-lookup"><span data-stu-id="dc2d2-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="dc2d2-264">Si ce n’est pas le cas, l’utilisateur n’est pas autorisé et la réponse est 403 (Refusé).</span><span class="sxs-lookup"><span data-stu-id="dc2d2-264">If it isn’t, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="dc2d2-265">Utilisation de l’entrée Kubernetes et des passerelles d’API Ocelot</span><span class="sxs-lookup"><span data-stu-id="dc2d2-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="dc2d2-266">Quand vous utilisez Kubernetes (comme dans un cluster Azure Kubernetes Service), vous unifiez généralement toutes les requêtes HTTP à l’aide du [niveau d’entrée Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) basé sur *Nginx*.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="dc2d2-267">Dans Kubernetes, si vous n’utilisez aucune approche d’entrée, vos services et pods ont des adresses IP routables uniquement par le réseau en cluster.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-267">In Kubernetes, if you don’t use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="dc2d2-268">Toutefois, si vous utilisez une approche d’entrée, vous disposez d’un niveau intermédiaire entre Internet et vos services (y compris vos passerelles d’API), agissant comme un proxy inverse.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="dc2d2-269">Par définition, une entrée est une collection de règles qui autorisent les connexions entrantes à atteindre les services de cluster.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="dc2d2-270">Une entrée est généralement configurée pour fournir aux services des URL accessibles en externe, un trafic d’équilibrage de charge, un processus de terminaison SSL, et plus encore.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="dc2d2-271">Les utilisateurs demandent une entrée en publiant la ressource d’entrée sur le serveur d’API.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="dc2d2-272">Dans eShopOnContainers, lorsque vous effectuez un développement local et utilisez simplement votre machine de développement en tant qu’hôte Docker, vous n’utilisez pas d’entrée, mais uniquement les multiples passerelles d’API.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="dc2d2-273">Toutefois, lorsque vous ciblez un environnement de « production » basé sur Kubernetes, eShopOnContainers utilise une entrée en face des passerelles d’API.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-273">However, when targeting a “production” environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="dc2d2-274">De cette façon, les clients appellent toujours la même URL de base, mais les demandes sont acheminées vers plusieurs passerelles d’API ou BFF.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="dc2d2-275">Notez que les passerelles API sont des front-ends ou des façades exposant uniquement les services, mais pas les applications web qui sont généralement hors de leur portée.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-275">Note that API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="dc2d2-276">De plus, les passerelles d’API peuvent masquer certains microservices internes.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="dc2d2-277">Toutefois, l’entrée redirige simplement les requêtes HTTP et n’essaie pas de masquer de microservice ni d’application web.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="dc2d2-278">Le fait d’avoir un niveau Nginx d’entrée dans Kubernetes en face des applications web, ainsi que plusieurs passerelles d’API/BFF Ocelot, constitue l’architecture idéale, telle qu’elle est illustrée dans le diagramme suivant.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Une entrée Kubernetes agit comme un proxy inverse pour tout le trafic vers l’application, notamment les applications web, qui sont généralement en dehors de l’étendue de la passerelle API.](./media/image41.png)

<span data-ttu-id="dc2d2-280">**Figure 6-41.**</span><span class="sxs-lookup"><span data-stu-id="dc2d2-280">**Figure 6-41**.</span></span> <span data-ttu-id="dc2d2-281">Niveau d’entrée dans eShopOnContainers lors d’un déploiement dans Kubernetes</span><span class="sxs-lookup"><span data-stu-id="dc2d2-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="dc2d2-282">Quand vous déployez eShopOnContainers dans Kubernetes, il expose simplement quelques services ou points de terminaison via _l’entrée_, en fait la liste suivante de suffixes sur les URL :</span><span class="sxs-lookup"><span data-stu-id="dc2d2-282">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="dc2d2-283">`/` pour l’application web SPA cliente</span><span class="sxs-lookup"><span data-stu-id="dc2d2-283">`/` for the client SPA web application</span></span>
- <span data-ttu-id="dc2d2-284">`/webmvc` pour l’application web MVC cliente</span><span class="sxs-lookup"><span data-stu-id="dc2d2-284">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="dc2d2-285">`/webstatus` pour l’application web cliente affichant l’état/les vérifications d’intégrité</span><span class="sxs-lookup"><span data-stu-id="dc2d2-285">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="dc2d2-286">`/webshoppingapigw` pour les processus métier d’achat et BFF web</span><span class="sxs-lookup"><span data-stu-id="dc2d2-286">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="dc2d2-287">`/webmarketingapigw` pour les processus métier marketing et BFF web</span><span class="sxs-lookup"><span data-stu-id="dc2d2-287">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="dc2d2-288">`/mobileshoppingapigw` pour les processus métier d’achat et BFF mobiles</span><span class="sxs-lookup"><span data-stu-id="dc2d2-288">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="dc2d2-289">`/mobilemarketingapigw` pour les processus métier marketing et BFF mobiles</span><span class="sxs-lookup"><span data-stu-id="dc2d2-289">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="dc2d2-290">Lorsque vous déployez dans Kubernetes, chaque passerelle d’API Ocelot utilise un fichier « configuration.json » différent pour chaque _pod_ exécutant les passerelles d’API.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-290">When deploying to Kubernetes, each Ocelot API Gateway is using a different “configuration.json” file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="dc2d2-291">Ces fichiers « configuration.json » sont fournis en montant (initialement avec le script deploy.ps1) un volume créé sur la base d’une _carte de configuration_ Kubernetes et nommé « ocelot ».</span><span class="sxs-lookup"><span data-stu-id="dc2d2-291">Those “configuration.json” files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot’.</span></span> <span data-ttu-id="dc2d2-292">Chaque conteneur monte le fichier de configuration qui lui est associé dans le dossier du conteneur nommé `/app/configuration`.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-292">Each container mounts its related configuration file in the container’s folder named `/app/configuration`.</span></span>

<span data-ttu-id="dc2d2-293">Dans les fichiers de code source d’eShopOnContainers, les fichiers « configuration.json » d’origine sont disponibles dans le dossier `k8s/ocelot/`.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-293">In the source code files of eShopOnContainers, the original “configuration.json” files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="dc2d2-294">Il existe un fichier pour chaque passerelle d’API/BFF.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-294">There’s one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="dc2d2-295">Fonctionnalités transversales supplémentaires dans une passerelle d’API Ocelot</span><span class="sxs-lookup"><span data-stu-id="dc2d2-295">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="dc2d2-296">D’autres fonctionnalités importantes peuvent être étudiées et utilisées lorsque vous utilisez une passerelle d’API Ocelot. Elles sont décrites dans les liens suivants.</span><span class="sxs-lookup"><span data-stu-id="dc2d2-296">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="dc2d2-297">**Découverte de services côté client intégrant Ocelot avec Consul ou Eureka** </span><span class="sxs-lookup"><span data-stu-id="dc2d2-297">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="dc2d2-298">**Mise en cache au niveau de la passerelle API** </span><span class="sxs-lookup"><span data-stu-id="dc2d2-298">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="dc2d2-299">**Connexion au niveau de la passerelle API** </span><span class="sxs-lookup"><span data-stu-id="dc2d2-299">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="dc2d2-300">**Qualité de service (nouvelles tentatives et disjoncteurs) au niveau de la passerelle API** </span><span class="sxs-lookup"><span data-stu-id="dc2d2-300">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="dc2d2-301">**Limitation du débit** </span><span class="sxs-lookup"><span data-stu-id="dc2d2-301">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="dc2d2-302">[Précédent](background-tasks-with-ihostedservice.md)
> [Suivant](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="dc2d2-302">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
