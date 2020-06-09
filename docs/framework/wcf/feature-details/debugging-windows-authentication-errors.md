---
title: Débogage d'erreurs d'authentification Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: eb3274b98234324bd47aa456feb4845da5a7f3a9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599280"
---
# <a name="debug-windows-authentication-errors"></a>Erreurs d’authentification Windows de débogage

Lorsque vous utilisez l'authentification Windows comme un mécanisme de sécurité, l'interface SSPI (Security Support Provider Interface) gère les processus de sécurité. Lorsque des erreurs de sécurité se produisent au niveau de la couche SSPI, elles sont signalées par Windows Communication Foundation (WCF). Cette rubrique fournit une infrastructure et un ensemble de questions permettant de diagnostiquer les erreurs.  
  
 Pour obtenir une vue d’ensemble du protocole Kerberos, consultez [explication de Kerberos](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10)). pour obtenir une vue d’ensemble de SSPI, consultez [SSPI](/windows/win32/secauthn/sspi).  
  
 Pour l’authentification Windows, WCF utilise généralement le fournisseur SSP (Security Support Provider) *Negotiate* , qui effectue une authentification mutuelle Kerberos entre le client et le service. Si le protocole Kerberos n’est pas disponible, WCF revient par défaut à NT LAN Manager (NTLM). Toutefois, vous pouvez configurer WCF pour utiliser uniquement le protocole Kerberos (et pour lever une exception si Kerberos n’est pas disponible). Vous pouvez également configurer WCF pour utiliser des formes restreintes du protocole Kerberos.  
  
## <a name="debugging-methodology"></a>Méthodologie de débogage  
 La méthode de base est la suivante :  
  
1. Déterminez si vous utilisez l'authentification Windows. Si vous utilisez un autre schéma, cette rubrique ne s'applique pas.  
  
2. Si vous êtes sûr d’utiliser l’authentification Windows, déterminez si votre configuration WCF utilise Kerberos direct ou Negotiate.  
  
3. Une fois que vous avez déterminé si votre configuration utilise le protocole Kerberos ou NTLM, vous pouvez comprendre les messages d'erreur dans le contexte correct.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Disponibilité du protocole Kerberos et de NTLM  
 Le fournisseur SSP Kerberos requiert qu'un contrôleur de domaine se comporte comme un centre de distribution de clés (KDC, Key Distribution Center). Le protocole Kerberos est disponible uniquement lorsque le client et le service utilisent des identités de domaine. NTLM est utilisé dans d'autres combinaisons de comptes, tel qu'indiqué dans le tableau suivant.  
  
 Les en-têtes du tableau présentent les types de compte possibles utilisés par le serveur. La colonne de gauche présente les types de compte possibles utilisés par le client.  
  
||Utilisateur local|Système Local|Utilisateur de domaine|Ordinateur de domaine|  
|-|----------------|------------------|-----------------|--------------------|  
|Utilisateur local|NTLM|NTLM|NTLM|NTLM|  
|Système Local|NTLM anonyme|NTLM anonyme|NTLM anonyme|NTLM anonyme|  
|Utilisateur de domaine|NTLM|NTLM|Kerberos|Kerberos|  
|Ordinateur de domaine|NTLM|NTLM|Kerberos|Kerberos|  
  
 Plus précisément, les quatre types de comptes incluent :  
  
- Utilisateur local : profil utilisateur, ordinateur uniquement. Par exemple, `MachineName\Administrator` ou `MachineName\ProfileName`.  
  
- Système local : compte intégré SYSTEM sur un ordinateur qui n'est pas joint à un domaine.  
  
- Utilisateur de domaine : compte d'utilisateur sur un domaine Windows. Par exemple : `DomainName\ProfileName`.  
  
- Ordinateur de domaine : processus avec identité d'ordinateur s'exécutant sur un ordinateur joint à un domaine Windows. Par exemple : `MachineName\Network Service`.  
  
> [!NOTE]
> Les informations d'identification du service sont capturées lorsque la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> de la classe <xref:System.ServiceModel.ServiceHost> est appelée. Les informations d'identification du client sont lues chaque fois que le client envoie un message.  
  
## <a name="common-windows-authentication-problems"></a>Problèmes courants d'authentification Windows  
 Cette section présente certains problèmes d'authentification Windows courants et les solutions possibles.  
  
### <a name="kerberos-protocol"></a>Protocole Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Problèmes de SPN/UPN rencontrés avec le protocole Kerberos  
 Si vous utilisez l'authentification Windows, et que le protocole Kerberos est utilisé ou négocié par SSPI, l'URL utilisée par le point de terminaison client doit inclure le nom de domaine complet de l'hôte du service dans l'URL de service. Cela suppose que le compte sous lequel le service s'exécute a accès à la clé SPN (Service Principal Name) par défaut de l'ordinateur créée lorsque celui-ci est ajouté au domaine Active Directory, ce qui s'effectue le plus souvent en exécutant le service sous le compte Service Réseau. Si le service n'a pas accès à la clé SPN de l'ordinateur, vous devez fournir le SPN correct ou un nom d'utilisateur principal (UPN, User Principal Name) du compte sous lequel le service s'exécute dans l'identité de point de terminaison du client. Pour plus d’informations sur le fonctionnement de WCF avec SPN et UPN, consultez [identité du service et authentification](service-identity-and-authentication.md).  
  
 Dans les scénarios d'équilibrage de charge, tels que les batteries de serveurs Web ou les jardins Web, une pratique courante consiste à définir un compte unique pour chaque application, assigner un SPN à ce compte et veiller à ce que tous les services de l'application s'exécutent sous ce compte.  
  
 Pour obtenir un SPN pour le compte de votre service, vous devez être administrateur de domaine Active Directory. Pour plus d’informations, consultez [supplément technique Kerberos pour Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Le protocole Kerberos direct requiert l'exécution du service sous un compte d'ordinateur de domaine  
 Cela se produit lorsque la propriété `ClientCredentialType` a la valeur `Windows` et que la propriété <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a la valeur `false`, tel qu'indiqué dans le code suivant.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Pour y remédier, exécutez le service à l'aide d'un compte d'ordinateur de domaine, tel que Service réseau, sur un ordinateur joint au domaine.  
  
### <a name="delegation-requires-credential-negotiation"></a>La délégation nécessite la négociation des informations d'identification  
 Pour utiliser le protocole d'authentification Kerberos avec délégation, vous devez implémenter le protocole Kerberos avec la négociation d'informations d'identification (parfois appelé Kerberos « multi-leg » ou Kerberos « multi-step »). Si vous implémentez l'authentification Kerberos sans négociation d'informations d'identification (parfois appelée Kerberos « one-shot » ou Kerberos « single-leg »), une exception sera levée.  
  
 Pour implémenter Kerberos avec la négociation d'information d'identification, procédez comme suit :  
  
1. Implémentez la délégation en affectant <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> à <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2. Requérez la négociation SSPI :  
  
    1. Si vous utilisez des liaisons standard, affectez `NegotiateServiceCredential` à la propriété `true`.  
  
    2. Si vous utilisez des liaisons personnalisées, affectez `AuthenticationMode` à l’attribut `Security` de l’élément `SspiNegotiated`.  
  
3. Requérez que la négociation SSPI utilise Kerberos en interdisant l'utilisation de NTLM :  
  
    1. Effectuez cette opération dans le code, à l'aide de l'instruction suivante : `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2. Vous pouvez également effectuer cette opération dans le fichier de configuration en affectant `allowNtlm` à l'attribut `false`. Cet attribut est contenu dans le [\<windows>](../../configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md) .  
  
### <a name="ntlm-protocol"></a>Protocole NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Négociation du retour de SSP à NTLM, mais NTLM est désactivé  
 La <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> propriété a la valeur `false` , ce qui amène Windows Communication Foundation (WCF) à lever un meilleur effort pour lever une exception si NTLM est utilisé. L’affectation de la valeur à cette propriété `false` peut ne pas empêcher l’envoi des informations d’identification NTLM sur le réseau.  
  
 La section suivante indique comment désactiver le retour à NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Échec d'ouverture de session NTLM  
 Les informations d'identification du client ne sont pas valides sur le service. Vérifiez que le nom d'utilisateur et le mot de passe sont correctement définis et correspondent à un compte connu sur l'ordinateur sur lequel le service s'exécute. NTLM utilise les informations d'identification spécifiées pour se connecter à l'ordinateur du service. Même si les informations d'identification sont valides sur l'ordinateur sur lequel le client s'exécute, cette ouverture de session échouera si elles ne sont pas valides sur l'ordinateur du service.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Une ouverture de session NTLM anonyme se produit, mais les ouvertures de session anonymes sont désactivées par défaut  
 Lors de la création d'un client, la propriété <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> a la valeur <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, tel qu'indiqué dans l'exemple suivant, mais par défaut, le serveur interdit les ouvertures de session anonymes. En effet, la valeur par défaut de la propriété <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> de la classe <xref:System.ServiceModel.Security.WindowsServiceCredential> est `false`.  
  
 Le code client suivant tente d'activer des ouvertures de session anonymes (notez que la propriété par défaut est `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Le code de service suivant modifie la valeur par défaut afin d'activer des ouvertures de session anonymes par le serveur.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Pour plus d’informations sur l’emprunt d’identité, consultez [délégation et emprunt d’identité](delegation-and-impersonation-with-wcf.md).  
  
 Le client s'exécute également en tant que service Windows, à l'aide du compte intégré SYSTEM.  
  
### <a name="other-problems"></a>Autres problèmes  
  
#### <a name="client-credentials-are-not-set-correctly"></a>Les informations d'identification du client ne sont pas correctement définies  
 L'authentification Windows utilise l'instance <xref:System.ServiceModel.Security.WindowsClientCredential> retournée par la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la classe <xref:System.ServiceModel.ClientBase%601>, et non pas <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Le code suivant présente un exemple incorrect.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Le code suivant présente l'exemple correct.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>SSPI n'est pas disponible  
 Les systèmes d’exploitation suivants ne prennent pas en charge l’authentification Windows lorsqu’ils sont utilisés en tant que serveur : Windows XP Édition personnelle, Windows XP Édition Media Center et les Éditions familiales de Windows Vista.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Développement et déploiement avec des identités différentes  
 Si vous développez votre application sur un ordinateur, la déployez sur un autre et utilisez différents types de compte pour vous authentifier sur chaque ordinateur, vous pouvez observer un comportement différent. Par exemple, supposons que vous développiez votre application sur un ordinateur Windows XP Professionnel à l’aide du mode d’authentification `SSPI Negotiated`. Si vous utilisez un compte d'utilisateur local pour vous authentifier, le protocole NTLM sera alors utilisé. Une fois que l'application est développée, vous déployez le service sur un ordinateur Windows Server 2003 où il s'exécute sous un compte de domaine. À ce stade, le client ne sera pas en mesure d’authentifier le service, car il utilisera Kerberos et un contrôleur de domaine.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Délégation et emprunt d'identité](delegation-and-impersonation-with-wcf.md)
- [Scénarios non pris en charge](unsupported-scenarios.md)
