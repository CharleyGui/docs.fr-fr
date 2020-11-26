---
title: Modèle de programmation HTTP Web WCF
ms.date: 03/30/2017
helpviewer_keywords:
- web services programming model [WCF]
- POX
- REST
ms.assetid: 2312a8d3-b66e-4623-ba42-978434300c7f
ms.openlocfilehash: 644bcba9f8ced965ff962962bd83e1ae170159a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239001"
---
# <a name="wcf-web-http-programming-model"></a><span data-ttu-id="b7297-102">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="b7297-102">WCF Web HTTP Programming Model</span></span>

<span data-ttu-id="b7297-103">Le modèle de programmation HTTP Web Windows Communication Foundation (WCF) permet aux développeurs d’exposer des opérations de service WCF à des points de terminaison non-SOAP.</span><span class="sxs-lookup"><span data-stu-id="b7297-103">The Windows Communication Foundation (WCF) Web HTTP Programming Model allows developers to expose WCF service operations to non-SOAP endpoints.</span></span> <span data-ttu-id="b7297-104">Cette fonctionnalité est décrite en détail dans les rubriques de cette section.</span><span class="sxs-lookup"><span data-stu-id="b7297-104">The topics in this section examine the feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7297-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b7297-105">In This Section</span></span>  

 [<span data-ttu-id="b7297-106">Vue d'ensemble du modèle de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="b7297-106">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)  
 <span data-ttu-id="b7297-107">Fournit une vue d’ensemble du modèle de programmation HTTP Web Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b7297-107">Provides an overview of the Windows Communication Foundation (WCF) Web HTTP Programming Model.</span></span>  
  
 [<span data-ttu-id="b7297-108">Modèle objet de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="b7297-108">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)  
 <span data-ttu-id="b7297-109">Décrit le modèle de programmation HTTP Web Windows Communication Foundation (WCF) et son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="b7297-109">Discusses the Windows Communication Foundation (WCF) Web HTTP Programming Model and how it works.</span></span>  
  
 [<span data-ttu-id="b7297-110">Procédure : créer un service HTTP web WCF de base</span><span class="sxs-lookup"><span data-stu-id="b7297-110">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)  
 <span data-ttu-id="b7297-111">Décrit comment écrire un service de base qui expose un point de terminaison non-SOAP.</span><span class="sxs-lookup"><span data-stu-id="b7297-111">Describes how to write a basic service that exposes a non-SOAP endpoint.</span></span>  
  
 [<span data-ttu-id="b7297-112">Procédure : exposer un contrat à des clients SOAP et web</span><span class="sxs-lookup"><span data-stu-id="b7297-112">How to: Expose a Contract to SOAP and Web Clients</span></span>](how-to-expose-a-contract-to-soap-and-web-clients.md)  
 <span data-ttu-id="b7297-113">Décrit comment écrire un service de base qui expose le même contrat aux clients SOAP et non-SOAP.</span><span class="sxs-lookup"><span data-stu-id="b7297-113">Describes how to write a basic service that exposes the same contract to both SOAP and non-SOAP clients.</span></span>  
  
 [<span data-ttu-id="b7297-114">UriTemplate et UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="b7297-114">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)  
 <span data-ttu-id="b7297-115">Décrit comment contrôler les URI à l'aide de <xref:System.UriTemplate> et <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="b7297-115">Describes how to control URIs using <xref:System.UriTemplate> and <xref:System.UriTemplateTable>.</span></span>  
  
 [<span data-ttu-id="b7297-116">Prise en charge de la mise en cache pour les services HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="b7297-116">Caching Support for WCF Web HTTP Services</span></span>](caching-support-for-wcf-web-http-services.md)  
 <span data-ttu-id="b7297-117">Décrit comment spécifier un comportement de mise en cache pour un service HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="b7297-117">Describes how to specify caching behavior for a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="b7297-118">Mise en forme HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="b7297-118">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)  
 <span data-ttu-id="b7297-119">Décrit comment spécifier le format de la réponse à partir d'un service HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="b7297-119">Describes how to specify the format of the response from a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="b7297-120">Gestion des erreurs HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="b7297-120">WCF Web HTTP Error Handling</span></span>](wcf-web-http-error-handling.md)  
 <span data-ttu-id="b7297-121">Décrit comment retourner des erreurs aux clients Web WCF, notamment les codes d'état HTTP et des données d'erreur supplémentaires définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7297-121">Describes how to return errors to WCF Web clients including HTTP status codes and additional user-defined error data.</span></span>  
  
 [<span data-ttu-id="b7297-122">Appel d'un service REST à partir d'un service WCF</span><span class="sxs-lookup"><span data-stu-id="b7297-122">Calling a REST-style service from a WCF service</span></span>](calling-a-rest-style-service-from-a-wcf-service.md)  
 <span data-ttu-id="b7297-123">Décrit comment appeler un service REST à partir d'un service WCF.</span><span class="sxs-lookup"><span data-stu-id="b7297-123">Describes how to call a REST-style service from inside a WCF service.</span></span>
