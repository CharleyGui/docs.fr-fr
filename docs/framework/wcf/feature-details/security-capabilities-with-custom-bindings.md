---
title: Fonctionnalités de sécurité avec des liaisons personnalisées
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 1b12907481ccb3f3c5f4b8aaba6ede8ebfa6228a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288305"
---
# <a name="security-capabilities-with-custom-bindings"></a>Fonctionnalités de sécurité avec des liaisons personnalisées

Vous pouvez effectuer la plupart des tâches de sécurité courantes en utilisant l'une des liaisons fournies par le système. Toutefois, si vous avez besoin de plus de contrôle, vous pouvez créer une liaison personnalisée à l'aide de <xref:System.ServiceModel.Channels.SecurityBindingElement>, comme expliqué dans les rubriques suivantes. Pour plus d’informations sur les liaisons personnalisées, consultez [liaisons personnalisées](../extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Modes d'authentification SecurityBindingElement](securitybindingelement-authentication-modes.md)  
 Décrit les modes d’authentification possibles avec une liaison personnalisée.  
  
 [Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Décrit les étapes de base pour créer une liaison personnalisée avec un élément de sécurité.  
  
 [Procédure : créer un SecurityBindingElement pour un mode d’authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Décrit comment créer un élément de sécurité pour un mode d'authentification spécifié.  
  
 [Procédure : désactiver des sessions sécurisées sur un WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Décrit comment désactiver des sessions sécurisées lors de la création d'un service FS.  
  
 [Procédure : activer la détection de réexécution des messages](how-to-enable-message-replay-detection.md)  
 Décrit comment déterminer le moment où une attaque par relecture se produit.  
  
 [Procédure : créer des informations d’identification de prise en charge](how-to-create-a-supporting-credential.md)  
 Décrit comment fournir des informations d'identification de prise en charge à un service, si ce dernier en a besoin.  
  
 [Procédure : configurer une confirmation de signature](how-to-set-up-a-signature-confirmation.md)  
 Décrit les étapes permettant de confirmer des signatures lors de la signature numérique de messages.  
  
 [Procédure : définir une inclinaison de l’horloge maximale](how-to-set-a-max-clock-skew.md)  
 Décrit comment définir la différence de temps maximale autorisée entre un service et un client.  
  
 [Procédure : désactiver le chiffrement des signatures numériques](how-to-disable-encryption-of-digital-signatures.md)  
 Décrit les avantages de la désactivation du chiffrement des signatures numériques en matière de performances.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>Sections connexes  

 [Fonctionnement des niveaux de protection](../understanding-protection-level.md)  
  
 [Sécurisation des services et des clients](securing-services-and-clients.md)  
  
## <a name="see-also"></a>Voir aussi

- [Liaisons et sécurité](bindings-and-security.md)
- [Présentation de la sécurité](security-overview.md)
- [Liaisons fournies par le système](../system-provided-bindings.md)
