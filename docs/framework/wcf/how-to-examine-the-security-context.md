---
title: 'Procédure : examiner le contexte de sécurité'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
ms.openlocfilehash: 40950614892ddfd4eb24194f0389e057a5a13378
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272942"
---
# <a name="how-to-examine-the-security-context"></a>Procédure : examiner le contexte de sécurité

Lors de la programmation des services Windows Communication Foundation (WCF), le contexte de sécurité du service vous permet de déterminer les détails sur les informations d’identification du client et les revendications utilisées pour l’authentification auprès du service. Pour ce faire, utilisez les propriétés de la classe <xref:System.ServiceModel.ServiceSecurityContext>.  
  
 Par exemple, vous pouvez récupérer l'identité du client actuel en utilisant la propriété <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ou <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>. Pour déterminer si le client est ou non anonyme, utilisez la propriété <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.  
  
 Vous pouvez également déterminer les revendications effectuées pour le compte du client en effectuant une itération dans la collection de revendications de la propriété <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.  
  
### <a name="to-get-the-current-security-context"></a>Pour obtenir le contexte de sécurité actuel  
  
- Accédez à la propriété <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> statique pour obtenir le contexte de sécurité actuel. Examinez chacune des propriétés du contexte actuel à partir de la référence.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Pour déterminer l'identité de l'appelant  
  
1. Imprimez la valeur des propriétés <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> et <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Pour analyser les revendications d'un appelant  
  
1. Retournez la classe actuelle <xref:System.IdentityModel.Policy.AuthorizationContext>. Utilisez la propriété <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> pour retourner le contexte de sécurité des services actuel, puis retournez `AuthorizationContext` à l'aide de la propriété <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.  
  
2. Analysez la collection d’objets <xref:System.IdentityModel.Claims.ClaimSet> retournés par la propriété <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> de la classe <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
## <a name="example"></a> Exemple  

 L'exemple suivant imprime les valeurs des propriétés <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> et <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> du contexte de sécurité actuel ainsi que la propriété <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, la valeur de ressource de la revendication et la propriété <xref:System.IdentityModel.Claims.Claim.Right%2A> de chaque revendication du contexte de sécurité actuel.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilation du code  

 Le code utilise les espaces de noms suivants :  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation de services](securing-services.md)
- [Identité du service et authentification](./feature-details/service-identity-and-authentication.md)
