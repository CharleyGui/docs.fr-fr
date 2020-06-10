---
title: Sécurité dans Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 327fb509a5186a0b3f428efc2ddd7f983bcfa978
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595140"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="1bacd-102">Sécurité dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1bacd-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="1bacd-103">Les rubriques de cette section décrivent les fonctionnalités de sécurité de Windows Communication Foundation (WCF) et expliquent comment les utiliser pour aider à sécuriser les messages.</span><span class="sxs-lookup"><span data-stu-id="1bacd-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="1bacd-104">Pour plus d’informations sur Windows Server AppFabric et la sécurité, consultez [modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10)) .</span><span class="sxs-lookup"><span data-stu-id="1bacd-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1bacd-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1bacd-105">In This Section</span></span>  
 [<span data-ttu-id="1bacd-106">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="1bacd-106">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="1bacd-107">Décrit les fonctionnalités de sécurité de WCF.</span><span class="sxs-lookup"><span data-stu-id="1bacd-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="1bacd-108">Concepts de sécurité</span><span class="sxs-lookup"><span data-stu-id="1bacd-108">Security Concepts</span></span>](security-concepts.md)  
 <span data-ttu-id="1bacd-109">Décrit la terminologie et les concepts de base utilisés dans la sécurité WCF.</span><span class="sxs-lookup"><span data-stu-id="1bacd-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="1bacd-110">Scénarios de sécurité courants</span><span class="sxs-lookup"><span data-stu-id="1bacd-110">Common Security Scenarios</span></span>](common-security-scenarios.md)  
 <span data-ttu-id="1bacd-111">Décrit les scénarios et les topologies que vous pouvez configurer avec WCF.</span><span class="sxs-lookup"><span data-stu-id="1bacd-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="1bacd-112">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="1bacd-112">Security Behaviors</span></span>](security-behaviors-in-wcf.md)  
 <span data-ttu-id="1bacd-113">Fournit une vue d'ensemble des comportements WCF qui affectent la sécurité, comme la définition des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="1bacd-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="1bacd-114">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="1bacd-114">Bindings and Security</span></span>](bindings-and-security.md)  
 <span data-ttu-id="1bacd-115">Une vue orientée sécurité des liaisons, y compris des rubriques qui montrent comment créer des liaisons de sécurité personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1bacd-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="1bacd-116">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="1bacd-116">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
 <span data-ttu-id="1bacd-117">Décrit comment sécuriser des messages à l’aide des fonctionnalités de sécurité WCF.</span><span class="sxs-lookup"><span data-stu-id="1bacd-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="1bacd-118">Authentification</span><span class="sxs-lookup"><span data-stu-id="1bacd-118">Authentication</span></span>](authentication-in-wcf.md)  
 <span data-ttu-id="1bacd-119">Illustre des tâches d’authentification courantes.</span><span class="sxs-lookup"><span data-stu-id="1bacd-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="1bacd-120">Autorisation</span><span class="sxs-lookup"><span data-stu-id="1bacd-120">Authorization</span></span>](authorization-in-wcf.md)  
 <span data-ttu-id="1bacd-121">Décrit des scénarios d'autorisation courants avec des implémentations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1bacd-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="1bacd-122">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="1bacd-122">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
 <span data-ttu-id="1bacd-123">Décrit les principes de base de la fédération et comment créer des clients qui communiquent avec des serveurs fédérés.</span><span class="sxs-lookup"><span data-stu-id="1bacd-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="1bacd-124">Confiance partielle</span><span class="sxs-lookup"><span data-stu-id="1bacd-124">Partial Trust</span></span>](partial-trust.md)  
 <span data-ttu-id="1bacd-125">Décrit comment exécuter des scénarios de confiance partielle et des limitations WCF lors de l’exécution d’une confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="1bacd-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="1bacd-126">Audit</span><span class="sxs-lookup"><span data-stu-id="1bacd-126">Auditing</span></span>](auditing-security-events.md)  
 <span data-ttu-id="1bacd-127">Décrit comment effectuer un audit des événements de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1bacd-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="1bacd-128">Aide sur la sécurité et meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="1bacd-128">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
 <span data-ttu-id="1bacd-129">Instructions pour la création d’applications WCF sécurisées.</span><span class="sxs-lookup"><span data-stu-id="1bacd-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1bacd-130">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="1bacd-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="1bacd-131">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="1bacd-131">Related Sections</span></span>  
 [<span data-ttu-id="1bacd-132">Détails des fonctionnalités WCF</span><span class="sxs-lookup"><span data-stu-id="1bacd-132">WCF Feature Details</span></span>](index.md)  
  
 [<span data-ttu-id="1bacd-133">Programmation WCF de base</span><span class="sxs-lookup"><span data-stu-id="1bacd-133">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="1bacd-134">Didacticiel Prise en main</span><span class="sxs-lookup"><span data-stu-id="1bacd-134">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)  
  
 [<span data-ttu-id="1bacd-135">Vue d’ensemble conceptuelle</span><span class="sxs-lookup"><span data-stu-id="1bacd-135">Conceptual Overview</span></span>](../conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="1bacd-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bacd-136">See also</span></span>

- [<span data-ttu-id="1bacd-137">Configuration de votre application</span><span class="sxs-lookup"><span data-stu-id="1bacd-137">Configuring Your Application</span></span>](../diagnostics/configuring-your-application.md)
