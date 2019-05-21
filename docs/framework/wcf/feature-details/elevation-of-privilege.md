---
title: Élévation de privilège
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: df55b4fa107f3630cd259b755e0aaacdee4904ef
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960092"
---
# <a name="elevation-of-privilege"></a>Élévation de privilège
*Une élévation de privilèges* résulte de ce qui donne à un intrus d’autorisations supérieures à celles initialement accordées. Par exemple, un intrus avec un jeu de privilèges contenant des autorisations « en lecture seule » élèvent d'une façon ou d'une autre le jeu pour inclure des autorisations « en lecture et en écriture ».  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Un STS approuvé doit signer des revendications de jeton SAML  
 Un jeton SAML (Security Assertions Markup Language) est un jeton XML générique qui est le type par défaut pour les jetons émis. Un jeton SAML peut être construit par un service de jeton de sécurité (STS, Security Token Service) que le service Web de fin approuve dans un échange standard. Les jetons SAML contiennent des revendications dans les instructions. Un intrus peut copier les revendications d'un jeton valide, créer un jeton SAML et le signer avec un émetteur différent. L'intention est de déterminer si le serveur valide des émetteurs et, si ce n'est pas le cas, d'utiliser la faille pour construire des jetons SAML qui autorisent des privilèges supérieurs à ceux prévus par un STS approuvé.  
  
 La classe <xref:System.IdentityModel.Tokens.SamlAssertion> vérifie la signature numérique contenue dans un jeton SAML, et le <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> par défaut nécessite que les jetons SAML soient signés par un certificat X.509 qui est valide lorsque le <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> de la classe <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> a la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. Le mode `ChainTrust` seul ne suffit pas pour déterminer si l'émetteur du jeton SAML est approuvé. Les services qui requièrent un modèle d’approbation plus précis peuvent soit faire appel aux stratégies d’autorisation et d’application pour vérifier l’émetteur des jeux de revendications produits par l’authentification de jetons émis, soit utiliser les paramètres de validation X.509 sur <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> pour restreindre le jeu de certificats de signature autorisés. Pour plus d’informations, consultez [la gestion des revendications et autorisation avec le modèle d’identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) et [fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Transfert d'identité sans un contexte de sécurité  
 Ce qui suit s’applique uniquement aux WinFX.  
  
 Lorsqu’une connexion est établie entre un client et le serveur, l’identité du client ne change pas, sauf dans une situation : une fois le client WCF est ouvert, si toutes les conditions suivantes sont remplies :  
  
- Les procédures pour établir un contexte de sécurité (à l’aide de la sécurité de transport, session ou une session de sécurité de message) est désactivée (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriété est définie sur `false` en cas de sécurité de message ou pas en mesure d’établir la sécurité de transport sessions est utilisé en cas de sécurité de transport. HTTPS est un exemple de ce transport).  
  
- Vous utilisez l'authentification Windows.  
  
- Vous ne définissez pas l'information d'identification explicitement.  
  
- Vous appelez le service dans le contexte de sécurité dont l'identité a été empruntée.  
  
 Si ces conditions sont remplies, l’identité utilisée pour authentifier le client auprès du service peut changer (il peut être l’identité empruntée, mais l’identité du processus à la place) une fois le client WCF est ouvert. Cela se produit parce que les informations d'identification Windows utilisées pour authentifier le client auprès du service sont transmises avec chaque message, et l'information d'identification utilisée pour l'authentification provient de l'identité Windows du thread actuel. Si l'identité Windows du thread actuel change (par exemple, en empruntant l'identité d'un appelant différent), l'information d'identification jointe au message et utilisé pour authentifier le client auprès du service peut changer également.  
  
 Si vous souhaitez avoir un comportement déterministe lorsque vous utilisez l'authentification Windows avec l'emprunt d'identité, vous devez définir les informations d'identification Windows explicitement ou vous devez établir un contexte de sécurité avec le service. Pour cela, utilisez une session de sécurité de message ou une session de sécurité de transport. Par exemple, le transport net.tcp peut fournir une session de sécurité de transport. En outre, vous devez utiliser uniquement une version synchrone des opérations clientes lors de l'appel du service. Si vous établissez un contexte de sécurité de message, vous ne devez pas garder la connexion au service ouverte plus longtemps que la période de renouvellement de la session configurée, étant donné que l'identité peut également changer pendant le processus de renouvellement de la session.  
  
### <a name="credentials-capture"></a>Capture des informations d'identification  
 Les éléments suivants s'appliquent au [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], et aux versions ultérieures.  
  
 Les informations d'identification utilisées par le client ou le service sont basées sur le thread de contexte actuel. Les informations d'identification sont obtenues lorsque la méthode `Open` (ou `BeginOpen`, pour les appels asynchrones) du client ou du service est appelée. Pour les classes <xref:System.ServiceModel.ServiceHost> et <xref:System.ServiceModel.ClientBase%601>, les méthodes `Open` et `BeginOpen` héritent des méthodes <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> et <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> de la classe <xref:System.ServiceModel.Channels.CommunicationObject>.  
  
> [!NOTE]
>  Lors de l'utilisation de la méthode `BeginOpen`, il n'est pas possible de garantir que les informations d'identification capturées sont celles du processus qui appelle la méthode.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Les caches de jeton autorisent la relecture en utilisant des données obsolètes  
 WCF utilise l’autorité de sécurité locale (LSA) `LogonUser` (fonction) pour authentifier les utilisateurs par nom d’utilisateur et mot de passe. Étant donné que la fonction d’ouverture de session est une opération coûteuse, WCF permet de vous en cache des jetons qui représentent les utilisateurs authentifiés à augmenter les performances. Le mécanisme de mise en cache enregistre les résultats de `LogonUser` pour des utilisations ultérieures. Ce mécanisme est désactivé par défaut ; Pour cela, définissez la <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> propriété `true`, ou utiliser le `cacheLogonTokens` attribut de la [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Vous pouvez définir une durée de vie pour les jetons mis en cache en affectant à la propriété <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> la valeur <xref:System.TimeSpan> ou utilisez l'attribut `cachedLogonTokenLifetime` de l'élément `userNameAuthentication` ; la valeur par défaut est 15 minutes. Notez que lors de la mise en cache d'un jeton, tout client qui présente le même nom d'utilisateur et mot de passe peut utiliser le jeton, même si le compte d'utilisateur est supprimé de Windows ou si son mot de passe a été modifié. Jusqu'à ce que la durée de vie expire et que le jeton est supprimé du cache, WCF permet à l’utilisateur (et potentiellement malveillant) pour s’authentifier.  
  
 Pour atténuer ce problème : Réduire le délai d’attaque en définissant le `cachedLogonTokenLifetime` à la valeur du délai le plus court s’étendent sur vos utilisateurs ont besoin.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Émis le jeton d’autorisation : Expiration réinitialisée à valeur élevée  
 Dans certaines conditions, la propriété <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> du <xref:System.IdentityModel.Policy.AuthorizationContext> peut avoir une valeur supérieure inattendue (la valeur de champ <xref:System.DateTime.MaxValue> moins un jour, ou le 20 décembre 9999).  
  
 Cela se produit lors de l'utilisation du <xref:System.ServiceModel.WSFederationHttpBinding> et des liaisons fournies par le système qui ont un jeton émis comme type d'informations d'identification du client.  
  
 Cela se produit également lorsque vous créez des liaisons personnalisées en utilisant l’une des méthodes suivantes :  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Pour atténuer ce problème, la stratégie d'autorisation doit vérifier l'action et l'heure d'expiration de chaque stratégie d'autorisation.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Le service utilise un certificat différent que celui prévu par le client  
 Dans certaines conditions, un client peut signer numériquement un message avec un certificat X.509 et faire récupérer par le service un certificat différent de celui prévu.  
  
 Cela peut se produire dans les circonstances suivantes :  
  
- Le client signe numériquement un message à l'aide d'un certificat X.509 et ne joint pas le certificat X.509 au message, mais il se contente de le référencer à l'aide de son identificateur de clé du sujet.  
  
- L'ordinateur du service contient au moins deux certificats avec la même clé publique, mais ils contiennent des informations différentes.  
  
- Le service récupère un certificat qui correspond à l'identificateur de clé du sujet, mais ce n'est pas celui que le client a projeté d'utiliser. Lorsque WCF reçoit le message et vérifie la signature, WCF met en correspondance les informations contenues dans le certificat X.509 non conforme à un ensemble de revendications qui sont différents et potentiellement élevées des attentes du client.  
  
 Pour atténuer ce risquez, référencez le certificat X.509 d'une autre manière, en utilisant par exemple <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Voir aussi

- [Considérations relatives à la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Divulgation d’informations](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Déni de service](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Attaques par relecture](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Falsification](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Scénarios non pris en charge](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
