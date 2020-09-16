---
title: Intégration d'AJAX et prise en charge de JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: f1748372af520955c139dffb2e6e80ae066c9397
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536061"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="78abe-102">Intégration d'AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="78abe-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="78abe-103">La prise en charge de Windows Communication Foundation (WCF) pour les formats de données AJAX (Asynchronous JavaScript and XML) et JavaScript Object Notation (JSON) de ASP.NET permet aux services WCF d’exposer des opérations aux clients AJAX.</span><span class="sxs-lookup"><span data-stu-id="78abe-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="78abe-104">Les clients AJAX sont des pages Web qui exécutent du code JavaScript et accèdent à ces services WCF à l’aide de requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="78abe-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="78abe-105">Les rubriques de cette section fournissent des informations sur cette prise en charge et sur la manière de l'implémenter.</span><span class="sxs-lookup"><span data-stu-id="78abe-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="78abe-106">Pour plus d’informations sur ASP.NET AJAX et son intégration à ASP.NET 2,0, consultez [vue d’ensemble d’ASP.NET AJAX](/previous-versions/aspnet/bb398874(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="78abe-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78abe-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="78abe-107">In This Section</span></span>  
 [<span data-ttu-id="78abe-108">Création de services WCF pour ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="78abe-108">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="78abe-109">Décrit comment un service WCF peut être exposé aux clients AJAX en ajoutant le point de terminaison AJAX approprié par le biais de la configuration ou à l’aide d’une fabrique d’hôte de service personnalisée pour générer un hôte de service qui configure automatiquement le point de terminaison AJAX.</span><span class="sxs-lookup"><span data-stu-id="78abe-109">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="78abe-110">Création de services AJAX WCF sans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78abe-110">Creating WCF AJAX Services without ASP.NET</span></span>](creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="78abe-111">Décrit comment créer un service WCF sans utiliser ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="78abe-111">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="78abe-112">Prise en charge du format JSON et d'autres formats de transfert de données</span><span class="sxs-lookup"><span data-stu-id="78abe-112">Support for JSON and Other Data Transfer Formats</span></span>](support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="78abe-113">Décrit la prise en charge du format JSON utilisé en général (à la place de XML) pour la messagerie avec les services ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="78abe-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="78abe-114">Procédure : migrer des services web ASP.NET compatibles AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="78abe-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="78abe-115">Décrit comment migrer un service Web ASP.NET compatible AJAX vers un service Web WCF.</span><span class="sxs-lookup"><span data-stu-id="78abe-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78abe-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78abe-116">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="78abe-117">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="78abe-117">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
