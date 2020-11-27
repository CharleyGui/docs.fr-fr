---
title: Falsification
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: c2b0cae1dc57fac486122ca17fc8109ffe62f77d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249798"
---
# <a name="tampering"></a><span data-ttu-id="46ffe-102">Falsification</span><span class="sxs-lookup"><span data-stu-id="46ffe-102">Tampering</span></span>

<span data-ttu-id="46ffe-103">La *falsification* est l’action consistant à modifier un message ou à remettre un message, et à utiliser le message modifié à des fins autres que celles prévues.</span><span class="sxs-lookup"><span data-stu-id="46ffe-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="46ffe-104">Ne pas désactiver WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="46ffe-104">Do Not Disable WS-Addressing</span></span>  

 <span data-ttu-id="46ffe-105">La spécification WS-Addressing fournit des en-têtes d'adresse sur chaque message, ce qui permet au destinataire d'un message de vérifier l'expéditeur de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="46ffe-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="46ffe-106">Vous pouvez désactiver cette fonctionnalité en affectant <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> à la propriété <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="46ffe-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="46ffe-107">Si le mode de sécurité a la valeur Message et que WS-Addressing est désactivé, un intrus peut prendre la demande d'un client et l'envoyer à un autre service, le deuxième service n'ayant aucun moyen de détecter que le message est provenu du client d'origine.</span><span class="sxs-lookup"><span data-stu-id="46ffe-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="46ffe-108">En effet, le premier service peut prétendre qu'il est un client lorsqu'il parle au deuxième service.</span><span class="sxs-lookup"><span data-stu-id="46ffe-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="46ffe-109">Pour atténuer ce risque, n'affectez jamais <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> à la propriété <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> et évitez d'utiliser <xref:System.ServiceModel.Channels.MessageVersion>, tel que la propriété statique <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A>, qui affecte <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> à la propriété <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="46ffe-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ffe-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46ffe-110">See also</span></span>

- [<span data-ttu-id="46ffe-111">Security Considerations</span><span class="sxs-lookup"><span data-stu-id="46ffe-111">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="46ffe-112">Divulgation d’informations</span><span class="sxs-lookup"><span data-stu-id="46ffe-112">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="46ffe-113">Élévation de privilège</span><span class="sxs-lookup"><span data-stu-id="46ffe-113">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="46ffe-114">Déni de service</span><span class="sxs-lookup"><span data-stu-id="46ffe-114">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="46ffe-115">Scénarios non pris en charge</span><span class="sxs-lookup"><span data-stu-id="46ffe-115">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="46ffe-116">Attaques par relecture</span><span class="sxs-lookup"><span data-stu-id="46ffe-116">Replay Attacks</span></span>](replay-attacks.md)
