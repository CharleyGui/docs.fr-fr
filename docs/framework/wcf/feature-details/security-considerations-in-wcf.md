---
title: Considérations relatives à la sécurité dans WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 796098258601ec5fa208fd8a8060b28c3eeeb4d6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276020"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="ba595-102">Considérations relatives à la sécurité dans WCF</span><span class="sxs-lookup"><span data-stu-id="ba595-102">Security Considerations in WCF</span></span>

<span data-ttu-id="ba595-103">Les rubriques de cette section répertorient les différents éléments liés à la sécurité à prendre en compte lors de la conception d’une application Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ba595-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba595-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ba595-104">In This Section</span></span>  

 [<span data-ttu-id="ba595-105">Divulgation d’informations</span><span class="sxs-lookup"><span data-stu-id="ba595-105">Information Disclosure</span></span>](information-disclosure.md)  
 <span data-ttu-id="ba595-106">Traite des diverses manières dont les informations peuvent être divulguées ou attaquées, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="ba595-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="ba595-107">Élévation de privilège</span><span class="sxs-lookup"><span data-stu-id="ba595-107">Elevation of Privilege</span></span>](elevation-of-privilege.md)  
 <span data-ttu-id="ba595-108">Traite des conséquences de l'attribution à un intrus d'autorisations plus étendues celles accordées initialement, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="ba595-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="ba595-109">Déni de service</span><span class="sxs-lookup"><span data-stu-id="ba595-109">Denial of Service</span></span>](denial-of-service.md)  
 <span data-ttu-id="ba595-110">Traite de ce qui arrive lorsqu'un système ne peut pas traiter des messages convenablement, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="ba595-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="ba595-111">Falsification</span><span class="sxs-lookup"><span data-stu-id="ba595-111">Tampering</span></span>](tampering.md)  
 <span data-ttu-id="ba595-112">Traite de la modification des messages ou de la remise des messages, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="ba595-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="ba595-113">Attaques par relecture</span><span class="sxs-lookup"><span data-stu-id="ba595-113">Replay Attacks</span></span>](replay-attacks.md)  
 <span data-ttu-id="ba595-114">Traite de ce qui arrive lorsqu'un intrus copie un flux de messages entre deux correspondants et relit le flux à l'un des correspondants ou les deux, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="ba595-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="ba595-115">Considérations sur la sécurité pour les sessions sécurisées</span><span class="sxs-lookup"><span data-stu-id="ba595-115">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="ba595-116">Traite des éléments suivants qui affectent la sécurité lors de l'implémentation de sessions sécurisées.</span><span class="sxs-lookup"><span data-stu-id="ba595-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="ba595-117">Scénarios non pris en charge</span><span class="sxs-lookup"><span data-stu-id="ba595-117">Unsupported Scenarios</span></span>](unsupported-scenarios.md)  
 <span data-ttu-id="ba595-118">Répertorie différents scénarios qui ne prennent pas en charge un aspect particulier de la sécurité et qui doivent être évités ou pris en compte.</span><span class="sxs-lookup"><span data-stu-id="ba595-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ba595-119">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="ba595-119">Reference</span></span>  

 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="ba595-120">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="ba595-120">Related Sections</span></span>  

 [<span data-ttu-id="ba595-121">Aide sur la sécurité et meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="ba595-121">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba595-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba595-122">See also</span></span>

- [<span data-ttu-id="ba595-123">Sécurité</span><span class="sxs-lookup"><span data-stu-id="ba595-123">Security</span></span>](security.md)
