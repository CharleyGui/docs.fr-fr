---
title: Sessions sécurisées
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: cb02adc7514e27175088e7664b12e45bc8ca5cd9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590083"
---
# <a name="secure-sessions"></a><span data-ttu-id="b5421-102">Sessions sécurisées</span><span class="sxs-lookup"><span data-stu-id="b5421-102">Secure Sessions</span></span>
<span data-ttu-id="b5421-103">Une fonctionnalité de Windows Communication Foundation (WCF) est des sessions fiables qui garantissent que les messages sont reçus dans l’ordre dans lequel ils ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="b5421-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="b5421-104">Les rubriques de cette section traitent des implications de sécurité à considérer lors de la création d'une session fiable.</span><span class="sxs-lookup"><span data-stu-id="b5421-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="b5421-105">Pour plus d’informations sur les sessions fiables, consultez [utilisation de sessions](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="b5421-105">For more information about reliable sessions, see [Using Sessions](../using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5421-106">Lorsque l’emprunt d’identité est requis sur Windows XP, utilisez une session sécurisée sans jeton de contexte de sécurité avec état (SCT).</span><span class="sxs-lookup"><span data-stu-id="b5421-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="b5421-107">Lorsque des SCT avec état sont utilisés avec l’emprunt d’identité, une <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="b5421-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="b5421-108">Pour plus d’informations, consultez [scénarios non pris en charge](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="b5421-108">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5421-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b5421-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="b5421-110">Conversations sécurisées et sessions sécurisées</span><span class="sxs-lookup"><span data-stu-id="b5421-110">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)|<span data-ttu-id="b5421-111">Les termes « conversations sécurisées » et « sessions sécurisées » sont synonymes.</span><span class="sxs-lookup"><span data-stu-id="b5421-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="b5421-112">Cette rubrique explique le fonctionnement d’une conversation sécurisée et quand et pourquoi utiliser le modèle.</span><span class="sxs-lookup"><span data-stu-id="b5421-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="b5421-113">Comment : créer une session sécurisée</span><span class="sxs-lookup"><span data-stu-id="b5421-113">How to: Create a Secure Session</span></span>](how-to-create-a-secure-session.md)|<span data-ttu-id="b5421-114">Présente les étapes essentielles de la création d'une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="b5421-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="b5421-115">Procédure : créer un jeton de contexte de sécurité pour une session sécurisée</span><span class="sxs-lookup"><span data-stu-id="b5421-115">How to: Create a Security Context Token for a Secure Session</span></span>](how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="b5421-116">Présente les étapes nécessaires à la création d'une batterie de serveurs Web qui maintiendra l'état et les sessions avec les clients.</span><span class="sxs-lookup"><span data-stu-id="b5421-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="b5421-117">Considérations sur la sécurité pour les sessions sécurisées</span><span class="sxs-lookup"><span data-stu-id="b5421-117">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)|<span data-ttu-id="b5421-118">Décrit des considérations spéciales relatives aux sessions sécurisées.</span><span class="sxs-lookup"><span data-stu-id="b5421-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="b5421-119">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="b5421-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="b5421-120">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="b5421-120">Related Sections</span></span>  
 [<span data-ttu-id="b5421-121">Sessions, instanciation et concurrence</span><span class="sxs-lookup"><span data-stu-id="b5421-121">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="b5421-122">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="b5421-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5421-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5421-123">See also</span></span>

- [<span data-ttu-id="b5421-124">Comment : activer la détection de relecture des messages</span><span class="sxs-lookup"><span data-stu-id="b5421-124">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="b5421-125">Attaques par relecture</span><span class="sxs-lookup"><span data-stu-id="b5421-125">Replay Attacks</span></span>](replay-attacks.md)
- [<span data-ttu-id="b5421-126">Comment : créer un service qui requiert des sessions</span><span class="sxs-lookup"><span data-stu-id="b5421-126">How to: Create a Service That Requires Sessions</span></span>](how-to-create-a-service-that-requires-sessions.md)
