---
title: 'Procédure : personnaliser une liaison fournie par le système'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: e3d7cb72bcbdd636530e7861071b73f8a5f38b31
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249226"
---
# <a name="how-to-customize-a-system-provided-binding"></a>Procédure : personnaliser une liaison fournie par le système

Windows Communication Foundation (WCF) comprend plusieurs liaisons fournies par le système qui vous permettent de configurer certaines des propriétés des éléments de liaison sous-jacents, mais pas toutes les propriétés. Cette rubrique explique comment attribuer des propriétés aux éléments de liaison afin de créer une liaison personnalisée.  
  
 Pour plus d’informations sur la façon de créer et de configurer directement des éléments de liaison sans utiliser les liaisons fournies par le système, consultez [liaisons personnalisées](custom-bindings.md).  
  
 Pour plus d’informations sur la création et l’extension de liaisons personnalisées, consultez [extension des liaisons](extending-bindings.md).  
  
 Dans WCF, toutes les liaisons sont composées d' *éléments de liaison*. Chaque élément de liaison dérive de la classe <xref:System.ServiceModel.Channels.BindingElement>. Les liaisons fournies par le système telles que <xref:System.ServiceModel.BasicHttpBinding> créent et configurent leurs propres éléments de liaison. Cette rubrique vous indique comment accéder aux propriétés de ces éléments de liaison qui ne sont pas exposés directement sur la liaison et comment les modifier ; il s’agit, notamment, de la classe <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Les éléments de liaison individuels sont inclus dans une collection représentée par la classe <xref:System.ServiceModel.Channels.BindingElementCollection> et sont ajoutés dans l’ordre suivant : Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding et Transport. Notez que les éléments de liaison répertoriés ne sont pas tous requis dans chaque liaison. Les éléments de liaison définis par l’utilisateur peuvent également apparaître dans cette collection et doivent figurer dans le même ordre que précédemment. Par exemple, un transport défini par l'utilisateur doit être le dernier élément de la collection d'éléments de liaison.  
  
 La classe <xref:System.ServiceModel.BasicHttpBinding> contient trois éléments de liaison :  
  
1. Un élément de liaison de sécurité facultatif, soit la classe <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> utilisée avec le transport HTTP (sécurité de niveau transport), soit la classe <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> utilisée lorsque la couche transport fournit la sécurité, auquel cas le transport HTTPS est utilisé.  
  
2. Un élément de liaison d'encodeur de message requis, <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ou <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3. Un élément de liaison de transport requis, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, ou <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 Dans cet exemple, nous créons une instance de la liaison, générons une *liaison personnalisée* à partir de celle-ci, nous examinons les éléments de liaison dans la liaison personnalisée et, lorsque nous trouvons l’élément de liaison http, nous définissons sa `KeepAliveEnabled` propriété sur `false` . La propriété `KeepAliveEnabled` n’est pas exposée directement sur `BasicHttpBinding`, nous devons donc créer une liaison personnalisée pour naviguer jusqu’à l’élément de liaison et définir cette propriété.  
  
### <a name="to-modify-a-system-provided-binding"></a>Pour modifier une liaison fournie par le système  
  
1. Créez une instance de la classe <xref:System.ServiceModel.BasicHttpBinding> et affectez à son mode de sécurité la valeur de sécurité au niveau du message.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. Créez une liaison personnalisée à partir de la liaison et ensuite une classe <xref:System.ServiceModel.Channels.BindingElementCollection> à partir de l’une des propriétés de la liaison personnalisée.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. Parcourez la classe <xref:System.ServiceModel.Channels.BindingElementCollection> et lorsque vous trouverez la classe <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, affectez à sa propriété <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> la valeur `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Liaisons personnalisées](custom-bindings.md)
