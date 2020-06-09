---
title: 'Comment : désactiver le chiffrement des signatures numériques'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 7ef305fdfd9a4ee61dfd89fdd46f2dc03a350977
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595399"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Comment : désactiver le chiffrement des signatures numériques
Par défaut, un message est signé et la signature est chiffrée numériquement. Cette opération est contrôlée en créant une liaison personnalisée à l’aide d’une instance de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, et en affectant à la propriété `MessageProtectionOrder` de l’une de ces deux classes une valeur d’énumération <xref:System.ServiceModel.Security.MessageProtectionOrder>. Par défaut, il s’agit de <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ce processus consomme jusqu'à 30 pour cent de temps de plus que la simple signature et le chiffrement à partir de la taille de message totale (plus le message est petit, plus grand est l'impact sur les performances). Toutefois, désactiver le chiffrement de la signature présente un risque en matière de sécurité, puisqu'il peut permettre à un intrus de deviner le contenu du message. En effet, l'élément de la signature contient le code de hachage du texte brut de chaque partie signée du message. Par exemple, même si le corps des messages est chiffré par défaut, la signature non chiffrée contient le code de hachage du corps des messages avant le chiffrement. Si le jeu de valeurs possibles pour la partie signée et chiffrée est petit, un intrus peut être en mesure de deviner le contenu en consultant la valeur de hachage. Le chiffrement de la signature réduit les risques présents dans ce domaine.  
  
 Par conséquent, désactivez uniquement le chiffrement de la signature lorsque la valeur du contenu est basse ou le jeu de valeurs de contenu possible est grand et non déterministe, et le gain de performance est plus important que de réduire les risques d'attaque décrits précédemment.  
  
> [!NOTE]
> Si le message ne contient aucun élément chiffré, l'élément de signature n'est pas chiffré, même lorsque la propriété <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> a la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ce comportement se produit même avec les liaisons fournies par le système ; toutes les liaisons fournies par le système ont l’ordre de protection des messages défini à `SignBeforeEncryptAndEncryptSignature`. Toutefois, le Web Services Description Language (WSDL) généré par WCF contient toujours l' `<sp:EncryptSignature>` assertion.  
  
### <a name="to-disable-digital-signing"></a>Pour désactiver la signature numérique  
  
1. Créez un <xref:System.ServiceModel.Channels.CustomBinding>. Pour plus d’informations, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Ajoutez un élément <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou un élément <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à la collection de liaisons.  
  
3. Affectez à la propriété <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> ou affectez à la propriété <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de sécurité avec des liaisons personnalisées](security-capabilities-with-custom-bindings.md)
