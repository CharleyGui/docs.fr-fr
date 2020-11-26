---
title: 'Procédure : créer un fournisseur de jetons de sécurité personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 94de506b16d97ec82b84ec6eed34111e99f62977
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249265"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Procédure : créer un fournisseur de jetons de sécurité personnalisé

Cette rubrique montre comment créer de nouveaux types de jetons à l'aide d'un fournisseur de jetons de sécurité personnalisé et comment intégrer le fournisseur à un gestionnaire de jetons de sécurité personnalisé.  
  
> [!NOTE]
> Créez un fournisseur de jetons personnalisé si les jetons fournis par le système, situés dans l'espace de noms <xref:System.IdentityModel.Tokens>, ne répondent pas à vos besoins.  
  
 Le fournisseur de jetons de sécurité crée une représentation de jeton de sécurité en fonction des informations d'identification du client ou du service. Pour utiliser le fournisseur de jetons de sécurité personnalisé dans la sécurité Windows Communication Foundation (WCF), vous devez créer des informations d’identification personnalisées et des implémentations de gestionnaire de jetons de sécurité.  
  
 Pour plus d’informations sur les informations d’identification personnalisées et le gestionnaire de jetons de sécurité, consultez la [procédure pas à pas : création d’informations d’identification client et service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md).  
  
### <a name="to-create-a-custom-security-token-provider"></a>Pour créer un fournisseur de jetons de sécurité personnalisé  
  
1. Définissez une nouvelle classe dérivée de la classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider>.  
  
2. Implémentez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29>. La méthode est chargée de créer et retourner une instance du jeton de sécurité. L'exemple suivant crée une classe nommée `MySecurityTokenProvider`et substitue la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> pour retourner une instance de la classe <xref:System.IdentityModel.Tokens.X509SecurityToken>. Le constructeur de classe requiert une instance de la classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Pour intégrer un fournisseur de jetons de sécurité personnalisé à un gestionnaire de jetons de sécurité personnalisé  
  
1. Définissez une nouvelle classe dérivée de la classe <xref:System.IdentityModel.Selectors.SecurityTokenManager>. (L'exemple suivant est dérivé de la classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, elle-même dérivée de la classe <xref:System.IdentityModel.Selectors.SecurityTokenManager>.)  
  
2. Substituez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> si elle ne l'est pas déjà.  
  
     La <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> méthode est chargée de retourner une instance de la <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe appropriée au <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> paramètre passé à la méthode par l’infrastructure de sécurité WCF. Modifiez la méthode pour retourner l'implémentation du fournisseur de jetons de sécurité personnalisé (créée dans la procédure précédente) lorsque la méthode est appelée avec un paramètre de jeton de sécurité approprié. Pour plus d’informations sur le gestionnaire de jetons de sécurité, consultez la [procédure pas à pas : création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md).  
  
3. Ajoutez une logique personnalisée à la méthode pour lui permettre de retourner votre fournisseur de jetons de sécurité personnalisé en fonction du paramètre <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>. L’exemple suivant retourne le fournisseur de jetons de sécurité personnalisé si les exigences de jeton sont satisfaites. Ces exigences incluent un jeton de sécurité X.509 et la direction des messages (le jeton est utilisé pour la sortie de message). Dans tous les autres cas, le code appelle la classe de base pour conserver le comportement fourni par le système pour les autres exigences de jeton de sécurité.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a> Exemple  

 Le code suivant montre une implémentation <xref:System.IdentityModel.Selectors.SecurityTokenProvider> complète avec une implémentation <xref:System.IdentityModel.Selectors.SecurityTokenManager> correspondante.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.X509SecurityToken>
- [Procédure pas à pas : création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md)
- [Procédure : créer un authentificateur de jetons de sécurité personnalisé](how-to-create-a-custom-security-token-authenticator.md)
