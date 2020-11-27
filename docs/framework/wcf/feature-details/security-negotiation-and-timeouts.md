---
title: Négociation et délais de sécurité
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 4ccc7e5539b1a772be6f9edb5a4cb4d94a8d1c1b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275981"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="5d404-102">Négociation et délais de sécurité</span><span class="sxs-lookup"><span data-stu-id="5d404-102">Security Negotiation and Timeouts</span></span>

<span data-ttu-id="5d404-103">Lorsque les clients et les services s’authentifient, Windows Communication Foundation (WCF) prend en charge un mode dans lequel les informations d’identification du service sont négociées dans le cadre de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="5d404-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="5d404-104">Dans un tel cas, un échange potentiellement multi-segment intervient entre le client et le service. Il permet la propagation des informations d'identification du service vers le client.</span><span class="sxs-lookup"><span data-stu-id="5d404-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="5d404-105">La propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> contrôle le délai nécessaire à l'exécution de cet échange.</span><span class="sxs-lookup"><span data-stu-id="5d404-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="5d404-106">Toutefois, ce délai est appliqué uniquement lorsque l'échange nécessite plusieurs demandes-réponses.</span><span class="sxs-lookup"><span data-stu-id="5d404-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="5d404-107">Lorsque la négociation s'effectue en une seule boucle, ce délai n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="5d404-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d404-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d404-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="5d404-109">Procédure : définir une inclinaison de l’horloge maximale</span><span class="sxs-lookup"><span data-stu-id="5d404-109">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)
