---
title: "Comment : créer une information d'identification de prise en charge"
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: b8e7ddcd6118c77e14e090a0b1fa8d65aeb8e3df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597148"
---
# <a name="how-to-create-a-supporting-credential"></a>Comment : créer une information d'identification de prise en charge
Il est possible d'avoir un modèle de sécurité personnalisé qui requiert plusieurs informations d'identification. Par exemple, un service peut exiger du client non seulement un nom d'utilisateur et un mot de passe, mais également une information d'identification qui prouve que le client a plus de 18 ans. La deuxième information d’identification est une *information d’identification de prise en charge*. Cette rubrique explique comment implémenter ces informations d’identification dans un client Windows Communication Foundation (WCF).  
  
> [!NOTE]
> La spécification pour la prise en charge d'informations d'identification fait partie de la spécification WS-SecurityPolicy. Pour plus d’informations, consultez [spécifications de Web Services Security](https://docs.microsoft.com/previous-versions/dotnet/articles/ms951273(v=msdn.10)).  
  
## <a name="supporting-tokens"></a>Supporting Tokens  
 En résumé, lorsque vous utilisez la sécurité de message, les *informations d’identification principales* sont toujours utilisées pour sécuriser le message (par exemple, un certificat X. 509 ou un ticket Kerberos).  
  
 Comme défini par la spécification, une liaison de sécurité utilise des *jetons* pour sécuriser l’échange de messages. Un *jeton* est une représentation d’informations d’identification de sécurité.  
  
 La liaison de sécurité utilise un jeton principal identifié dans la stratégie de liaison de sécurité pour créer une signature. Cette signature est appelée *signature de message*.  
  
 Des jetons supplémentaires peuvent être spécifiés afin d'augmenter les revendications fournies par le jeton associé à la signature de message.  
  
## <a name="endorsing-signing-and-encrypting"></a>Endossement, signature et chiffrement  
 Les informations d’identification de prise en charge entraînent la transmission d’un *jeton de prise en charge* dans le message. La spécification WS-SecurityPolicy définit quatre façons de joindre un jeton de prise en charge au message, comme décrit dans le tableau suivant.  
  
|Objectif|Description|  
|-------------|-----------------|  
|Signé|Le jeton de prise en charge est inclus dans l'en-tête de sécurité et est signé par la signature de message.|  
|Endossement|Un *jeton d’endossement* signe la signature du message.|  
|Signé et endossement|Les jetons d'endossement signés signent l'élément `ds:Signature` entier produit à partir de la signature de message et sont eux-mêmes signés par cette signature de message ; autrement dit, les deux jetons (le jeton utilisé pour la signature de message et le jeton d'endossement signé) se signent l'un l'autre.|  
|Signé et chiffrement|Les jetons de prise en charge chiffrés et signés sont des jetons de prise en charge signés qui sont également chiffrés lorsqu'ils apparaissent dans le `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Programmation d'informations d'identification de prise en charge  
 Pour créer un service qui utilise des jetons de prise en charge, vous devez créer un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) . (Pour plus d’informations, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 La première étape de création d’une liaison personnalisée consiste à créer un élément de liaison de sécurité, qui peut être l’un des trois types suivants :  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Toutes les classes héritent de l'objet <xref:System.ServiceModel.Channels.SecurityBindingElement>, qui inclut quatre propriétés pertinentes :  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Étendues  
 Il existe deux étendues pour les informations d'identification de prise en charge :  
  
- Les *jetons de prise en charge du point de terminaison* prennent en charge toutes les opérations d’un point de terminaison. Autrement dit, l'information d'identification que le jeton de prise en charge représente peut être utilisée chaque fois qu'une opération de point de terminaison est appelée.  
  
- Les *jetons de prise en charge* de l’opération prennent uniquement en charge une opération de point de terminaison spécifique.  
  
 Comme indiqué par les noms de propriétés, les informations d'identification de prise en charge peuvent être obligatoires ou facultatives. Autrement dit, l'information d'identification de prise en charge est utilisée si elle est présente, bien que cela ne soit pas nécessaire, mais l'authentification n'échouera pas si elle n'est pas présente.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Pour créer une liaison personnalisée qui inclut des informations d’identification de prise en charge  
  
1. Créez un élément de liaison de sécurité. L'exemple suivant crée un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> avec le mode d'authentification `UserNameForCertificate`. Utilisez la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.  
  
2. Ajoutez le paramètre de prise en charge à la collection de types retournée par la propriété appropriée (`Endorsing`, `Signed`, `SignedEncrypted` ou `SignedEndorsed`). Les types dans l'espace de noms <xref:System.ServiceModel.Security.Tokens> incluent des types couramment utilisés, tels que <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant crée une instance du <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et ajoute une instance de la classe <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> à la collection retournée par la propriété Endorsing.  
  
### <a name="code"></a>Code  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
