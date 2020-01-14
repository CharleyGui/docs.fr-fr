---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: aace683b1a105445b5a3ba3de0a6a671859588b5
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937442"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="08a5e-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="08a5e-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="08a5e-103">WCF Data Services (autrefois appelé « ADO.NET Data Services ») est un composant de la .NET Framework qui vous permet de créer des services qui utilisent le Open Data Protocol (OData) pour exposer et consommer des données sur le Web ou l’intranet à l’aide de la sémantique de [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span><span class="sxs-lookup"><span data-stu-id="08a5e-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="08a5e-104">OData expose des données en tant que ressources qui sont adressables à l'aide d'URI.</span><span class="sxs-lookup"><span data-stu-id="08a5e-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="08a5e-105">Les données sont accessibles et modifiées en utilisant des mots HTTP standard (GET, PUT, POST et DELETE).</span><span class="sxs-lookup"><span data-stu-id="08a5e-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="08a5e-106">OData utilise les conventions de relation d’entité de la [Entity Data Model](../adonet/entity-data-model.md) pour exposer des ressources sous la forme d’ensembles d’entités liés par des associations.</span><span class="sxs-lookup"><span data-stu-id="08a5e-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="08a5e-107">WCF Data Services utilise le protocole OData pour l’adressage et la mise à jour des ressources.</span><span class="sxs-lookup"><span data-stu-id="08a5e-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="08a5e-108">De cette façon, vous pouvez accéder à ces services à partir de n’importe quel client qui prend en charge OData.</span><span class="sxs-lookup"><span data-stu-id="08a5e-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="08a5e-109">OData vous permet de demander et d’écrire des données dans les ressources à l’aide de formats de transfert connus : Atom, un ensemble de normes pour l’échange et la mise à jour de données au format XML, et le format JSON (JavaScript Object Notation), un format d’échange de données textuel utilisé largement dans AJAX applications.</span><span class="sxs-lookup"><span data-stu-id="08a5e-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="08a5e-110">WCF Data Services pouvez exposer des données provenant de différentes sources en tant que flux OData.</span><span class="sxs-lookup"><span data-stu-id="08a5e-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="08a5e-111">Les outils Visual Studio facilitent la création d’un service OData à l’aide d’un modèle de données ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="08a5e-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="08a5e-112">Vous pouvez également créer des flux OData basés sur des classes common language runtime (CLR) et même des données à liaison tardive ou non typées.</span><span class="sxs-lookup"><span data-stu-id="08a5e-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="08a5e-113">WCF Data Services comprend également un ensemble de bibliothèques clientes, un pour les applications clientes générales .NET Framework et une autre pour les applications basées sur Silverlight.</span><span class="sxs-lookup"><span data-stu-id="08a5e-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="08a5e-114">Ces bibliothèques clientes fournissent un modèle de programmation basé sur les objets lorsque vous accédez à un flux OData à partir d’environnements tels que les .NET Framework et Silverlight.</span><span class="sxs-lookup"><span data-stu-id="08a5e-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="08a5e-115">Où est-ce que je dois démarrer ?</span><span class="sxs-lookup"><span data-stu-id="08a5e-115">Where Should I Start?</span></span>

<span data-ttu-id="08a5e-116">En fonction de vos centres d’intérêt, vous pouvez vous familiariser avec WCF Data Services dans l’une des rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="08a5e-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="08a5e-117">Je veux rentrer dans le vif du sujet...</span><span class="sxs-lookup"><span data-stu-id="08a5e-117">I want to jump right in...</span></span>

- [<span data-ttu-id="08a5e-118">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="08a5e-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="08a5e-119">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="08a5e-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="08a5e-120">Montrez-moi un peu de code...</span><span class="sxs-lookup"><span data-stu-id="08a5e-120">Just show me some code...</span></span>

- [<span data-ttu-id="08a5e-121">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="08a5e-121">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="08a5e-122">Comment : exécuter les requêtes de services de données</span><span class="sxs-lookup"><span data-stu-id="08a5e-122">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="08a5e-123">Comment : lier les données aux éléments Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="08a5e-123">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="08a5e-124">Je souhaite en savoir plus sur OData...</span><span class="sxs-lookup"><span data-stu-id="08a5e-124">I want to know more about OData...</span></span>

- [<span data-ttu-id="08a5e-125">Livre blanc : présentation d’OData</span><span class="sxs-lookup"><span data-stu-id="08a5e-125">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="08a5e-126">Site Web Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="08a5e-126">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="08a5e-127">Kit de développement logiciel (SDK) OData</span><span class="sxs-lookup"><span data-stu-id="08a5e-127">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="08a5e-128">Je souhaite voir des exemples de bout en bout...</span><span class="sxs-lookup"><span data-stu-id="08a5e-128">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="08a5e-129">[Démarrage rapide WCF Data Services](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="08a5e-129">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="08a5e-130">OData SDK-exemple de code</span><span class="sxs-lookup"><span data-stu-id="08a5e-130">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="08a5e-131">Qu'en est-il de l'intégration avec Visual Studio ?</span><span class="sxs-lookup"><span data-stu-id="08a5e-131">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="08a5e-132">Génération de la bibliothèque cliente du service de données</span><span class="sxs-lookup"><span data-stu-id="08a5e-132">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="08a5e-133">Création du service de données</span><span class="sxs-lookup"><span data-stu-id="08a5e-133">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="08a5e-134">Fournisseur Entity Framework</span><span class="sxs-lookup"><span data-stu-id="08a5e-134">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="08a5e-135">Comment puis-je l'utiliser ?</span><span class="sxs-lookup"><span data-stu-id="08a5e-135">What can I do with it?</span></span>

- [<span data-ttu-id="08a5e-136">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="08a5e-136">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="08a5e-137">Scénarios d’application</span><span class="sxs-lookup"><span data-stu-id="08a5e-137">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="08a5e-138">Je souhaite utiliser LINQ...</span><span class="sxs-lookup"><span data-stu-id="08a5e-138">I want to use LINQ...</span></span>

- [<span data-ttu-id="08a5e-139">Interrogation du service de données</span><span class="sxs-lookup"><span data-stu-id="08a5e-139">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="08a5e-140">Considérations sur LINQ</span><span class="sxs-lookup"><span data-stu-id="08a5e-140">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="08a5e-141">Comment : exécuter les requêtes de services de données</span><span class="sxs-lookup"><span data-stu-id="08a5e-141">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="08a5e-142">J’ai encore besoin d’informations supplémentaires...</span><span class="sxs-lookup"><span data-stu-id="08a5e-142">I still need some more information...</span></span>

- [<span data-ttu-id="08a5e-143">Blog de l’équipe WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="08a5e-143">WCF Data Services Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [<span data-ttu-id="08a5e-144">Ressources</span><span class="sxs-lookup"><span data-stu-id="08a5e-144">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="08a5e-145">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="08a5e-145">In This Section</span></span>

[<span data-ttu-id="08a5e-146">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="08a5e-146">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="08a5e-147">Fournit une vue d’ensemble des fonctionnalités et fonctionnalités disponibles dans WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="08a5e-147">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="08a5e-148">[Nouveautés de WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="08a5e-148">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="08a5e-149">Décrit les nouvelles fonctionnalités de WCF Data Services et la prise en charge des nouvelles fonctionnalités OData.</span><span class="sxs-lookup"><span data-stu-id="08a5e-149">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="08a5e-150">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="08a5e-150">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="08a5e-151">Décrit comment exposer et consommer des flux OData à l’aide de WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="08a5e-151">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="08a5e-152">Définition de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="08a5e-152">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="08a5e-153">Décrit comment créer et configurer un service de données qui expose des flux OData.</span><span class="sxs-lookup"><span data-stu-id="08a5e-153">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="08a5e-154">Bibliothèque cliente WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="08a5e-154">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="08a5e-155">Décrit comment utiliser des bibliothèques clientes pour consommer des flux OData à partir d’une application cliente .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08a5e-155">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="08a5e-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08a5e-156">See also</span></span>

- [<span data-ttu-id="08a5e-157">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="08a5e-157">Representational State Transfer (REST)</span></span>](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
