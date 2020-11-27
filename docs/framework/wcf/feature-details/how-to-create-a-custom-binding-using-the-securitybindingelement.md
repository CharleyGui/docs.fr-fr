---
title: 'Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: 9aaaf6a10e0c51db35720d72512c1a91cfbb9720
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256740"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement

Windows Communication Foundation (WCF) comprend plusieurs liaisons fournies par le système qui peuvent être configurées, mais n’offrent pas une flexibilité totale lors de la configuration de toutes les options de sécurité prises en charge par WCF. Cette rubrique montre comment créer une liaison personnalisée directement à partir d'éléments de liaison individuels et met en évidence certains des paramètres de sécurité qui peuvent être spécifiés lors de la création d'une liaison de ce type. Pour plus d’informations sur la création de liaisons personnalisées, consultez [extension des liaisons](../extending/extending-bindings.md).  
  
> [!WARNING]
> <xref:System.ServiceModel.Channels.SecurityBindingElement> ne prend pas en charge la forme de canal <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, qui est la forme de canal par défaut utilisée par le transport TCP lorsque <xref:System.ServiceModel.TransferMode> a la valeur <xref:System.ServiceModel.TransferMode.Buffered>. Vous devez définir <xref:System.ServiceModel.TransferMode> à <xref:System.ServiceModel.TransferMode.Streamed> pour utiliser <xref:System.ServiceModel.Channels.SecurityBindingElement> dans ce scénario.  
  
## <a name="creating-a-custom-binding"></a>Création d’une liaison personnalisée  

 Dans WCF, toutes les liaisons sont composées d' *éléments de liaison*. Chaque élément de liaison dérive de la classe <xref:System.ServiceModel.Channels.BindingElement>. Pour les liaisons fournies par le système standard, les éléments de liaison sont créés et configurés automatiquement, bien que vous puissiez personnaliser quelques paramètres de propriétés.  
  
 En revanche, pour créer une liaison personnalisée, les éléments de liaison sont créés et configurés, puis une <xref:System.ServiceModel.Channels.CustomBinding> est créée à partir des éléments de liaison.  
  
 Pour ce faire, vous ajoutez les éléments de liaison individuels à une collection représentée par une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection>, puis vous affectez à la propriété `Elements` de `CustomBinding` une valeur égale à cet objet. Vous devez ajouter les éléments de liaison dans l'ordre suivant : flux de transaction, session fiable, sécurité, duplex composite, unidirectionnel, sécurité de flux de données, encodage de message et transport. Notez que les éléments de liaison répertoriés ne sont pas tous requis dans chaque liaison.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  

 Trois éléments de liaison concernent la sécurité au niveau des messages et tous sont dérivés de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>. Il s'agit de <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Le <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> est utilisé pour assurer une sécurité en mode mixte. Les deux autres éléments sont utilisés lorsque la couche message fournit la sécurité.  
  
 D'autres classes sont utilisées lorsque la sécurité au niveau du transport est assurée :  
  
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Éléments de liaison requis  

 Un grand nombre d’éléments de liaison peuvent être combinés dans une liaison. Toutes les combinaisons ne sont pas valides. Cette section décrit les éléments requis qui doivent être présents dans une liaison de sécurité.  
  
 Les liaisons de sécurité valides dépendent de nombreux facteurs, notamment :  
  
- Mode de sécurité  
  
- Protocole de transport  
  
- Modèle d’échange de messages (MEP) spécifié dans le contrat  
  
 Le tableau suivant indique les configurations des piles d’éléments de liaison valides pour chaque combinaison des facteurs précédents. Notez qu’il s’agit d’exigences minimales. Vous pouvez ajouter d'autres éléments de liaison à la liaison, notamment des éléments de liaison d'encodage de message et de transaction.  
  
|Mode de sécurité|Transport|Contracter le modèle d'échange de messages|Contracter le modèle d'échange de messages|Contracter le modèle d'échange de messages|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Transport|Https||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||StreamSecurityBindingElement de SSL ou Windows|StreamSecurityBindingElement de SSL ou Windows|StreamSecurityBindingElement de SSL ou Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Message|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (mode d'authentification = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||TCP|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (mode d'authentification = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Mixte (transport avec informations d'identification de message)|Https|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (mode d'authentification = SecureConversation)|SymmetricSecurityBindingElement (mode d'authentification = SecureConversation)|  
|||OneWayBindingElement|||  
|||StreamSecurityBindingElement de SSL ou Windows|StreamSecurityBindingElement de SSL ou Windows|StreamSecurityBindingElement de SSL ou Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Notez qu'il existe de nombreux paramètres configurables sur SecurityBindingElements. Pour plus d’informations, consultez [modes d’authentification SecurityBindingElement](securitybindingelement-authentication-modes.md).  
  
 Pour plus d’informations, consultez [conversations sécurisées et sessions sécurisées](secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Pour créer une liaison personnalisée qui utilise SymmetricSecurityBindingElement  
  
1. Créez une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection> portant le nom `outputBec`.  
  
2. Appelez la méthode statique `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, qui retourne une instance de la classe <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
3. Ajoutez <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à la collection (`outputBec`) en appelant la méthode `Add` de <xref:System.Collections.ObjectModel.Collection%601> de la classe <xref:System.ServiceModel.Channels.BindingElement>.  
  
4. Créez une instance de la classe <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> et ajoutez-la à la collection (`outputBec`). Cela spécifie l’encodage utilisé par la liaison.  
  
5. Créez un <xref:System.ServiceModel.Channels.HttpTransportBindingElement> et ajoutez-le à la collection `outputBec`. Cela indique que la liaison utilise le transport HTTP.  
  
6. Créez une liaison personnalisée en créant une instance de la classe <xref:System.ServiceModel.Channels.CustomBinding> et en passant la collection `outputBec` au constructeur.  
  
7. La liaison personnalisée résultante partage un grand nombre des caractéristiques de <xref:System.ServiceModel.WSHttpBinding>. Elle spécifie la sécurité au niveau du message et les informations d'identification Windows, mais désactive les sessions sécurisées, requiert que les informations d'identification du service soient spécifiées hors bande, et ne chiffre pas de signature. La dernière ne peut être contrôlée que par la définition de la propriété <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A>, tel qu'indiqué à l'étape 4. Les deux autres peuvent être contrôlées à l'aide de paramètres sur la liaison standard.  
  
## <a name="example"></a> Exemple  
  
### <a name="description"></a>Description  

 L'exemple suivant fournit une fonction complète permettant de créer une liaison personnalisée qui utilise <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
### <a name="code"></a>Code  

 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Extension de liaisons](../extending/extending-bindings.md)
- [Liaisons fournies par le système](../system-provided-bindings.md)
