---
title: Négociation et délais de sécurité
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 1b5fb15b4ea00ba33b741c96bcb423aefe9890fa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600995"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="02d18-102">Négociation et délais de sécurité</span><span class="sxs-lookup"><span data-stu-id="02d18-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="02d18-103">Lorsque les clients et les services s’authentifient, Windows Communication Foundation (WCF) prend en charge un mode dans lequel les informations d’identification du service sont négociées dans le cadre de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="02d18-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="02d18-104">Dans un tel cas, un échange potentiellement multi-segment intervient entre le client et le service. Il permet la propagation des informations d'identification du service vers le client.</span><span class="sxs-lookup"><span data-stu-id="02d18-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="02d18-105">La propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> contrôle le délai nécessaire à l'exécution de cet échange.</span><span class="sxs-lookup"><span data-stu-id="02d18-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="02d18-106">Toutefois, ce délai est appliqué uniquement lorsque l'échange nécessite plusieurs demandes-réponses.</span><span class="sxs-lookup"><span data-stu-id="02d18-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="02d18-107">Lorsque la négociation s'effectue en une seule boucle, ce délai n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="02d18-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d18-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02d18-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="02d18-109">Comment : définir une inclinaison de l'horloge maximale</span><span class="sxs-lookup"><span data-stu-id="02d18-109">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)
