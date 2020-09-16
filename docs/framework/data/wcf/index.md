---
title: WCF Data Services 4.5
description: En savoir plus sur WCF Data Services, un composant .NET Framework qui prend en charge les services pour exposer et consommer des données à l’aide de la sémantique REST.
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: c36967236c40efbf432d554c3f551aea22cfb148
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549677"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="a2c96-103">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="a2c96-103">WCF Data Services 4.5</span></span>

<span data-ttu-id="a2c96-104">WCF Data Services (autrefois appelé « ADO.NET Data Services ») est un composant de la .NET Framework qui vous permet de créer des services qui utilisent le Open Data Protocol (OData) pour exposer et consommer des données sur le Web ou l’intranet à l’aide de la sémantique de [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span><span class="sxs-lookup"><span data-stu-id="a2c96-104">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="a2c96-105">OData expose les données sous forme de ressources adressables par des URI.</span><span class="sxs-lookup"><span data-stu-id="a2c96-105">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="a2c96-106">Les données sont accessibles et modifiables à l'aide des verbes HTTP standard GET, PUT, POST et DELETE.</span><span class="sxs-lookup"><span data-stu-id="a2c96-106">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="a2c96-107">OData utilise les conventions de relation d’entité de la [Entity Data Model](../adonet/entity-data-model.md) pour exposer des ressources sous la forme d’ensembles d’entités liés par des associations.</span><span class="sxs-lookup"><span data-stu-id="a2c96-107">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="a2c96-108">WCF Data Services utilise le protocole OData pour l’adressage et la mise à jour des ressources.</span><span class="sxs-lookup"><span data-stu-id="a2c96-108">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="a2c96-109">De cette façon, vous pouvez accéder à ces services à partir de n’importe quel client qui prend en charge OData.</span><span class="sxs-lookup"><span data-stu-id="a2c96-109">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="a2c96-110">OData vous permet de demander et d’écrire des données dans les ressources à l’aide de formats de transfert connus : Atom, un ensemble de normes pour l’échange et la mise à jour de données au format XML, et le format JSON (JavaScript Object Notation), un format d’échange de données textuel utilisé largement dans les applications AJAX.</span><span class="sxs-lookup"><span data-stu-id="a2c96-110">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="a2c96-111">WCF Data Services pouvez exposer des données provenant de différentes sources en tant que flux OData.</span><span class="sxs-lookup"><span data-stu-id="a2c96-111">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="a2c96-112">Les outils Visual Studio facilitent la création d’un service OData à l’aide d’un modèle de données ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a2c96-112">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="a2c96-113">Vous pouvez également créer des flux OData basés sur des classes common language runtime (CLR) et même des données à liaison tardive ou non typées.</span><span class="sxs-lookup"><span data-stu-id="a2c96-113">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="a2c96-114">WCF Data Services comprend également un ensemble de bibliothèques clientes, un pour les applications clientes générales .NET Framework et une autre pour les applications basées sur Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a2c96-114">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="a2c96-115">Ces bibliothèques clientes fournissent un modèle de programmation basé sur des objets lorsque vous accédez à un flux OData depuis des environnements tels que .NET Framework et Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a2c96-115">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="a2c96-116">Où est-ce que je dois démarrer ?</span><span class="sxs-lookup"><span data-stu-id="a2c96-116">Where Should I Start?</span></span>

<span data-ttu-id="a2c96-117">En fonction de vos centres d’intérêt, vous pouvez vous familiariser avec WCF Data Services dans l’une des rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="a2c96-117">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="a2c96-118">Je veux rentrer dans le vif du sujet...</span><span class="sxs-lookup"><span data-stu-id="a2c96-118">I want to jump right in...</span></span>

- [<span data-ttu-id="a2c96-119">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="a2c96-119">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="a2c96-120">Prise en main</span><span class="sxs-lookup"><span data-stu-id="a2c96-120">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="a2c96-121">Montrez-moi un peu de code...</span><span class="sxs-lookup"><span data-stu-id="a2c96-121">Just show me some code...</span></span>

- [<span data-ttu-id="a2c96-122">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="a2c96-122">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="a2c96-123">Procédure : Exécuter les requêtes de services de données</span><span class="sxs-lookup"><span data-stu-id="a2c96-123">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="a2c96-124">Procédure : Lier des données aux éléments Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a2c96-124">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="a2c96-125">Je souhaite en savoir plus sur OData...</span><span class="sxs-lookup"><span data-stu-id="a2c96-125">I want to know more about OData...</span></span>

- [<span data-ttu-id="a2c96-126">Livre blanc : présentation d’OData</span><span class="sxs-lookup"><span data-stu-id="a2c96-126">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="a2c96-127">Site Web Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="a2c96-127">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="a2c96-128">Kit de développement logiciel (SDK) OData</span><span class="sxs-lookup"><span data-stu-id="a2c96-128">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="a2c96-129">Je souhaite voir des exemples de bout en bout...</span><span class="sxs-lookup"><span data-stu-id="a2c96-129">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="a2c96-130">[Démarrage rapide WCF Data Services](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="a2c96-130">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="a2c96-131">OData SDK-exemple de code</span><span class="sxs-lookup"><span data-stu-id="a2c96-131">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="a2c96-132">Qu'en est-il de l'intégration avec Visual Studio ?</span><span class="sxs-lookup"><span data-stu-id="a2c96-132">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="a2c96-133">Génération de la bibliothèque cliente du service de données</span><span class="sxs-lookup"><span data-stu-id="a2c96-133">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="a2c96-134">Création du service de données</span><span class="sxs-lookup"><span data-stu-id="a2c96-134">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="a2c96-135">Fournisseur Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a2c96-135">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="a2c96-136">À quoi sert PIM ?</span><span class="sxs-lookup"><span data-stu-id="a2c96-136">What can I do with it?</span></span>

- [<span data-ttu-id="a2c96-137">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a2c96-137">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="a2c96-138">Scénarios d’application</span><span class="sxs-lookup"><span data-stu-id="a2c96-138">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="a2c96-139">Je souhaite utiliser LINQ...</span><span class="sxs-lookup"><span data-stu-id="a2c96-139">I want to use LINQ...</span></span>

- [<span data-ttu-id="a2c96-140">Interrogation du service de données</span><span class="sxs-lookup"><span data-stu-id="a2c96-140">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="a2c96-141">Considérations sur LINQ</span><span class="sxs-lookup"><span data-stu-id="a2c96-141">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="a2c96-142">Procédure : Exécuter les requêtes de services de données</span><span class="sxs-lookup"><span data-stu-id="a2c96-142">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="a2c96-143">J’ai encore besoin d’informations supplémentaires...</span><span class="sxs-lookup"><span data-stu-id="a2c96-143">I still need some more information...</span></span>

- [<span data-ttu-id="a2c96-144">Blog de l’équipe WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a2c96-144">WCF Data Services Team Blog</span></span>](/archive/blogs/astoriateam/)

- [<span data-ttu-id="a2c96-145">Ressources</span><span class="sxs-lookup"><span data-stu-id="a2c96-145">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="a2c96-146">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a2c96-146">In This Section</span></span>

[<span data-ttu-id="a2c96-147">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a2c96-147">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="a2c96-148">Fournit une vue d’ensemble des fonctionnalités et fonctionnalités disponibles dans WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="a2c96-148">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="a2c96-149">[Nouveautés de WCF Data Services 5,0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="a2c96-149">[What's New in WCF Data Services 5.0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="a2c96-150">Décrit les nouvelles fonctionnalités de WCF Data Services et la prise en charge des nouvelles fonctionnalités OData.</span><span class="sxs-lookup"><span data-stu-id="a2c96-150">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="a2c96-151">Prise en main</span><span class="sxs-lookup"><span data-stu-id="a2c96-151">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="a2c96-152">Décrit comment exposer et consommer des flux OData à l’aide de WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="a2c96-152">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="a2c96-153">Définition des services de données WCF</span><span class="sxs-lookup"><span data-stu-id="a2c96-153">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="a2c96-154">Décrit comment créer et configurer un service de données qui expose des flux OData.</span><span class="sxs-lookup"><span data-stu-id="a2c96-154">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="a2c96-155">Bibliothèque client services de données WCF</span><span class="sxs-lookup"><span data-stu-id="a2c96-155">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="a2c96-156">Décrit comment utiliser des bibliothèques clientes pour consommer des flux OData à partir d’une application cliente .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2c96-156">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2c96-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2c96-157">See also</span></span>

- [<span data-ttu-id="a2c96-158">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="a2c96-158">Representational State Transfer (REST)</span></span>](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
