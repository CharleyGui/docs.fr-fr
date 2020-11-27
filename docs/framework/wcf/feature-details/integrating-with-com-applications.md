---
title: Intégration à des applications COM
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: bc58e22b64284d66367302d55b5c9554c9ec0d72
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268233"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="85187-102">Intégration à des applications COM</span><span class="sxs-lookup"><span data-stu-id="85187-102">Integrating with COM Applications</span></span>

<span data-ttu-id="85187-103">Les services Windows Communication Foundation (WCF) peuvent être intégrés directement dans votre code existant à l’aide du moniker de service WCF.</span><span class="sxs-lookup"><span data-stu-id="85187-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="85187-104">Le moniker de service peut être utilisé à partir d'une large gamme d'environnements de développement COM, tels qu'Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="85187-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85187-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="85187-105">In This Section</span></span>  

 [<span data-ttu-id="85187-106">Vue d'ensemble de l'intégration à des applications COM</span><span class="sxs-lookup"><span data-stu-id="85187-106">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)  
 <span data-ttu-id="85187-107">Fournit une vue d'ensemble des principales phases du processus d'intégration.</span><span class="sxs-lookup"><span data-stu-id="85187-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="85187-108">Procédure : inscrire et configurer un moniker de service</span><span class="sxs-lookup"><span data-stu-id="85187-108">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="85187-109">Pour utiliser le moniker de service WCF dans une application COM, inscrivez les types attribués requis avec COM et configurez l’application COM et le moniker avec la configuration de liaison requise.</span><span class="sxs-lookup"><span data-stu-id="85187-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="85187-110">Procédure : utiliser le moniker de service Windows Communication Foundation sans inscription</span><span class="sxs-lookup"><span data-stu-id="85187-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="85187-111">Explique comment obtenir la définition du contrat sous la forme d'un document WSDL (Web Services Definition Language) ou à partir d'un point de terminaison WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="85187-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="85187-112">Procédure : utiliser un moniker de service avec des contrats WSDL</span><span class="sxs-lookup"><span data-stu-id="85187-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="85187-113">Décrit comment appeler un exemple WCF à l’aide d’un moniker WSDL WCF.</span><span class="sxs-lookup"><span data-stu-id="85187-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="85187-114">Procédure : utiliser un moniker de service avec des contrats d’échange de métadonnées</span><span class="sxs-lookup"><span data-stu-id="85187-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="85187-115">Décrit comment appeler un exemple WCF à l’aide d’un moniker WCF qui spécifie un point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="85187-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="85187-116">Procédure : spécifier des informations d’identification de sécurité de canal</span><span class="sxs-lookup"><span data-stu-id="85187-116">How to: Specify Channel Security Credentials</span></span>](how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="85187-117">Le moniker de service WCF prend en charge l' `IChannelCredentials` interface qui autorise une plage de méthodes alternatives pour spécifier les informations d’identification de canal.</span><span class="sxs-lookup"><span data-stu-id="85187-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="85187-118">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="85187-118">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="85187-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85187-119">See also</span></span>

- [<span data-ttu-id="85187-120">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="85187-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
