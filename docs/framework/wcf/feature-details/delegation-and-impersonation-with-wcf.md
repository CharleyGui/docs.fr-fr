---
title: Délégation et emprunt d'identité avec WCF
description: Découvrez les méthodes d’emprunt d’identité et de délégation que WCF utilise pour limiter l’accès client aux ressources d’un domaine de service.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- impersonation [WCF]
- delegation [WCF]
ms.assetid: 110e60f7-5b03-4b69-b667-31721b8e3152
ms.openlocfilehash: 91e7ea8df5c32329f0eb8d12943ce5f816ff0e5a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557591"
---
# <a name="delegation-and-impersonation-with-wcf"></a>Délégation et emprunt d'identité avec WCF
L'*emprunt d'identité* est une technique courante utilisée par les services pour restreindre l'accès du client aux ressources d'un domaine de service. Les ressources de domaine de service peuvent être des ressources d'ordinateur, telles que des fichiers locaux (emprunt d'identité), ou une ressource sur un autre ordinateur, tel qu'un partage de fichiers (délégation). Pour obtenir un exemple d'application, consultez [Impersonating the Client](../samples/impersonating-the-client.md). Pour obtenir un exemple sur l’utilisation de l’emprunt d’identité, consultez [How to: Impersonate a Client on a Service](../how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
> Sachez que lors de l'emprunt d'identité d'un client sur un service, le service s'exécute avec les informations d'identification du client, qui peut avoir des privilèges plus élevés que le processus serveur.  
  
## <a name="overview"></a>Vue d’ensemble  
 Généralement, les clients appellent un client pour que celui-ci effectue une action au nom du client. L'emprunt d'identité permet au service d'agir comme le client lors de l'exécution de l'action. La délégation permet à un service frontal de transmettre la demande du client à un service principal d'une manière qui permet au service principal d'emprunter l'identité du client. L'emprunt d'identité est une méthode couramment utilisée pour vérifier si un client est autorisé à effectuer une action donnée. La délégation est une méthode permettant de transmettre les fonctions d'emprunt d'identité avec l'identité du client à un service principal. La délégation est une fonctionnalité du domaine Windows qui peut être utilisée dans le cadre de l'authentification Kerberos. La délégation n'est pas la même chose que le flux d'identité et comme la délégation transfère la possibilité d'emprunter l'identité du client sans connaître son mot de passe, elle représente une opération d'un niveau de privilège supérieur au flux d'identité.  
  
 L'emprunt d'identité et la délégation nécessitent que le client possède une identité Windows. Si ce n'est pas le cas, la seule option consiste à transmettre l'identité du client au second service.  
  
## <a name="impersonation-basics"></a>Principes de base de l'emprunt d'identité  
 Windows Communication Foundation (WCF) prend en charge l’emprunt d’identité pour diverses informations d’identification du client. Cette rubrique décrit la prise en charge de modèle de service permettant d'emprunter l'identité de l'appelant pendant l'implémentation d'une méthode de service. Les scénarios de déploiement courants impliquant l’emprunt d’identité et la sécurité SOAP et les options WCF dans ces scénarios sont également abordés.  
  
 Cette rubrique se concentre sur l’emprunt d’identité et la délégation dans WCF lors de l’utilisation de la sécurité SOAP. Vous pouvez également utiliser l’emprunt d’identité et la délégation avec WCF lors de l’utilisation de la sécurité de transport, comme décrit dans [utilisation de l’emprunt d’identité avec la sécurité de transport](using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>Deux méthodes  
 La sécurité SOAP WCF a deux méthodes distinctes pour effectuer l’emprunt d’identité. La méthode utilisée dépend de la liaison. L'une concerne l'emprunt d'identité à partir d'un jeton Windows fourni par l'authentification SSPI (Security Support Provider Interface) ou Kerberos, qui est ensuite mis en cache sur le service. La deuxième concerne l'emprunt d'identité à partir d'un jeton Windows fourni par les extensions Kerberos, collectivement appelées *S4U* (Service-for-User).  
  
### <a name="cached-token-impersonation"></a>Emprunt d'identité avec jeton mis en cache  
 Vous pouvez effectuer l'emprunt d'identité avec jeton mis en cache à l'aide des éléments suivants :  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>et <xref:System.ServiceModel.NetTcpBinding> avec une information d'identification de client Windows.  
  
- <xref:System.ServiceModel.BasicHttpBinding> avec <xref:System.ServiceModel.BasicHttpSecurityMode> défini à l'information d'identification <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> , ou toute autre liaison standard dans laquelle le client présente une information d'identification de nom d'utilisateur que le service peut mapper à un compte Windows valide.  
  
- Tout <xref:System.ServiceModel.Channels.CustomBinding> qui utilise une information d'identification de client Windows avec `requireCancellation` défini à `true`. (La propriété est disponible sur les classes suivantes : <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> , <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters> et <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters> .) Si une conversation sécurisée est utilisée sur la liaison, la propriété doit également avoir la `requireCancellation` valeur `true` .  
  
- Tout <xref:System.ServiceModel.Channels.CustomBinding> où le client présente une information d'identification de nom d'utilisateur. Si une conversation sécurisée est utilisée sur la liaison, sa propriété `requireCancellation` doit également avoir la valeur `true`.  
  
### <a name="s4u-based-impersonation"></a>Emprunt d'identité basé sur S4U  
 Vous pouvez effectuer l'emprunt d'identité basé sur S4U à l'aide des éléments suivants :  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>et <xref:System.ServiceModel.NetTcpBinding> avec une information d'identification de client de certificat que le service peut mapper à un compte Windows valide.  
  
- Tout <xref:System.ServiceModel.Channels.CustomBinding> qui utilise une information d'identification de client Windows avec la propriété `requireCancellation` définie à `false`.  
  
- Tout <xref:System.ServiceModel.Channels.CustomBinding> qui utilise un nom d'utilisateur ou une information d'identification de client Windows et une conversation sécurisée avec la propriété `requireCancellation` définie à `false`.  
  
 L'étendue à laquelle le service peut emprunter l'identité du client dépend des privilèges dont le compte de service dispose lorsqu'il tente l'emprunt d'identité, du type d'emprunt d'identité utilisé, et éventuellement de l'étendue d'emprunt d'identité autorisée par le client.  
  
> [!NOTE]
> Lorsque le client et le service s'exécutent sur le même ordinateur et que le client s'exécute sous un compte système (par exemple, `Local System` ou `Network Service`), il n'est pas possible d'emprunter l'identité du client lorsqu'une session sécurisée est établie avec les jetons de contexte de sécurité avec état. Une application Windows Forms ou console s'exécute en général sous le compte actuellement connecté, afin que l'emprunt d'identité du compte puisse être effectué par défaut. Toutefois, lorsque le client est une page ASP.NET et que la page est hébergée dans IIS 6,0 ou IIS 7,0, le client s’exécute sous le `Network Service` compte par défaut. Toutes les liaisons fournies par le système qui prennent en charge des sessions sécurisées utilisent par défaut un jeton de contexte de sécurité sans état. Toutefois, si le client est une page ASP.NET, et que des sessions sécurisées avec SCT avec état sont utilisées, le client ne peut pas faire l’emprunt d’identité. Pour plus d’informations sur l’utilisation de SCT avec état dans une session sécurisée, consultez [Comment : créer un jeton de contexte de sécurité pour une session sécurisée](how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Emprunt d'identité dans une méthode de service : modèle déclaratif  
 La plupart des scénarios d'emprunt d'identité impliquent l'exécution de la méthode de service dans le contexte de l'appelant. WCF fournit une fonctionnalité d’emprunt d’identité qui facilite cette opération en permettant à l’utilisateur de spécifier l’exigence d’emprunt d’identité dans l' <xref:System.ServiceModel.OperationBehaviorAttribute> attribut. Par exemple, dans le code suivant, l’infrastructure WCF emprunte l’identité de l’appelant avant d’exécuter la `Hello` méthode. Toute tentative d'accès aux ressources natives à l'intérieur de la méthode `Hello` réussit uniquement si la liste de contrôle d'accès (ACL, Access Control List) de la ressource autorise les privilèges d'accès de l'appelant. Pour activer l'emprunt d'identité, affectez l'une des valeurs d'énumération <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> ( <xref:System.ServiceModel.ImpersonationOption> ou <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> ) à la propriété <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, tel qu'indiqué dans l'exemple suivant.  
  
> [!NOTE]
> Lorsqu'un service a des informations d'identification plus élevées que le client distant, celles-ci sont utilisées si la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> a la valeur <xref:System.ServiceModel.ImpersonationOption.Allowed>. En d'autres termes, si un utilisateur à privilèges faibles fournit ses informations d'identification, un service à privilèges plus élevés exécute la méthode avec les informations d'identification du service, et peut utiliser des ressources que l'utilisateur à privilèges faibles n'aurait pas pu utiliser sinon.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 L’infrastructure WCF peut emprunter l’identité de l’appelant uniquement si l’appelant est authentifié avec des informations d’identification qui peuvent être mappées à un compte d’utilisateur Windows. Si le service est configuré pour authentifier l'utilisation d'une information d'identification qui ne peut pas être mappée à un compte Windows, la méthode de service n'est pas exécutée.  
  
> [!NOTE]
> Sur Windows XP, l’emprunt d’identité échoue si un SCT avec état est créé, ce qui génère un <xref:System.InvalidOperationException> . Pour plus d’informations, consultez [scénarios non pris en charge](unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Emprunt d'identité dans une méthode de service : modèle impératif  
 Un appelant n'a parfois pas besoin d'emprunter l'identité de l'ensemble de la méthode de service pour fonctionner, mais uniquement une partie de celle-ci. Dans ce cas, obtenez l'identité Windows de l'appelant à l'intérieur de la méthode de service et exécutez l'emprunt d'identité de manière impérative. Pour ce faire, utilisez la propriété <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> de <xref:System.ServiceModel.ServiceSecurityContext> pour retourner une instance de la classe <xref:System.Security.Principal.WindowsIdentity> , et appelez la méthode <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> avant d'utiliser l'instance.  
  
> [!NOTE]
> Veillez à utiliser l' `Using` instruction Visual Basic ou l' `using` instruction C# pour rétablir automatiquement l’action d’emprunt d’identité. Si vous n’utilisez pas l’instruction ou si vous utilisez un langage de programmation autre que Visual Basic ou C#, assurez-vous de rétablir le niveau d’emprunt d’identité. Si vous ne le faites pas, vous risquez de vous exposer à des attaques par déni de service et d'élévation de privilège.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Emprunt d'identité pour toutes les méthodes de service  
 Dans certains cas, vous devez exécuter toutes les méthodes d'un service dans le contexte de l'appelant. Au lieu d'activer explicitement cette fonction par méthode, utilisez <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Comme indiqué dans le code suivant, affectez <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> à la propriété `true`. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> est récupéré des collections de comportements de la classe <xref:System.ServiceModel.ServiceHost> . Notez également que la propriété `Impersonation` de <xref:System.ServiceModel.OperationBehaviorAttribute> appliquée à chaque méthode doit également avoir la valeur <xref:System.ServiceModel.ImpersonationOption.Allowed> ou <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 Le tableau suivant décrit le comportement WCF pour toutes les combinaisons possibles de `ImpersonationOption` et `ImpersonateCallerForAllServiceOperations` .  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Comportement|  
|---------------------------|------------------------------------------------|--------------|  
|Obligatoire|n/a|WCF emprunte l’identité de l’appelant|  
|Autorisé|false|WCF n’emprunte pas l’identité de l’appelant|  
|Autorisé|true|WCF emprunte l’identité de l’appelant|  
|Non autorisé|false|WCF n’emprunte pas l’identité de l’appelant|  
|Non autorisé|true|Non autorisé. (Une exception <xref:System.InvalidOperationException> est levée.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Niveau d'emprunt d'identité obtenu à partir des informations d'identification Windows et emprunt d'identité avec jeton mis en cache  
 Dans certains scénarios, le client contrôle en partie le niveau d'emprunt d'identité que le service effectue lorsqu'une information d'identification de client Windows est utilisée. L'un de ces scénarios se produit lorsque le client spécifie un niveau d'emprunt d'identité à Anonymous. L'autre se produit lors de l'exécution de l'emprunt d'identité avec un jeton mis en cache. Pour ce faire, définissez la propriété <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> de la classe <xref:System.ServiceModel.Security.WindowsClientCredential> , qui est accessible en tant que propriété de la classe <xref:System.ServiceModel.ChannelFactory%601> générique.  
  
> [!NOTE]
> Si vous spécifiez un niveau d'emprunt d'identité à Anonymous, le client ouvre une session sur le service de façon anonyme. Le service doit donc autoriser des ouvertures de session anonymes, indépendamment de l'exécution de l'emprunt d'identité.  
  
 Le client peut spécifier le niveau d'emprunt d'identité à <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>ou <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Un jeton est uniquement généré au niveau spécifié, tel qu'indiqué dans le code suivant.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Le tableau suivant spécifie le niveau d'emprunt d'identité que le service obtient lors de l'emprunt d'identité à partir d'un jeton mis en cache.  
  
|Valeur `AllowedImpersonationLevel`|Le Service a `SeImpersonatePrivilege`|Le Service et le client sont capables de délégation|Jeton `ImpersonationLevel`mis en cache|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonyme|Oui|n/a|Emprunt d'identité|  
|Anonyme|Non|n/a|Identification|  
|Identification|n/a|n/a|Identification|  
|Emprunt d'identité|Oui|n/a|Emprunt d'identité|  
|Emprunt d'identité|Non|n/a|Identification|  
|La délégation|Oui|Oui|La délégation|  
|La délégation|Oui|Non|Emprunt d'identité|  
|La délégation|Non|n/a|Identification|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Niveau d'emprunt d'identité obtenu à partir des informations d'identification de nom d'utilisateur et emprunt d'identité avec jeton mis en cache  
 En passant le service à son nom d’utilisateur et son mot de passe, un client permet à WCF de se connecter en tant qu’utilisateur, ce qui équivaut à affecter à la propriété la valeur `AllowedImpersonationLevel` <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> . (Le `AllowedImpersonationLevel` est disponible sur les <xref:System.ServiceModel.Security.WindowsClientCredential> <xref:System.ServiceModel.Security.HttpDigestClientCredential> classes et.) Le tableau suivant indique le niveau d’emprunt d’identité obtenu lorsque le service reçoit les informations d’identification de nom d’utilisateur.  
  
|`AllowedImpersonationLevel`|Le Service a `SeImpersonatePrivilege`|Le Service et le client sont capables de délégation|Jeton `ImpersonationLevel`mis en cache|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|n/a|Oui|Oui|La délégation|  
|n/a|Oui|Non|Emprunt d'identité|  
|n/a|Non|n/a|Identification|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Niveau d'emprunt d'identité obtenu à partir de l'emprunt d'identité basé sur S4U  
  
|Le Service a `SeTcbPrivilege`|Le Service a `SeImpersonatePrivilege`|Le Service et le client sont capables de délégation|Jeton `ImpersonationLevel`mis en cache|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Oui|Oui|n/a|Emprunt d'identité|  
|Oui|Non|n/a|Identification|  
|Non|n/a|n/a|Identification|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Mappage d'un certificat client à un compte Windows  
 Il est possible pour un client de s'authentifier auprès d'un service à l'aide d'un certificat et que le service mappe le client à un compte existant par le biais d'Active Directory. Le code XML suivant indique comment configurer le service pour mapper le certificat.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="MapToWindowsAccount">  
      <serviceCredentials>  
        <clientCertificate>  
          <authentication mapClientCertificateToWindowsAccount="true" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Le code suivant indique comment configurer le service.  
  
```csharp
// Create a binding that sets a certificate as the client credential type.  
WSHttpBinding b = new WSHttpBinding();  
b.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a service host that maps the certificate to a Windows account.  
Uri httpUri = new Uri("http://localhost/Calculator");  
ServiceHost sh = new ServiceHost(typeof(HelloService), httpUri);  
sh.Credentials.ClientCertificate.Authentication.MapClientCertificateToWindowsAccount = true;  
```  
  
## <a name="delegation"></a>La délégation  
 Pour déléguer à un service principal, un service doit effectuer une authentification Kerberos multi-leg (SSPI sans NTLM) ou une authentification directe Kerberos au service principal à l'aide de l'identité Windows du client. Pour déléguer à un service principal, créez un <xref:System.ServiceModel.ChannelFactory%601> et un canal, puis communiquez par le biais du canal lors de l'emprunt d'identité du client. Avec cette forme de délégation, la distance entre l'emplacement du service principal et le service frontal dépend du niveau d'emprunt d'identité atteint par le service frontal. Lorsque le niveau d'emprunt d'identité est <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, les services frontaux et principaux doivent s'exécuter sur le même ordinateur. Lorsque le niveau d'emprunt d'identité est <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, les services frontaux et principaux peuvent être présents sur des ordinateurs séparés ou sur le même ordinateur. L'activation de l'emprunt d'identité au niveau délégation nécessite que la stratégie du domaine Windows soit configurée pour permettre la délégation. Pour plus d’informations sur la configuration d’Active Directory pour la prise en charge de la délégation, consultez [Enabling Delegated Authentication](/previous-versions/windows/it-pro/windows-server-2003/cc780217(v=ws.10))(Activation de l’authentification déléguée).  
  
> [!NOTE]
> Lorsqu'un client s'authentifie auprès du service frontal à l'aide d'un nom d'utilisateur et d'un mot de passe qui correspondent à un compte Windows, le service frontal peut s'authentifier auprès du service principal en réutilisant le nom et le mot de passe du client. Il s'agit d'une forme très puissante de flux d'identité, car la transmission d'un nom d'utilisateur et d'un mot de passe au service principal permet à ce service d'effectuer l'emprunt d'identité, mais elle ne constitue pas une délégation en l'absence de l'utilisation de Kerberos. Les contrôles Active Directory sur la délégation ne s'appliquent pas à l'authentification par nom d'utilisateur et par mot de passe.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>La délégation comme fonction du niveau d'emprunt d'identité  
  
|Niveau d'emprunt d'identité|Le service peut effectuer une délégation interprocessus|Le service peut effectuer une délégation sur plusieurs ordinateurs|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Non|Non|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Oui|Non|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Oui|Oui|  
  
 L'exemple de code suivant montre comment utiliser la délégation.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Comment configurer une Application pour utiliser la délégation contrainte  
 Avant de pouvoir utiliser la délégation contrainte, l'expéditeur, le destinataire et le contrôleur de domaine doivent être configurés en conséquence. La procédure suivante répertorie les étapes qui permettent d'activer la délégation contrainte. Pour des informations sur les différences entre la délégation et la délégation contrainte, consultez la section [Windows Server 2003 Kerberos Extensions](/previous-versions/windows/it-pro/windows-server-2003/cc738207(v=ws.10)) (Kerberos dans Windows Server 2003) qui traite de la délégation contrainte.  
  
1. Dans le contrôleur de domaine, désactivez la case à cocher **Le compte est sensible et ne peut pas être délégué** pour le compte sous lequel s'exécute l'application cliente.  
  
2. Dans le contrôleur de domaine, activez la case à cocher **Le compte est approuvé pour la délégation** pour le compte sous lequel s'exécute l'application cliente.  
  
3. Dans le contrôleur de domaine, configurez l'ordinateur intermédiaire pour qu'il soit approuvé pour la délégation en cliquant sur l'option **Approuver l'ordinateur pour la délégation** .  
  
4. Dans le contrôleur de domaine, configurez l'ordinateur intermédiaire pour utiliser la délégation contrainte en cliquant sur l'option **N'approuver cet ordinateur que pour la délégation aux services spécifiés** .  
  
 Pour obtenir des instructions plus détaillées sur la configuration de la délégation avec restriction, consultez [transition de protocole Kerberos et délégation avec restriction](/previous-versions/windows/it-pro/windows-server-2003/cc739587(v=ws.10)).
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>
- <xref:System.ServiceModel.ImpersonationOption>
- <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>
- <xref:System.ServiceModel.ServiceSecurityContext>
- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ChannelFactory%601>
- <xref:System.Security.Principal.TokenImpersonationLevel.Identification>
- [Utilisation de l'emprunt d'identité avec la sécurité de transport](using-impersonation-with-transport-security.md)
- [Emprunt de l'identité du client](../samples/impersonating-the-client.md)
- [Procédure : emprunter l’identité d’un client sur un service](../how-to-impersonate-a-client-on-a-service.md)
- [Outil Service Model Metadata Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
