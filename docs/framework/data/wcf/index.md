---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 1ce152b84f17a35982a75f54b5418623ba39210f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975231"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="9aaa5-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="9aaa5-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="9aaa5-103">WCF Data Services (autrefois appelé « ADO.NET Data Services ») est un composant de la .NET Framework qui vous permet de créer des services qui utilisent le Open Data Protocol (OData) pour exposer et consommer des données sur le Web ou l’intranet à l’aide de la sémantique de [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="9aaa5-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="9aaa5-104">OData expose les données sous forme de ressources adressables par des URI.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="9aaa5-105">Les données sont accessibles et modifiables à l'aide des verbes HTTP standard GET, PUT, POST et DELETE.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="9aaa5-106">OData utilise les conventions de relation d’entité de la [Entity Data Model](../adonet/entity-data-model.md) pour exposer des ressources sous la forme d’ensembles d’entités liés par des associations.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="9aaa5-107">WCF Data Services utilise le protocole OData pour l’adressage et la mise à jour des ressources.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="9aaa5-108">De cette façon, vous pouvez accéder à ces services à partir de n’importe quel client qui prend en charge OData.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="9aaa5-109">OData vous permet de demander et d’écrire des données dans les ressources à l’aide de formats de transfert connus : Atom, un ensemble de normes pour l’échange et la mise à jour de données au format XML, et le format JSON (JavaScript Object Notation), un format d’échange de données textuel utilisé largement dans AJAX applications.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="9aaa5-110">WCF Data Services pouvez exposer des données provenant de différentes sources en tant que flux OData.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="9aaa5-111">Les outils Visual Studio facilitent la création d’un service OData à l’aide d’un modèle de données ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="9aaa5-112">Vous pouvez également créer des flux OData basés sur des classes common language runtime (CLR) et même des données à liaison tardive ou non typées.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="9aaa5-113">WCF Data Services comprend également un ensemble de bibliothèques clientes, un pour les applications clientes générales .NET Framework et une autre pour les applications basées sur Silverlight.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="9aaa5-114">Ces bibliothèques clientes fournissent un modèle de programmation basé sur les objets lorsque vous accédez à un flux OData à partir d’environnements tels que les .NET Framework et Silverlight.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="9aaa5-115">Où est-ce que je dois démarrer ?</span><span class="sxs-lookup"><span data-stu-id="9aaa5-115">Where Should I Start?</span></span>

<span data-ttu-id="9aaa5-116">En fonction de vos centres d’intérêt, vous pouvez vous familiariser avec WCF Data Services dans l’une des rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="9aaa5-117">Je veux rentrer dans le vif du sujet...</span><span class="sxs-lookup"><span data-stu-id="9aaa5-117">I want to jump right in...</span></span>

- [<span data-ttu-id="9aaa5-118">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="9aaa5-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="9aaa5-119">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="9aaa5-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

- [<span data-ttu-id="9aaa5-120">Démarrage rapide avec Silverlight</span><span class="sxs-lookup"><span data-stu-id="9aaa5-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="9aaa5-121">Démarrage rapide avec Silverlight pour le développement de Windows Phone</span><span class="sxs-lookup"><span data-stu-id="9aaa5-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="9aaa5-122">Montrez-moi un peu de code...</span><span class="sxs-lookup"><span data-stu-id="9aaa5-122">Just show me some code...</span></span>

- [<span data-ttu-id="9aaa5-123">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="9aaa5-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="9aaa5-124">Comment : exécuter les requêtes de services de données</span><span class="sxs-lookup"><span data-stu-id="9aaa5-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="9aaa5-125">Comment : lier les données aux éléments Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="9aaa5-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="9aaa5-126">Je souhaite en savoir plus sur OData...</span><span class="sxs-lookup"><span data-stu-id="9aaa5-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="9aaa5-127">Livre blanc : présentation d’OData</span><span class="sxs-lookup"><span data-stu-id="9aaa5-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="9aaa5-128">Site web Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="9aaa5-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

- [<span data-ttu-id="9aaa5-129">Kit de développement logiciel (SDK) OData</span><span class="sxs-lookup"><span data-stu-id="9aaa5-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

- [<span data-ttu-id="9aaa5-130">OData : forum aux questions</span><span class="sxs-lookup"><span data-stu-id="9aaa5-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="9aaa5-131">Je souhaite regarder des vidéos...</span><span class="sxs-lookup"><span data-stu-id="9aaa5-131">I want to watch some videos...</span></span>

- [<span data-ttu-id="9aaa5-132">Guide du débutant sur WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="9aaa5-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

- [<span data-ttu-id="9aaa5-133">Vidéos du développeur WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="9aaa5-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

- [<span data-ttu-id="9aaa5-134">OData : site web développeurs</span><span class="sxs-lookup"><span data-stu-id="9aaa5-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="9aaa5-135">Je souhaite voir des exemples de bout en bout...</span><span class="sxs-lookup"><span data-stu-id="9aaa5-135">I want to see end-to-end samples...</span></span>

- [<span data-ttu-id="9aaa5-136">Exemples de documentation WCF Data Services dans la galerie d’exemples MSDN</span><span class="sxs-lookup"><span data-stu-id="9aaa5-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

- [<span data-ttu-id="9aaa5-137">Autres exemples WCF Data Services dans la galerie d’exemples MSDN</span><span class="sxs-lookup"><span data-stu-id="9aaa5-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

- [<span data-ttu-id="9aaa5-138">Kit de développement logiciel (SDK) OData</span><span class="sxs-lookup"><span data-stu-id="9aaa5-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="9aaa5-139">Qu'en est-il de l'intégration avec Visual Studio ?</span><span class="sxs-lookup"><span data-stu-id="9aaa5-139">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="9aaa5-140">Génération de la bibliothèque cliente du service de données</span><span class="sxs-lookup"><span data-stu-id="9aaa5-140">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="9aaa5-141">Création du service de données</span><span class="sxs-lookup"><span data-stu-id="9aaa5-141">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="9aaa5-142">Fournisseur Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9aaa5-142">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="9aaa5-143">Comment puis-je l'utiliser ?</span><span class="sxs-lookup"><span data-stu-id="9aaa5-143">What can I do with it?</span></span>

- [<span data-ttu-id="9aaa5-144">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="9aaa5-144">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="9aaa5-145">Livre blanc : présentation d’OData</span><span class="sxs-lookup"><span data-stu-id="9aaa5-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="9aaa5-146">Scénarios d’application</span><span class="sxs-lookup"><span data-stu-id="9aaa5-146">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="9aaa5-147">Je souhaite utiliser Silverlight...</span><span class="sxs-lookup"><span data-stu-id="9aaa5-147">I want to use Silverlight...</span></span>

- [<span data-ttu-id="9aaa5-148">Démarrage rapide avec Silverlight</span><span class="sxs-lookup"><span data-stu-id="9aaa5-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="9aaa5-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="9aaa5-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

- [<span data-ttu-id="9aaa5-150">Prise en main de Silverlight</span><span class="sxs-lookup"><span data-stu-id="9aaa5-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="9aaa5-151">Je souhaite utiliser LINQ...</span><span class="sxs-lookup"><span data-stu-id="9aaa5-151">I want to use LINQ...</span></span>

- [<span data-ttu-id="9aaa5-152">Interrogation du service de données</span><span class="sxs-lookup"><span data-stu-id="9aaa5-152">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="9aaa5-153">Considérations sur LINQ</span><span class="sxs-lookup"><span data-stu-id="9aaa5-153">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="9aaa5-154">Comment : exécuter les requêtes de services de données</span><span class="sxs-lookup"><span data-stu-id="9aaa5-154">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="9aaa5-155">J’ai encore besoin d’informations supplémentaires...</span><span class="sxs-lookup"><span data-stu-id="9aaa5-155">I still need some more information...</span></span>

- [<span data-ttu-id="9aaa5-156">Blog de l’équipe WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="9aaa5-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

- [<span data-ttu-id="9aaa5-157">Ressources</span><span class="sxs-lookup"><span data-stu-id="9aaa5-157">Resources</span></span>](wcf-data-services-resources.md)

- [<span data-ttu-id="9aaa5-158">Centre de développement WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="9aaa5-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

- [<span data-ttu-id="9aaa5-159">Site web Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="9aaa5-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="9aaa5-160">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9aaa5-160">In This Section</span></span>

[<span data-ttu-id="9aaa5-161">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="9aaa5-161">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="9aaa5-162">Fournit une vue d’ensemble des fonctionnalités et fonctionnalités disponibles dans WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="9aaa5-163">[Nouveautés de WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="9aaa5-163">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="9aaa5-164">Décrit les nouvelles fonctionnalités de WCF Data Services et la prise en charge des nouvelles fonctionnalités OData.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="9aaa5-165">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="9aaa5-165">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="9aaa5-166">Décrit comment exposer et consommer des flux OData à l’aide de WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="9aaa5-167">Définition de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="9aaa5-167">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="9aaa5-168">Décrit comment créer et configurer un service de données qui expose des flux OData.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="9aaa5-169">Bibliothèque cliente WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="9aaa5-169">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="9aaa5-170">Décrit comment utiliser des bibliothèques clientes pour consommer des flux OData à partir d’une application cliente .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9aaa5-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="9aaa5-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9aaa5-171">See also</span></span>

- [<span data-ttu-id="9aaa5-172">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="9aaa5-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
