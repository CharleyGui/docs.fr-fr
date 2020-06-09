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
# <a name="secure-sessions"></a>Sessions sécurisées
Une fonctionnalité de Windows Communication Foundation (WCF) est des sessions fiables qui garantissent que les messages sont reçus dans l’ordre dans lequel ils ont été envoyés. Les rubriques de cette section traitent des implications de sécurité à considérer lors de la création d'une session fiable. Pour plus d’informations sur les sessions fiables, consultez [utilisation de sessions](../using-sessions.md).  
  
> [!NOTE]
> Lorsque l’emprunt d’identité est requis sur Windows XP, utilisez une session sécurisée sans jeton de contexte de sécurité avec état (SCT). Lorsque des SCT avec état sont utilisés avec l’emprunt d’identité, une <xref:System.InvalidOperationException> est levée. Pour plus d’informations, consultez [scénarios non pris en charge](unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|||  
|-|-|  
|[Conversations sécurisées et sessions sécurisées](secure-conversations-and-secure-sessions.md)|Les termes « conversations sécurisées » et « sessions sécurisées » sont synonymes. Cette rubrique explique le fonctionnement d’une conversation sécurisée et quand et pourquoi utiliser le modèle.|  
|[Comment : créer une session sécurisée](how-to-create-a-secure-session.md)|Présente les étapes essentielles de la création d'une session sécurisée.|  
|[Procédure : créer un jeton de contexte de sécurité pour une session sécurisée](how-to-create-a-security-context-token-for-a-secure-session.md)|Présente les étapes nécessaires à la création d'une batterie de serveurs Web qui maintiendra l'état et les sessions avec les clients.|  
|[Considérations sur la sécurité pour les sessions sécurisées](security-considerations-for-secure-sessions.md)|Décrit des considérations spéciales relatives aux sessions sécurisées.|  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Sections connexes  
 [Sessions, instanciation et concurrence](sessions-instancing-and-concurrency.md)  
  
 [Conception et implémentation de services](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Voir aussi

- [Comment : activer la détection de relecture des messages](how-to-enable-message-replay-detection.md)
- [Attaques par relecture](replay-attacks.md)
- [Comment : créer un service qui requiert des sessions](how-to-create-a-service-that-requires-sessions.md)
