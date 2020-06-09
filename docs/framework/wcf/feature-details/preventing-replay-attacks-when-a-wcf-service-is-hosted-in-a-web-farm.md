---
title: Prévention des attaques par relecture en cas d'hébergement d'un service WCF dans une batterie de serveurs Web
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: 07743795effd3da9a241fd778756dd92d99d78f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596784"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Prévention des attaques par relecture en cas d'hébergement d'un service WCF dans une batterie de serveurs Web
Lors de l'utilisation de la sécurité du message, WCF empêche toute attaque par relecture en créant une valeur à usage unique à partir du message entrant et en vérifiant le `InMemoryNonceCache` interne pour voir si la valeur à usage unique générée est présente. Si tel est le cas, le message est ignoré comme relecture. Lorsqu'un service WCF est hébergé dans une batterie de serveurs Web, étant donné que `InMemoryNonceCache` n'est pas partagé entre les nœuds de la batterie de serveurs Web, le service est vulnérable aux attaques par relecture.  Pour limiter ce risque, WCF 4.5 fournit un point d'extensibilité qui vous permet d'implémenter votre propre cache partagé de valeurs à usage unique en dérivant une classe de la classe abstraite <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>Implémentation de NonceCache  
 Pour implémenter votre propre cache partagé de valeurs à usage unique, dérivez une classe de <xref:System.ServiceModel.Security.NonceCache> et substituez les méthodes <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> et <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> vérifiera pour voir si la valeur à usage unique spécifiée existe dans le cache. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> tente d'ajouter une valeur à usage unique au cache. Une fois que la classe est implémentée, vous l'accrochez en instanciant une instance et en l'assignant à <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> pour la détection de relecture côté client et à <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> pour la détection de relecture côté serveur. Il n’existe aucune prise en charge de configuration prête à l’emploi pour cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité des messages](message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../diagnostics/wmi/symmetricsecuritybindingelement.md)
