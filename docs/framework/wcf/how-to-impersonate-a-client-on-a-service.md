---
title: 'Procédure : emprunter l’identité d’un client sur un service'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: 24a06df5b6fbb908aff3ef1b2166fd5162549ba2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290112"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Procédure : emprunter l’identité d’un client sur un service

L’emprunt d’identité d’un client sur un service Windows Communication Foundation (WCF) permet au service d’effectuer des actions pour le compte du client. Pour les actions soumises à la vérification de la liste de contrôle d'accès (ACL), telles que l'accès aux répertoires et aux fichiers sur un ordinateur ou l'accès à une base de données SQL Server, la vérification de la liste ACL est effectuée en fonction du compte d'utilisateur client. Cette rubrique décrit les étapes de base requises pour permettre à un client dans un domaine Windows de définir un niveau d'emprunt de l'identité du client. Pour obtenir un exemple fonctionnel, consultez [Impersonating the Client](./samples/impersonating-the-client.md). Pour plus d’informations sur l’emprunt d’identité du client, consultez [délégation et emprunt d’identité](./feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
> Lorsque le client et le service s'exécutent sur le même ordinateur et que le client s'exécute sous un compte système (c'est-à-dire `Local System` ou `Network Service`), il n'est pas possible d'emprunter l'identité du client lorsqu'une session sécurisée est établie avec les jetons de contexte de sécurité avec état. Une application WinForms ou console s'exécute en général sous le compte actuellement connecté, afin que le l'emprunt d'identité du compte puisse être effectué par défaut. Toutefois, lorsque le client est une page ASP.NET et que la page est hébergée dans IIS 6,0 ou IIS 7,0, le client s’exécute sous le `Network Service` compte par défaut. Toutes les liaisons fournies par le système qui prennent en charge des sessions sécurisées utilisent par défaut un jeton de contexte de sécurité sans état. Toutefois, si le client est une page ASP.NET et que des sessions sécurisées avec des jetons de contexte de sécurité avec état sont utilisées, le client ne peut pas faire l’emprunt d’identité. Pour plus d’informations sur l’utilisation des jetons de contexte de sécurité avec état dans une session sécurisée, consultez [Comment : créer un jeton de contexte de sécurité pour une session sécurisée](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Pour activer l'emprunt de l'identité d'un client depuis un jeton Windows mis en cache sur un service  
  
1. Créez le service. Pour obtenir un didacticiel sur cette procédure de base, consultez [Getting Started Tutorial](getting-started-tutorial.md).  
  
2. Utilisez une liaison qui fait appel à l'authentification Windows et crée une session, telle que <xref:System.ServiceModel.NetTcpBinding> ou <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Lorsque vous créez l'implémentation de l'interface du service, appliquez la classe <xref:System.ServiceModel.OperationBehaviorAttribute> à la méthode qui requiert l'emprunt de l'identité du client. Affectez à la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> la valeur <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Pour définir le niveau d'emprunt d'identité autorisé sur le client  
  
1. Créez le code client du service à l’aide de [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md). Pour plus d’informations, consultez [accès aux services à l’aide d’un client WCF](accessing-services-using-a-wcf-client.md).  
  
2. Après avoir créé le client WCF, affectez <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> à la propriété de la <xref:System.ServiceModel.Security.WindowsClientCredential> classe l’une des <xref:System.Security.Principal.TokenImpersonationLevel> valeurs d’énumération.  
  
    > [!NOTE]
    > Pour utiliser <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, l'authentification Kerberos négociée (parfois appelée Kerberos *multi-leg* ou *multi-step* ) doit être utilisée. Pour obtenir une description de la manière d’implémenter cela, consultez [meilleures pratiques pour la sécurité](./feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [Emprunt de l'identité du client](./samples/impersonating-the-client.md)
- [Délégation et emprunt d’identité](./feature-details/delegation-and-impersonation-with-wcf.md)
