---
title: 'Procédure : créer un service d’émission de jeton de sécurité'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
ms.openlocfilehash: cfe1da7c66f5c64ac3f5346bc23e9b618db38d20
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286459"
---
# <a name="how-to-create-a-security-token-service"></a>Procédure : créer un service d’émission de jeton de sécurité

Un service de jeton de sécurité implémente le protocole défini dans la spécification WS-Trust. Ce protocole définit des formats de message et des modèles d’échange de message pour émettre, renouveler, annuler et valider des jetons de sécurité. Un service de jeton de sécurité donné fournit une ou plusieurs de ces fonctions. Cette rubrique examine le scénario le plus courant : l'implémentation de l'émission de jeton.  
  
## <a name="issuing-tokens"></a>Émission de jetons  

 La spécification WS-Trust définit des formats de message, basés sur l'élément de schéma XSD (XML Schema Definition) `RequestSecurityToken` et sur l'élément de schéma XSD `RequestSecurityTokenResponse` pour réaliser une émission de jetons. De plus, elle définit les URI (Uniform Resource Identifier) d'action associés. L’URI d’action associé au `RequestSecurityToken` message est `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` . L’URI d’action associé au `RequestSecurityTokenResponse` message est   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` .  
  
### <a name="request-message-structure"></a>Structure d'un message de demande  

 La structure d'un message de demande d'émission se compose en général des éléments suivants :  
  
- URI de type de requête avec la valeur `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` .
  
- Un URI de type de jeton. Pour les jetons SAML (Security Assertions Markup Language) 1,1, la valeur de cet URI est `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .  
  
- Une valeur de taille de clé qui indique le nombre de bits inclus dans la clé à associer au jeton émis.  
  
- Un URI de type de clé. Pour les clés symétriques, la valeur de cet URI est `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` .  
  
 De plus, plusieurs autres éléments peuvent être présents :  
  
- Le matériel de clé fourni par le client.  
  
- Des informations d'étendue qui indiquent avec quel service cible le jeton émis sera utilisé.  
  
 Le service de jeton de sécurité utilise les informations incluses dans le message de demande d'émission lorsqu'il construit le message de réponse d'émission.  
  
## <a name="response-message-structure"></a>Structure d'un message de réponse  

 La structure d'un message de réponse d'émission se compose en général des éléments suivants :  
  
- Le jeton de sécurité émis, par exemple, une assertion SAML 1.1.  
  
- Un jeton de preuve associé au jeton de sécurité. Pour des clés symétriques, il s'agit souvent d'une forme chiffrée du matériel de clé.  
  
- Des références au jeton de sécurité émis. En général, le service de jeton de sécurité retourne une référence qui peut être utilisée lorsque le jeton émis apparaît dans un message ultérieur envoyé par le client et une autre référence qui peut être utilisée lorsque le jeton n'est pas présent dans les messages ultérieurs.  
  
 De plus, plusieurs autres éléments peuvent être présents :  
  
- Le matériel de clé fourni par le service de jeton de sécurité.  
  
- L'algorithme requis pour calculer la clé partagée.  
  
- Les informations de durée de vie du jeton émis.  
  
## <a name="processing-request-messages"></a>Traitement des messages de demande  

 Le service de jeton de sécurité traite la demande d'émission en examinant les différents éléments du message de demande et en s'assurant qu'il peut émettre un jeton satisfaisant la demande. Le service de jeton de sécurité doit déterminer les éléments suivants avant de créer le jeton à émettre :  
  
- La demande est vraiment une demande d'émission de jeton.  
  
- Le service de jeton de sécurité prend en charge le type de jeton demandé.  
  
- Le demandeur est autorisé à faire la demande.  
  
- Le service de jeton de sécurité peut satisfaire les attentes du demandeur en ce qui concerne le matériel de clé.  
  
 Deux parties essentielles de la construction d'un jeton correspondent à la détermination de la clé utilisée pour signer le jeton et de la clé utilisée pour chiffrer la clé partagée. Le jeton doit être signé pour que, lorsque le client présente le jeton au service cible, ce service puisse déterminer que le jeton a été émis par un service de jeton de sécurité qu'il approuve. Le matériel de clé doit être chiffré de telle façon que le service cible puisse le déchiffrer.  
  
 La signature d'une assertion SAML implique la création d'une instance <xref:System.IdentityModel.Tokens.SigningCredentials>. Le constructeur pour cette classe utilise les éléments suivants :  
  
- Un <xref:System.IdentityModel.Tokens.SecurityKey> pour la clé à utiliser pour signer l'assertion SAML.  
  
- Une chaîne qui identifie l'algorithme de signature à utiliser.  
  
- Une chaîne qui identifie l’algorithme de condensat à utiliser.  
  
- En option, un <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> qui identifie la clé à utiliser pour signer l'assertion.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Le chiffrement de la clé partagée implique le traitement du matériel de clé et son chiffrement avec une clé que le service cible peut utiliser pour déchiffrer la clé partagée. En général, la clé publique du service cible est utilisée.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 De plus, un objet <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> pour la clé chiffrée est requis.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 Ensuite, cet objet <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> est utilisé pour créer un `SamlSubject` dans le cadre du `SamlToken`.  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 Pour plus d’informations, consultez [exemple de Fédération](../samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Création de messages de réponse  

 Une fois que le service de jeton de sécurité traite la demande d'émission et construit le jeton à émettre avec la clé de vérification, le message de réponse doit être construit, qui inclut au moins le jeton demandé, le jeton de preuve et des références au jeton émis. Le jeton émis est en général un <xref:System.IdentityModel.Tokens.SamlSecurityToken> créé à partir de <xref:System.IdentityModel.Tokens.SamlAssertion>, comme le montre l'exemple ci-dessous.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 Dans le cas où le service de jeton de sécurité fournit le matériel de clé partagée, le jeton de preuve est construit en créant un <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 Pour plus d’informations sur la façon de construire le jeton de preuve lorsque le client et le service de jeton de sécurité fournissent tous deux un matériel de clé pour la clé partagée, consultez [exemple de Fédération](../samples/federation-sample.md).  
  
 Les références au jeton émis sont construites en créant des instances de la classe <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Ensuite, ces différentes valeurs sont sérialisées dans le message de réponse retourné au client.  
  
## <a name="example"></a> Exemple  

 Pour obtenir le code complet d’un service d’analyse de jeton de sécurité, consultez [exemple de Fédération](../samples/federation-sample.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [Federation, exemple](../samples/federation-sample.md)
