---
title: 'Procédure : désactiver des sessions sécurisées sur un WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972045"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Procédure : désactiver des sessions sécurisées sur un WSFederationHttpBinding

Certains services peuvent requérir des informations d'identification fédérées mais ne prennent pas en charge les sessions sécurisées. Dans ce cas, vous devez désactiver la fonctionnalité de session sécurisée. Contrairement à <xref:System.ServiceModel.WSHttpBinding>, la classe <xref:System.ServiceModel.WSFederationHttpBinding> n'offre aucun moyen de désactiver les sessions sécurisées lors de la communication avec un service. À la place, vous devez créer une liaison personnalisée qui remplace les paramètres de session sécurisée par un démarrage.

Cette rubrique montre comment modifier les éléments de liaison contenus dans une <xref:System.ServiceModel.WSFederationHttpBinding> pour créer une liaison personnalisée. Le résultat est identique à <xref:System.ServiceModel.WSFederationHttpBinding> mais n'utilise pas de sessions sécurisées.

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Pour créer une liaison fédérée personnalisée sans session sécurisée

1. Créez une instance de la classe <xref:System.ServiceModel.WSFederationHttpBinding> soit impérativement dans du code, soit en la chargeant à partir du fichier de configuration.

2. Clonez la <xref:System.ServiceModel.WSFederationHttpBinding> dans une <xref:System.ServiceModel.Channels.CustomBinding>.

3. Recherchez <xref:System.ServiceModel.Channels.SecurityBindingElement> dans <xref:System.ServiceModel.Channels.CustomBinding>.

4. Recherchez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> dans <xref:System.ServiceModel.Channels.SecurityBindingElement>.

5. Remplacez le <xref:System.ServiceModel.Channels.SecurityBindingElement> d’origine par l’élément de liaison de sécurité de démarrage des <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.

## <a name="example"></a>Exemples

L'exemple suivant permet de créer une liaison fédérée personnalisée sans session sécurisée.

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a>Compilation du code

- Pour compiler l'exemple de code, créez un projet qui référence l'assembly System.ServiceModel.dll.

## <a name="see-also"></a>Voir aussi

- [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
