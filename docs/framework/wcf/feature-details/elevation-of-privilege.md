---
title: Élévation de privilège
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: 823b41f86080d4802f76fe69865279a7c3506238
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597408"
---
# <a name="elevation-of-privilege"></a>Élévation de privilège
L' *élévation des privilèges* résulte de l’octroi à une personne malveillante d’autorisations d’accès au-delà de celles initialement accordées. Par exemple, un intrus avec un jeu de privilèges contenant des autorisations « en lecture seule » élèvent d'une façon ou d'une autre le jeu pour inclure des autorisations « en lecture et en écriture ».  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Un STS approuvé doit signer des revendications de jeton SAML  
 Un jeton SAML (Security Assertions Markup Language) est un jeton XML générique qui est le type par défaut pour les jetons émis. Un jeton SAML peut être construit par un service de jeton de sécurité (STS, Security Token Service) que le service Web de fin approuve dans un échange standard. Les jetons SAML contiennent des revendications dans les instructions. Un intrus peut copier les revendications d'un jeton valide, créer un jeton SAML et le signer avec un émetteur différent. L'intention est de déterminer si le serveur valide des émetteurs et, si ce n'est pas le cas, d'utiliser la faille pour construire des jetons SAML qui autorisent des privilèges supérieurs à ceux prévus par un STS approuvé.  
  
 La classe <xref:System.IdentityModel.Tokens.SamlAssertion> vérifie la signature numérique contenue dans un jeton SAML, et le <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> par défaut nécessite que les jetons SAML soient signés par un certificat X.509 qui est valide lorsque le <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> de la classe <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> a la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. Le mode `ChainTrust` seul ne suffit pas pour déterminer si l'émetteur du jeton SAML est approuvé. Les services qui requièrent un modèle d’approbation plus précis peuvent soit faire appel aux stratégies d’autorisation et d’application pour vérifier l’émetteur des jeux de revendications produits par l’authentification de jetons émis, soit utiliser les paramètres de validation X.509 sur <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> pour restreindre le jeu de certificats de signature autorisés. Pour plus d’informations, consultez [gestion des revendications et autorisation avec le modèle d’identité et la](managing-claims-and-authorization-with-the-identity-model.md) [Fédération et jetons émis](federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Transfert d'identité sans un contexte de sécurité  
 Les éléments suivants s’appliquent uniquement à WinFX.  
  
 Lorsqu’une connexion est établie entre un client et un serveur, l’identité du client ne change pas, sauf dans une situation : après l’ouverture du client WCF, si toutes les conditions suivantes sont remplies :  
  
- Les procédures d’établissement d’un contexte de sécurité (à l’aide d’une session de sécurité de transport ou d’une session de sécurité de message) sont désactivées (la <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriété a la valeur `false` en cas de sécurité de message ou le transport ne peut pas établir de sessions de sécurité est utilisé dans le cas de sécurité du transport. HTTPS est un exemple de ce transport).  
  
- Vous utilisez l'authentification Windows.  
  
- Vous ne définissez pas l'information d'identification explicitement.  
  
- Vous appelez le service dans le contexte de sécurité dont l'identité a été empruntée.  
  
 Si ces conditions sont vraies, l’identité utilisée pour authentifier le client auprès du service peut changer (il se peut qu’il ne s’agit pas de l’identité empruntée mais de l’identité du processus) après l’ouverture du client WCF. Cela se produit parce que les informations d'identification Windows utilisées pour authentifier le client auprès du service sont transmises avec chaque message, et l'information d'identification utilisée pour l'authentification provient de l'identité Windows du thread actuel. Si l'identité Windows du thread actuel change (par exemple, en empruntant l'identité d'un appelant différent), l'information d'identification jointe au message et utilisé pour authentifier le client auprès du service peut changer également.  
  
 Si vous souhaitez avoir un comportement déterministe lorsque vous utilisez l'authentification Windows avec l'emprunt d'identité, vous devez définir les informations d'identification Windows explicitement ou vous devez établir un contexte de sécurité avec le service. Pour cela, utilisez une session de sécurité de message ou une session de sécurité de transport. Par exemple, le transport net.tcp peut fournir une session de sécurité de transport. En outre, vous devez utiliser uniquement une version synchrone des opérations clientes lors de l'appel du service. Si vous établissez un contexte de sécurité de message, vous ne devez pas garder la connexion au service ouverte plus longtemps que la période de renouvellement de la session configurée, étant donné que l'identité peut également changer pendant le processus de renouvellement de la session.  
  
### <a name="credentials-capture"></a>Capture des informations d'identification  
 Les éléments suivants s’appliquent à .NET Framework 3,5 et aux versions ultérieures.  
  
 Les informations d'identification utilisées par le client ou le service sont basées sur le thread de contexte actuel. Les informations d'identification sont obtenues lorsque la méthode `Open` (ou `BeginOpen`, pour les appels asynchrones) du client ou du service est appelée. Pour les classes <xref:System.ServiceModel.ServiceHost> et <xref:System.ServiceModel.ClientBase%601>, les méthodes `Open` et `BeginOpen` héritent des méthodes <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> et <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> de la classe <xref:System.ServiceModel.Channels.CommunicationObject>.  
  
> [!NOTE]
> Lors de l'utilisation de la méthode `BeginOpen`, il n'est pas possible de garantir que les informations d'identification capturées sont celles du processus qui appelle la méthode.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Les caches de jeton autorisent la relecture en utilisant des données obsolètes  
 WCF utilise la fonction LSA (autorité de sécurité locale) `LogonUser` pour authentifier les utilisateurs par nom d’utilisateur et mot de passe. Étant donné que la fonction d’ouverture de session est une opération coûteuse, WCF vous permet de mettre en cache des jetons qui représentent des utilisateurs authentifiés afin d’augmenter les performances. Le mécanisme de mise en cache enregistre les résultats de `LogonUser` pour des utilisations ultérieures. Ce mécanisme est désactivé par défaut ; pour l’activer, affectez <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> à la propriété la valeur `true` ou utilisez l' `cacheLogonTokens` attribut de [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) .  
  
 Vous pouvez définir une durée de vie pour les jetons mis en cache en affectant à la propriété <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> la valeur <xref:System.TimeSpan> ou utilisez l'attribut `cachedLogonTokenLifetime` de l'élément `userNameAuthentication` ; la valeur par défaut est 15 minutes. Notez que lors de la mise en cache d'un jeton, tout client qui présente le même nom d'utilisateur et mot de passe peut utiliser le jeton, même si le compte d'utilisateur est supprimé de Windows ou si son mot de passe a été modifié. Tant que la durée de vie n’a pas expiré et que le jeton n’a pas été supprimé du cache, WCF permet à l’utilisateur (éventuellement malveillant) de s’authentifier.  
  
 Pour atténuer ce risque : réduisez le délai d'attaque en affectant à la valeur `cachedLogonTokenLifetime` l'intervalle de temps le plus court que nécessitent vos utilisateurs.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Autorisation de jeton émis : l'expiration réinitialisée à une grande valeur  
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
  
- Le service récupère un certificat qui correspond à l'identificateur de clé du sujet, mais ce n'est pas celui que le client a projeté d'utiliser. Lorsque WCF reçoit le message et vérifie la signature, WCF mappe les informations contenues dans le certificat X. 509 involontaire à un ensemble de revendications qui sont différentes et potentiellement élevées par rapport à ce que le client attendait.  
  
 Pour atténuer ce risquez, référencez le certificat X.509 d'une autre manière, en utilisant par exemple <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Voir aussi

- [Security Considerations](security-considerations-in-wcf.md)
- [Divulgation d’informations](information-disclosure.md)
- [Déni de service](denial-of-service.md)
- [Attaques par relecture](replay-attacks.md)
- [Falsification](tampering.md)
- [Scénarios non pris en charge](unsupported-scenarios.md)
