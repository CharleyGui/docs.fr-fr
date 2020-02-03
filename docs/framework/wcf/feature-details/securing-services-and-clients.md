---
title: Sécurisation des services et des clients
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746418"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="fae49-102">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="fae49-102">Securing Services and Clients</span></span>
<span data-ttu-id="fae49-103">Les informations contenues dans cette section se concentrent sur la programmation de la sécurité dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fae49-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="fae49-104">En général, l’opération inclut la sélection d’une liaison appropriée fournie par le système, la définition des propriétés de l’élément de sécurité, puis la définition des propriétés des comportements du service qui déterminent la manière dont les informations d’identification sont récupérées pour être utilisées par le service ou le client.</span><span class="sxs-lookup"><span data-stu-id="fae49-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="fae49-105">Ces techniques couvrent les exigences de sécurité de la plupart des utilisateurs pour la plupart des scénarios, comme indiqué dans les [scénarios de sécurité courants](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="fae49-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="fae49-106">Si votre scénario nécessite plus de fonctionnalités, commencez [par consulter les fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md). Si une solution n’est pas visible, consultez extension de la [sécurité](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="fae49-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="fae49-107">Si vous créez (ou interopèrez avec) un système qui utilise des revendications enrichies, consultez les rubriques dans [autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="fae49-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fae49-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fae49-108">In This Section</span></span>  
 [<span data-ttu-id="fae49-109">Programmation de la sécurité dans WCF</span><span class="sxs-lookup"><span data-stu-id="fae49-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="fae49-110">Vue d'ensemble du modèle de programmation utilisé pour sécuriser des messages.</span><span class="sxs-lookup"><span data-stu-id="fae49-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="fae49-111">Vue d’ensemble de la sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="fae49-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="fae49-112">Vue d'ensemble de la sécurisation des messages par le biais de la couche transport.</span><span class="sxs-lookup"><span data-stu-id="fae49-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="fae49-113">Sécurité de message</span><span class="sxs-lookup"><span data-stu-id="fae49-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="fae49-114">Résume les raisons de l’utilisation de la sécurité au niveau du message dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fae49-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="fae49-115">Sessions sécurisées</span><span class="sxs-lookup"><span data-stu-id="fae49-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="fae49-116">Discussion des points à prendre en compte lors de la sécurisation d’une session WCF.</span><span class="sxs-lookup"><span data-stu-id="fae49-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="fae49-117">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="fae49-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="fae49-118">Explication de quelques-unes des tâches courantes requises lors de l’utilisation de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="fae49-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fae49-119">Référence</span><span class="sxs-lookup"><span data-stu-id="fae49-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="fae49-120">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="fae49-120">Related Sections</span></span>  
 [<span data-ttu-id="fae49-121">Concepts relatifs à la sécurité</span><span class="sxs-lookup"><span data-stu-id="fae49-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="fae49-122">Extension de la sécurité</span><span class="sxs-lookup"><span data-stu-id="fae49-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="fae49-123">Scénarios de sécurité courants</span><span class="sxs-lookup"><span data-stu-id="fae49-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="fae49-124">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="fae49-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="fae49-125">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="fae49-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="fae49-126">Extension de la sécurité</span><span class="sxs-lookup"><span data-stu-id="fae49-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="fae49-127">Autorisation</span><span class="sxs-lookup"><span data-stu-id="fae49-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="fae49-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fae49-128">See also</span></span>

- [<span data-ttu-id="fae49-129">Programmation WCF de base</span><span class="sxs-lookup"><span data-stu-id="fae49-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
- <span data-ttu-id="fae49-130">[Modèle de sécurité pour Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fae49-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
