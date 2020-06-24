---
title: 'Comment : créer un jeton personnalisé'
description: Découvrez comment créer un jeton de sécurité personnalisé dans WCF à l’aide de la classe SecurityToken et comment l’intégrer à un fournisseur de jetons de sécurité et à un authentificateur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
ms.openlocfilehash: a95d663c2669186fcb3eb1fb2f0c426ade945f1c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247531"
---
# <a name="how-to-create-a-custom-token"></a>Comment : créer un jeton personnalisé
Cette rubrique contient des instructions permettant de créer un jeton de sécurité personnalisé à l'aide de la classe <xref:System.IdentityModel.Tokens.SecurityToken> et de l'intégrer à un fournisseur et authentificateur de jetons de sécurité personnalisés. Pour obtenir un exemple de code complet, consultez l’exemple de [jeton personnalisé](../samples/custom-token.md) .  
  
 Un *jeton de sécurité* est essentiellement un élément XML utilisé par l’infrastructure de sécurité Windows Communication Foundation (WCF) pour représenter les revendications relatives à un expéditeur à l’intérieur du message SOAP. La sécurité WCF fournit différents jetons pour les modes d’authentification fournis par le système. Les exemples comprennent un jeton de sécurité de certificat X.509 représenté par la classe <xref:System.IdentityModel.Tokens.X509SecurityToken> ou un jeton de sécurité de nom d'utilisateur représenté par la classe <xref:System.IdentityModel.Tokens.UserNameSecurityToken>.  
  
 Il peut arriver qu'un mode d'authentification ou que des informations d'identification ne soient pas prises en charge par les types fournis. Dans un tel cas, il est nécessaire de créer un jeton de sécurité personnalisé permettant de fournir une représentation XML des informations d'identification personnalisées dans les messages SOAP.  
  
 Les procédures suivantes montrent comment créer un jeton de sécurité personnalisé et comment l’intégrer à l’infrastructure de sécurité WCF. Cette rubrique contient des instructions permettant de créer un jeton de carte de crédit utilisé pour passer des informations relatives à la carte de crédit du client au serveur.  
  
 Pour plus d’informations sur les informations d’identification personnalisées et le gestionnaire de jetons de sécurité, consultez [procédure pas à pas : création d’informations d’identification de service et de client personnalisées](walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Consultez l'espace de noms <xref:System.IdentityModel.Tokens> pour obtenir davantage de classes représentant des jetons de sécurité.  
  
## <a name="procedures"></a>Procédures  
 Une application cliente doit être créée de manière à permettre la spécification d'informations de carte de crédit pour l'infrastructure de sécurité. Une classe d'informations d'identification client personnalisées permet à l'application d'accéder à ces informations. La première étape consiste à créer une classe qui représente les informations de carte de crédit au sein des informations d'identification client personnalisées.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Pour créer une classe qui représente les informations de carte de crédit au sein des informations d'identification client.  
  
1. Définissez une nouvelle classe qui représente les informations de carte de crédit pour l'application. L'exemple suivant nomme la classe `CreditCardInfo`.  
  
2. Ajoutez les propriétés adéquates à cette classe pour permettre à une application de définir les informations requises pour le jeton personnalisé. Dans notre exemple, cette classe dispose de trois propriétés : `CardNumber`, `CardIssuer` et `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Vous devez ensuite créer une classe qui représente le jeton de sécurité personnalisé. Cette classe est utilisée par le fournisseur de jetons de sécurité, l’authentificateur et les classes de sérialiseur pour transmettre des informations sur le jeton de sécurité depuis et vers l’infrastructure de sécurité WCF.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Pour créer une classe de jeton de sécurité personnalisé  
  
1. Définissez une nouvelle classe dérivée de la classe <xref:System.IdentityModel.Tokens.SecurityToken>. Cet exemple crée une classe nommée `CreditCardToken`.  
  
2. Remplacez la propriété <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A>. Cette propriété est utilisée pour obtenir l'identificateur local du jeton de sécurité qui permet de renvoyer à la représentation XML de ce dernier à partir des autres éléments figurant dans les messages SOAP. Dans cet exemple, l'identificateur de jeton peut être passé à cette propriété comme paramètre de constructeur ou un nouvel identificateur aléatoire est généré à chaque fois qu'une instance de jeton de sécurité est créée.  
  
3. Implémentez la propriété <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A>. Cette propriété retourne une collection de clés de sécurité représentée par l'instance de jeton de sécurité. Ces clés peuvent être utilisées par WCF pour signer ou chiffrer des parties du message SOAP. Dans cet exemple, le jeton de sécurité de carte de crédit ne peut pas contenir n'importe quelle clé de sécurité, c'est pourquoi l'implémentation retourne toujours une collection vide.  
  
4. Remplacez les propriétés <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> et <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A>. Ces propriétés sont utilisées par WCF pour déterminer la validité de l’instance du jeton de sécurité. Dans cet exemple, seule une date d'expiration est définie pour le jeton de carte de crédit, par conséquent la propriété `ValidFrom` retourne la valeur <xref:System.DateTime>, laquelle représente l'heure et la date de création de l'instance.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Lorsqu'un nouveau jeton de sécurité est créé, la classe <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> doit à nouveau être implémentée. L’implémentation est utilisée dans la configuration de l’élément de liaison de sécurité afin de représenter un nouveau type de jeton. La classe des paramètres de jeton de sécurité sert de modèle, lequel permet de mettre en correspondance la véritable instance de jeton de sécurité lorsqu'un message est traité. Ce modèle contient des propriétés supplémentaires qu'une application peut utiliser afin de spécifier les critères que le jeton de sécurité doit respecter pour pouvoir être utilisé ou authentifié. L’exemple suivant n’ajoute pas de propriétés supplémentaires. par conséquent, seul le type de jeton de sécurité est mis en correspondance lorsque l’infrastructure WCF recherche une instance de jeton de sécurité à utiliser ou à valider.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Pour créer une classe de paramètres de jeton de sécurité personnalisé  
  
1. Définissez une nouvelle classe dérivée de la classe <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>.  
  
2. Implémentez la méthode <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A>. Copiez tous les champs internes définis dans votre classe, le cas échéant. Cet exemple ne définit aucun champ supplémentaire.  
  
3. Implémentez la propriété en lecture seule <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A>. Cette propriété retourne `true` si le type de jeton de sécurité représenté par cette classe peut être utilisé pour authentifier un client auprès d'un service. Dans cet exemple, le jeton de sécurité de carte de crédit peut être utilisé pour authentifier un client auprès d'un service.  
  
4. Implémentez la propriété en lecture seule <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A>. Cette propriété retourne `true` si le type de jeton de sécurité représenté par cette classe peut être utilisé pour authentifier un service auprès d'un client. Dans cet exemple, le jeton de sécurité de carte de crédit ne peut pas être utilisé pour authentifier un service auprès d'un client.  
  
5. Implémentez la propriété en lecture seule <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A>. Cette propriété retourne `true` si le type de jeton de sécurité représenté par cette classe peut être mappé à un compte Windows. Si c'est le cas, le résultat de l'authentification est représenté par une instance de la classe <xref:System.Security.Principal.WindowsIdentity>. Dans cet exemple, le jeton ne peut pas être mappé à un compte Windows.  
  
6. Implémentez la méthode <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29>. Cette méthode est appelée par l’infrastructure de sécurité WCF lorsqu’elle requiert une référence à l’instance de jeton de sécurité représentée par cette classe de paramètres de jeton de sécurité. La véritable instance de jeton de sécurité et le type <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> qui spécifie le type de la référence demandée sont tous les deux passés à cette méthode sous forme d’arguments. Dans cet exemple, seules les références internes sont prises en charge par le jeton de sécurité de carte de crédit. La classe <xref:System.IdentityModel.Tokens.SecurityToken> dispose d'une fonctionnalité permettant de créer des références internes ; l'implémentation ne nécessite donc pas de code supplémentaire.  
  
7. Implémentez la méthode <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29>. Cette méthode est appelée par WCF pour convertir l’instance de la classe de paramètres de jeton de sécurité en une instance de la <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> classe. Le résultat est utilisé par les fournisseurs de jeton de sécurité pour créer l'instance de jeton de sécurité adéquate.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Les jetons de sécurité sont transmis dans les messages SOAP. Cette opération nécessite un mécanisme de traduction entre la représentation de jeton de sécurité en mémoire et la représentation en transmission. WCF utilise un sérialiseur de jeton de sécurité pour accomplir cette tâche. Chaque jeton personnalisé doit être accompagné par un sérialiseur de jeton de sécurité personnalisé pouvant le sérialiser et le désérialiser à partir des messages SOAP.  
  
> [!NOTE]
> Les clés dérivées sont activées par défaut. Si vous créez un jeton de sécurité personnalisé et que vous l’utilisez comme jeton principal, WCF en déduit une clé. Ce faisant, il appelle le sérialiseur de jeton de sécurité personnalisé afin d'écrire <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> pour le jeton de sécurité personnalisé pendant la sérialisation du `DerivedKeyToken` sur le câble. À l'extrémité de réception, lors de la désérialisation du jeton du câble, le sérialiseur `DerivedKeyToken` attend un élément `SecurityTokenReference` en tant qu'enfant de niveau supérieur au-dessous de lui. Si le sérialiseur de jeton de sécurité personnalisé n'a pas ajouté d'élément `SecurityTokenReference` pendant la sérialisation de son type de clause, une exception est levée.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Pour créer un sérialiseur de jeton de sécurité personnalisé  
  
1. Définissez une nouvelle classe dérivée de la classe <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>.  
  
2. Remplacez la méthode <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29>. Elle utilise un <xref:System.Xml.XmlReader> pour lire le flux XML. Cette méthode retourne `true` si l'implémentation du sérialiseur peut désérialiser le jeton de sécurité en fonction de l'élément en cours. Dans cet exemple, cette méthode vérifie si le nom et l'espace de noms de l'élément XML en cours du lecteur XML sont corrects. Dans le cas contraire, elle appelle l'implémentation de classe de base de cette méthode pour gérer l'élément XML.  
  
3. Remplacez la méthode <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> . Cette méthode lit le contenu XML de jeton de sécurité et construit la représentation en mémoire adéquate lui correspondant. Si elle ne reconnaît pas l'élément XML du lecteur XML passé, elle appelle l'implémentation de base pour traiter les types de jeton fournis par le système.  
  
4. Remplacez la méthode <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> . Cette méthode retourne `true` si elle peut convertir la représentation en mémoire du jeton (passée sous forme d'argument) en représentation XML. Dans le cas contraire, elle appelle l'implémentation de la classe de base.  
  
5. Remplacez la méthode <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> . Cette méthode convertit la représentation en mémoire du jeton de sécurité en représentation XML. Si elle ne peut pas effectuer la conversion, elle appelle l'implémentation de la classe de base.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Les quatre procédures ci-dessus effectuées, intégrez le jeton de sécurité personnalisé au fournisseur, authentificateur et gestionnaire de jetons de sécurité ainsi qu'aux informations d'identification client et service.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Pour intégrer le jeton de sécurité personnalisé à un fournisseur de jetons de sécurité  
  
1. Le fournisseur de jeton de sécurité crée, modifie (si nécessaire) et retourne une instance du jeton. Pour créer un fournisseur de jetons de sécurité pour le jeton de sécurité personnalisé, créez une classe qui hérite de la classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider>. L'exemple suivant remplace la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> pour retourner une instance de `CreditCardToken`. Pour plus d’informations sur les fournisseurs de jetons de sécurité personnalisés, consultez [Comment : créer un fournisseur de jetons de sécurité personnalisé](how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Pour intégrer le jeton de sécurité personnalisé à un authentificateur de jetons de sécurité  
  
1. L'authentificateur de jetons de sécurité valide le contenu du jeton de sécurité lorsque ce dernier est extrait du message. Pour créer un authentificateur personnalisé pour le jeton de sécurité personnalisé, créez une classe qui hérite de la classe <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>. L'exemple suivant substitue la méthode <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A>. Pour plus d’informations sur les authentificateurs de jetons de sécurité personnalisés, consultez [Comment : créer un authentificateur de jetons de sécurité personnalisé](how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Pour intégrer le jeton de sécurité personnalisé à un gestionnaire de jetons de sécurité  
  
1. Le gestionnaire de jetons de sécurité crée les instances de fournisseur, d'authentificateur et de sérialiseur de jetons de sécurité appropriées. Pour créer un gestionnaire de jetons de sécurité personnalisé, créez une classe qui hérite de la classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>. Les principales méthodes de la classe utilisent une spécification <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> pour créer le fournisseur approprié ainsi que les informations d'identification client ou service requises. Pour plus d’informations sur les gestionnaires de jetons de sécurité personnalisés, consultez [procédure pas à pas : création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Pour intégrer le jeton de sécurité personnalisé aux informations d'identification client et service personnalisées  
  
1. Les informations d'identification client et service doivent être ajoutées afin de générer une API pour l'application. Cette API permet de spécifier les informations du jeton de sécurité personnalisé qui seront utilisées par l'infrastructure de ce dernier créée précédemment afin de générer son contenu et de l'authentifier. Les exemples suivants montrent comment procéder. Pour plus d’informations sur les informations d’identification de client et de service personnalisées, consultez [procédure pas à pas : création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 La classe de paramètres de jeton de sécurité personnalisée créée précédemment est utilisée pour indiquer à l’infrastructure de sécurité WCF qu’un jeton de sécurité personnalisé doit être utilisé lors de la communication avec un service. La procédure suivante indique comment effectuer cette opération.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Pour intégrer le jeton de sécurité personnalisé à la liaison  
  
1. La classe de paramètres de jeton de sécurité personnalisé doit être spécifiée dans l'une des collections de paramètres de jeton exposées sur la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>. Dans l'exemple suivant, la collection retournée par `SignedEncrypted` est utilisée. Le code ajoute un jeton personnalisé de carte de crédit à tous les messages envoyés depuis le client au service, le contenu de ce jeton étant automatiquement signé et chiffré.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 Cette rubrique décrit les différents éléments de code nécessaires à l'implémentation et l'utilisation d'un jeton personnalisé. Pour voir un exemple complet de la façon dont tous ces éléments de code s’ajustent ensemble, consultez [jeton personnalisé](../samples/custom-token.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Tokens.SecurityToken>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>
- <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>
- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Procédure pas à pas : création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md)
- [Guide pratique pour créer un authentificateur de jetons de sécurité personnalisé](how-to-create-a-custom-security-token-authenticator.md)
- [Comment : créer un fournisseur de jetons de sécurité personnalisé](how-to-create-a-custom-security-token-provider.md)
