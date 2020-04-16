---
title: Comportements de sécurité dans WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 9f96abac0f5f32279c5579dd01c3dd7f2dc1786c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464049"
---
# <a name="security-behaviors-in-wcf"></a>Comportements de sécurité dans WCF
Dans Windows Communication Foundation (WCF), les comportements modifient le comportement en temps de course au niveau du service ou au niveau du point de terminaison. (Pour plus d’informations sur les comportements en général, voir [Specifying Service Run-Time Behavior](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Les comportements de sécurité* permettent le contrôle des informations d’identification, de l’authentification, de l’autorisation et de l’audit des journaux. Vous pouvez les utiliser via la programmation ou la configuration. Cette rubrique se concentre sur la configuration des comportements relatifs aux fonctions de sécurité suivants :  
  
- serviceCredentials>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
- clientCredentials>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
  
- serviceAuthorization>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)  
  
- serviceSecurityAudit>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
  
- serviceMetadata>, ce qui vous permet également de spécifier un critère d’évaluation sécurisé auquel les clients peuvent accéder pour les métadonnées. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)  
  
## <a name="setting-credentials-with-behaviors"></a>Définition d'informations d'identification avec des comportements  
 Utilisez le [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) et [ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) pour définir les valeurs d’identification pour un service ou un client. La configuration de liaison sous-jacente détermine si une information d’identification doit être définie. Par exemple, si le mode de sécurité a la valeur `None`, les clients et les services ne s'authentifient pas l'un l'autre et ne requièrent pas d'information d'identification d'aucun type.  
  
 En revanche, la liaison de service peut requérir un type d'informations d'identification du client. Dans ce cas, il peut s'avérer nécessaire de définir une valeur d'information d'identification à l'aide d'un comportement. (Pour plus d’informations sur les types possibles d’informations d’identification, voir [Sélection d’un type d’identification](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Dans certains cas, comme lorsque les informations d’identification Windows sont utilisées pour authentifier, l’environnement établit automatiquement la valeur réelle d’identification et vous n’avez pas besoin de définir explicitement la valeur d’identification (sauf si vous souhaitez spécifier un ensemble différent d’informations d’identification).  
  
 Toutes les informations d’identification de service sont trouvées comme éléments d’enfant du [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). L'exemple suivant présente un certificat utilisé en tant qu'information d'identification du service.  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a>Informations d'identification du service  
 Le [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) contient quatre éléments pour enfants. Les éléments et leurs utilisations sont traités dans les sections suivantes.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate> Element  
 Cet élément vous permet de spécifier un certificat X.509 qui est utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message. Si vous utilisez un certificat qui est périodiquement renouvelé, son empreinte numérique change. Dans ce cas, utilisez le nom du sujet comme `X509FindType` car le certificat peut être réémis avec le même nom du sujet.  
  
 Pour plus d’informations sur l’utilisation de l’élément, voir [comment : Spécifier les valeurs d’identification des clients](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certificat> de \<clientCertificate> Element  
 Utilisez [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) le certificat>élément lorsque le service doit avoir le certificat du client à l’avance pour communiquer en toute sécurité avec le client. Cela se produit lors de l'utilisation du modèle de communication duplex. Dans le modèle demande-réponse plus classique, le client inclut son certificat dans la demande, que le service utilise pour sécuriser de nouveau sa réponse au client. Toutefois, le modèle de communication duplex n’a pas de demande et de réponse. Le service ne peut pas déduire le certificat du client de la communication, et par conséquent, il en a besoin à l'avance pour sécuriser les messages au client. Vous devez obtenir le certificat du client hors bande et l'indiquer à l'aide de cet élément. Pour plus d’informations sur les services en duplex, voir [Comment : Créer un contrat En duplex.](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
  
### <a name="authentication-of-clientcertificate-element"></a>\<authentification> \<du clientCertificate> Element  
 [ \<L’authentification>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) élément vous permet de personnaliser la façon dont les clients sont authentifiés. Vous pouvez affecter `CertificateValidationMode`, `None`, `ChainTrust`, `PeerOrChainTrust` ou `PeerTrust` à l'attribut `Custom`. Par défaut, le niveau `ChainTrust`est fixé à , ce qui spécifie que chaque certificat doit être trouvé dans une hiérarchie de certificats se terminant par une *autorité racine* au sommet de la chaîne. C’est le mode le plus sécurisé. Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée. Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée. Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`. Vous pouvez également utiliser `Custom`. Lorsque vous utilisez `Custom`, vous devez également affecter l'assembly et le type utilisés pour valider le certificat à l'attribut `CustomCertificateValidatorType`. Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.  
  
### <a name="issuedtokenauthentication-element"></a>\<publiéTokenAuthentication> Element  
 Le scénario de jeton émis comporte trois étapes. Dans la première étape, un client qui tente d’accéder à un service est dirigé vers un *service de jetons sécurisé* (STS). Le STS authentifie le client et émet ensuite un jeton pour ce dernier, généralement un jeton SAML (Security Assertions Markup Language). Le client retourne ensuite au service avec le jeton. Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client. Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé. [ \<L’élément de>d’auteur délivré](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) est le référentiel pour un tel certificat de service de jetons sécurisé. Pour ajouter des certificats, utilisez les [ \<>connus ](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Insérez un [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) supplémentaire pour chaque certificat, comme indiqué dans l’exemple suivant.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé. Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.  
  
 Vous devez utiliser la `SamlSecurityToken` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) collection de>permise dans une application fédérée qui utilise un service de *jetons sécurisé* (STS) qui émet des jetons de sécurité. Lorsque le STS émet le jeton de sécurité, il peut spécifier l'URI des services Web pour lesquels le jeton de sécurité est prévu en ajoutant un `SamlAudienceRestrictionCondition` au jeton de sécurité. Cela permet au `SamlSecurityTokenAuthenticator` du service Web destinataire de vérifier que le jeton de sécurité émis est prévu pour ce service Web en spécifiant que ce contrôle doit arriver en effectuant les opérations suivantes :  
  
- Définissez `audienceUriMode` l’attribut de [ \<l'>d’auteur de l’aéroken](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) `Always` délivrée ou `BearerKeyOnly`.  
  
- Spécifiez le jeu d'URI valides en ajoutant les URI à cette collection. Pour ce faire, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) insérer un ajout>pour chaque URI  
  
 Pour plus d’informations, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Pour plus d’informations sur l’utilisation de cet élément de configuration, voir [Comment configurer les informations d’identification sur un service de fédération](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Autorisation d'accès aux utilisateurs CardSpace anonymes  
 L'affectation de `AllowUntrustedRsaIssuers` à l'attribut `<IssuedTokenAuthentication>` de l'élément `true` permet aux clients de présenter un jeton auto-émis signé avec une paire de clés RSA arbitraire. L’émetteur *n’est pas fiable* parce que la clé n’a pas de données d’émetteurs qui lui sont associées. Un utilisateur de CardSpace peut créer une carte auto-émise qui inclut des réclamations d’identité auto-fournies. Utilisez cette fonction avec précaution. Pour utiliser cette fonctionnalité, considérez la clé publique RSA comme un mot de passe plus sécurisé qui doit être stocké dans une base de données avec un nom d’utilisateur. Avant d'autoriser l'accès d'un client au service, vérifiez la clé publique RSA présentée par celui-ci en le comparant avec celle stockée pour le nom d'utilisateur présenté. Cela suppose que vous ayez établi un processus d'inscription permettant aux utilisateurs d'enregistrer leurs noms d'utilisateur et de les associer avec les clés publiques RSA auto-émises.  
  
## <a name="client-credentials"></a>Informations d’identification du client  
 Les informations d'identification du client permettent d'authentifier le client auprès des services dans les cas où l'authentification mutuelle est requise. Vous pouvez utiliser la section pour spécifier des certificats de service pour les scénarios dans lesquels le client doit sécuriser des messages auprès d'un service à l'aide du certificat de ce dernier.  
  
 Vous pouvez également configurer un client dans le cadre d'un scénario de fédération afin d'utiliser des jetons émis par un service d'émission de jeton sécurisé ou un émetteur local de jetons. Pour plus d’informations sur les scénarios fédéraux, voir [Fédération et Jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Tous les titres de compétences du client se trouvent sous le [ \<point de terminaisonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), comme indiqué dans le code suivant.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
#### <a name="clientcertificate-element"></a>\<clientCertificate> Element  
 Définissez le certificat utilisé pour authentifier le client avec cet élément. Pour plus d’informations, voir [Comment : Spécifier les valeurs d’identification des clients](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 Cette fonction doit être activée avec Active Directory sur Windows et les services IIS (Internet Information Services). Pour plus d’informations, voir [Digest Authentication in IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<publiéToken> Element  
 Le [ \<>de jet émis](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) contient les éléments utilisés pour configurer un émetteur local de jetons, ou les comportements utilisés avec un service de jetons de sécurité. Pour obtenir des instructions sur la configuration d’un client pour utiliser un émetteur local, voir [comment : Configurer un émetteur local.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress>  
 Spécifie une adresse de service d'émission de jeton de sécurité par défaut. Ceci est utilisé <xref:System.ServiceModel.WSFederationHttpBinding> lorsque le ne fournit pas une URL pour le service de jetons `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null`de sécurité, ou lorsque l’adresse de l’émetteur d’une liaison fédérée est ou . Dans ce cas, vous devez configurer <xref:System.ServiceModel.Description.ClientCredentials> avec l’adresse de l’émetteur local et la liaison à utiliser pour communiquer avec celui-ci.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors>  
 Utilisez [ \<l’émetteurChannelBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) pour ajouter les comportements des clients WCF utilisés lors de la communication avec un service de jetons de sécurité. Définir les comportements des clients dans la [ \<section endpointBehaviors>.](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) Pour utiliser un comportement défini, ajoutez `add` un <> `<issuerChannelBehaviors>` élément à l’élément avec deux attributs. Affectez l'URL du service d'émission de jeton de sécurité à `issuerAddress`, et affectez le nom du comportement de point de terminaison défini à l'attribut `behaviorConfiguration`, tel qu'indiqué dans l'exemple suivant.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
      </issuerChannelBehaviors>  
   </issuedToken>  
</clientCredentials>
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate> Element  
 Cet élément vous permet de contrôler l'authentification des certificats de service.  
  
 [ \<L’élément de>par défaut](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) peut stocker un seul certificat utilisé lorsque le service ne précise aucun certificat.  
  
 Utilisez les [ \<>de scopedCertificates](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) et [ \<ajoutez>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) pour définir les certificats de service qui sont associés à des services spécifiques. L'élément `<add>` inclut un attribut `targetUri` permettant d'associer le certificat au service.  
  
 [ \<L’authentification>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) élément spécifie le niveau de confiance utilisé pour authentifier les certificats. Par défaut, le niveau a la valeur « ChainTrust », laquelle spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne. C’est le mode le plus sécurisé. Vous pouvez également affecter la valeur « PeerOrChainTrust », laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée. Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée. Lorsque vous déployez un client, utilisez à la place la valeur "ChainTrust". Vous pouvez également affecter "Custom" ou "None". Pour utiliser la valeur "Custom", vous devez également définir l'attribut `CustomCertificateValidatorType` à un assembly et à un type utilisés pour valider le certificat. Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite. Pour plus d’informations, voir [Comment : Créer un service qui utilise un validateur de certificat personnalisé.](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
  
 [ \<L’authentification>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) élément `RevocationMode` comprend un attribut qui précise comment les certificats sont vérifiés pour la révocation. La valeur par défaut est « online », laquelle indique que les certificats sont automatiquement vérifiés pour révocation. Pour plus d’informations, voir [Travailler avec des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 Le [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) élément contient des éléments qui affectent l’autorisation, les fournisseurs de rôles personnalisés et l’usurpation d’identité.  
  
 La classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliquée à une méthode de service. L'attribut spécifie les groupes d'utilisateurs à utiliser lors de l'autorisation d'utilisation d'une méthode protégée. La valeur par défaut est "UseWindowsGroups", laquelle spécifie qu'une identité essayant d'accéder à une ressource est recherchée dans les groupes Windows, tels que "Administrators" ou "Users". Vous pouvez également spécifier "UseAspNetRoles" pour utiliser un fournisseur `system.web` de rôle personnalisé qui est configuré sous le <> élément, comme indiqué dans le code suivant.  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add
          name="SqlProvider"
          type="System.Web.Security.SqlMembershipProvider"
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 Le code suivant présente le `roleProviderName` utilisé avec l'attribut `principalPermissionMode`.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Configuration des audits de sécurité  
 Utilisez le [ \<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) pour spécifier le journal écrit et quels types d’événements enregistrer. Pour plus d’informations, voir [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```xml  
<behaviors>
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"
             messageAuthenticationAuditLevel="Success" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a>Échange de métadonnées sécurisé  
 L'exportation des métadonnées vers des clients s'avère pratique pour les développeurs de service et de client car elle permet des téléchargements de la configuration et du code client. Pour éviter l'exposition d'un service aux utilisateurs malveillants, il est possible de sécuriser le transfert à l'aide du mécanisme HTTPS (SSL over HTTP). Pour ce faire, vous devez d'abord lier un certificat X.509 approprié à un port spécifique sur l'ordinateur qui héberge le service. (Pour plus d’informations, voir [Travailler avec des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Deuxièmement, ajoutez un `HttpsGetEnabled` `true` [ \<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) à la configuration du service et définissez l’attribut à . Enfin, affectez l'URL du point de terminaison des métadonnées du service à l'attribut `HttpsGetUrl`, comme indiqué dans l'exemple suivant.  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
