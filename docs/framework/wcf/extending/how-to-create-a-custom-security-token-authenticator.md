---
title: 'Comment : créer un authentificateur de jetons de sécurité personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
ms.openlocfilehash: 667dc82502ba881b067b5588271947f7c18c8810
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249252"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Comment : créer un authentificateur de jetons de sécurité personnalisé

Cette rubrique indique comment créer un authentificateur de jetons de sécurité personnalisé et comment l'intégrer à un gestionnaire de jetons de sécurité personnalisé. Un authentificateur de jetons de sécurité valide le contenu du jeton de sécurité fourni par le message entrant. Lorsque le processus de validation réussit, l’authentificateur retourne une collection d’instances <xref:System.IdentityModel.Policy.IAuthorizationPolicy> qui, après évaluation, retourne un ensemble de revendications.  
  
 Pour utiliser un authentificateur de jetons de sécurité personnalisé dans Windows Communication Foundation (WCF), vous devez d’abord créer des informations d’identification personnalisées et des implémentations de gestionnaire de jetons de sécurité. Pour plus d’informations sur la création d’informations d’identification personnalisées et d’un gestionnaire de jetons de sécurité, consultez [procédure pas à pas : création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md).
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Pour créer un authentificateur de jetons de sécurité personnalisé  
  
1. Définissez une nouvelle classe dérivée de la classe <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>.  
  
2. Remplacez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> . La méthode retourne la valeur `true` ou `false` selon si l'authentificateur personnalisé peut ou non valider le type de jeton entrant.  
  
3. Remplacez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> . Cette méthode doit valider le contenu des jetons de manière adéquate. Si le jeton passe l'étape de validation, il retourne une collection d'instances <xref:System.IdentityModel.Policy.IAuthorizationPolicy>. L'exemple suivant utilise une implémentation de la stratégie d'autorisation personnalisée, laquelle sera créée au cours de la procédure suivante.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Le code précédent retourne une collection de stratégies d’autorisation dans la méthode <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29>. WCF ne fournit pas d’implémentation publique de cette interface. La procédure suivante indique comment procéder à cette implémentation publique, si requis par vos propres exigences.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Pour créer une stratégie d'autorisation personnalisée  
  
1. Définissez une nouvelle classe qui implémente l'interface <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2. Implémentez la propriété en lecture seule <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A>. L'une des solutions permettant d'implémenter cette propriété consiste à générer un identificateur global unique (Globally Unique Identifier, GUID) dans le constructeur de classe, puis de retourner cette propriété à chaque fois que sa valeur est demandée.  
  
3. Implémentez la propriété en lecture seule <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A>. Cette propriété doit retourner l'émetteur correspondant à tous les ensembles de revendications obtenus à partir du jeton. Cet émetteur doit correspondre à l'émetteur du jeton ou à une autorité chargée de valider le contenu des jetons. L'exemple suivant utilise la revendication d'émetteur passée à cette classe à partir de l'authentificateur de jetons de sécurité personnalisé créé au cours de la procédure précédente. L'authentificateur de jetons de sécurité personnalisé utilise l'ensemble des revendications fournies par le système (ensemble retourné par la propriété <xref:System.IdentityModel.Claims.ClaimSet.System%2A>) pour représenter l'émetteur de jeton de nom d'utilisateur.  
  
4. Implémentez la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A>. Cette méthode remplit une instance de la classe <xref:System.IdentityModel.Policy.EvaluationContext> (passée sous forme d’argument) avec les revendications basées sur le contenu des jetons de sécurité entrants. Cette méthode retourne la valeur `true` lorsque ce processus se déroule dans le cadre d'une évaluation. Lorsque l'implémentation s'appuie sur des stratégies d'autorisation fournissant des informations supplémentaires au contexte d'évaluation, cette méthode peut retourner la valeur `false` si les informations requises ne figurent pas encore dans le contexte d'évaluation. Dans ce cas, WCF appelle à nouveau la méthode après l’évaluation de toutes les autres stratégies d’autorisation générées pour le message entrant si au moins l’une de ces stratégies d’autorisation a modifié le contexte d’évaluation.  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [Procédure pas à pas : création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md) décrit comment créer des informations d’identification personnalisées et un gestionnaire de jetons de sécurité personnalisé. Pour utiliser l'authentificateur de jetons de sécurité personnalisés créé ici, une implémentation du gestionnaire de jetons de sécurité est modifiée pour retourner l'authentificateur personnalisé à partir de la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A>. La méthode retourne un authentificateur lorsqu’une exigence de jeton de sécurité appropriée est passée.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Pour intégrer un authentificateur de jetons de sécurité personnalisés à un gestionnaire de jetons de sécurité personnalisés  
  
1. Remplacez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> dans votre implémentation de gestionnaire de jetons de sécurité personnalisés.  
  
2. Ajoutez de la logique à la méthode pour lui permettre de retourner votre authentificateur de jetons de sécurité personnalisés basée sur le paramètre <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>. L’exemple suivant retourne un authentificateur de jetons de sécurité personnalisé si le type du jeton correspond à un nom d’utilisateur (représenté par la propriété <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A>) et si la direction de message pour laquelle l’authentificateur de jetons de sécurité est demandé correspond à entrée (représentée par le champ <xref:System.ServiceModel.Description.MessageDirection.Input> ).  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.UserNameSecurityToken>
- [Procédure pas à pas : création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md)
- [Procédure : créer un fournisseur de jetons de sécurité personnalisé](how-to-create-a-custom-security-token-provider.md)
