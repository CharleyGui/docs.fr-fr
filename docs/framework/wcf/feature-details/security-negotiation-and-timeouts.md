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
# <a name="security-negotiation-and-timeouts"></a>Négociation et délais de sécurité

Lorsque les clients et les services s’authentifient, Windows Communication Foundation (WCF) prend en charge un mode dans lequel les informations d’identification du service sont négociées dans le cadre de l’authentification. Dans un tel cas, un échange potentiellement multi-segment intervient entre le client et le service. Il permet la propagation des informations d'identification du service vers le client. La propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> contrôle le délai nécessaire à l'exécution de cet échange. Toutefois, ce délai est appliqué uniquement lorsque l'échange nécessite plusieurs demandes-réponses. Lorsque la négociation s'effectue en une seule boucle, ce délai n'est pas utilisé.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Procédure : définir une inclinaison de l’horloge maximale](how-to-set-a-max-clock-skew.md)
