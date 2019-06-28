---
title: Comportements de sécurité dans WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 53d8fedb5f562dfbc4aec566f8d0c442b255e1c9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424676"
---
# <a name="security-behaviors-in-wcf"></a>Comportements de sécurité dans WCF
Dans Windows Communication Foundation (WCF), les comportements modifient comportement au moment de l’exécution au niveau du service ou au niveau du point de terminaison. (Pour plus d’informations sur les comportements en général, consultez [spécification du comportement de Service runtime](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Comportements de sécurité* permettent de contrôler les informations d’identification, l’authentification, autorisation et les journaux d’audit. Vous pouvez les utiliser via la programmation ou la configuration. Cette rubrique se concentre sur la configuration des comportements relatifs aux fonctions de sécurité suivants :  
  
- [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), ce qui vous permet également de spécifier un point de terminaison sécurisé auquel les clients peuvent accéder pour les métadonnées.  
  
## <a name="setting-credentials-with-behaviors"></a>Définition d'informations d'identification avec des comportements  
 Utilisez le [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) et [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) pour définir les valeurs des informations d’identification pour un service ou d’un client. La configuration de liaison sous-jacente détermine si une information d’identification doit être définie. Par exemple, si le mode de sécurité a la valeur `None`, les clients et les services ne s'authentifient pas l'un l'autre et ne requièrent pas d'information d'identification d'aucun type.  
  
 En revanche, la liaison de service peut requérir un type d'informations d'identification du client. Dans ce cas, il peut s'avérer nécessaire de définir une valeur d'information d'identification à l'aide d'un comportement. (Pour plus d’informations sur les types possibles d’informations d’identification, consultez [sélection d’un Type d’informations d’identification](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Dans certains cas, par exemple lorsque des informations d'identification Windows sont utilisées pour l'authentification, l'environnement établit automatiquement la valeur d'informations d'identification réelle, et il n'est donc pas nécessaire de la définir explicitement (sauf si vous souhaitez spécifier un autre ensemble d'informations d'identification).  
  
 Toutes les informations d’identification de service sont trouvent en tant qu’éléments enfants de la [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). L'exemple suivant présente un certificat utilisé en tant qu'information d'identification du service.  
  
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
 Le [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) contient quatre éléments enfants. Les éléments et leurs utilisations sont traités dans les sections suivantes.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > élément  
 Cet élément vous permet de spécifier un certificat X.509 qui est utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message. Si vous utilisez un certificat qui est périodiquement renouvelé, son empreinte numérique change. Dans ce cas, utilisez le nom du sujet comme `X509FindType` car le certificat peut être réémis avec le même nom du sujet.  
  
 Pour plus d’informations sur l’utilisation de l’élément, consultez [Comment : Renseignez les informations d’identification Client](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certificat > de \<clientCertificate > élément  
 Utilisez le [ \<certificat >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) élément lorsque le service doit avoir le certificat du client à l’avance pour communiquer en toute sécurité avec le client. Cela se produit lors de l'utilisation du modèle de communication duplex. Dans le modèle demande-réponse plus classique, le client inclut son certificat dans la demande, que le service utilise pour sécuriser de nouveau sa réponse au client. Toutefois, le modèle de communication duplex n’a pas de demande et de réponse. Le service ne peut pas déduire le certificat du client de la communication, et par conséquent, il en a besoin à l'avance pour sécuriser les messages au client. Vous devez obtenir le certificat du client hors bande et l'indiquer à l'aide de cet élément. Pour plus d’informations sur les services duplex, consultez [Comment : Créer un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<authentification > de \<clientCertificate > élément  
 Le [ \<authentification >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) élément vous permet de personnaliser la façon dont les clients sont authentifiés. Vous pouvez affecter `CertificateValidationMode`, `None`, `ChainTrust`, `PeerOrChainTrust` ou `PeerTrust` à l'attribut `Custom`. Par défaut, le niveau est défini sur `ChainTrust`, qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant par un *autorité racine* en haut de la chaîne. C’est le mode le plus sécurisé. Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée. Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée. Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`. Vous pouvez également utiliser `Custom`. Lorsque vous utilisez `Custom`, vous devez également affecter l'assembly et le type utilisés pour valider le certificat à l'attribut `CustomCertificateValidatorType`. Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication > élément  
 Le scénario de jeton émis comporte trois étapes. Dans la première phase, un client tente d’accéder à un service est appelé un *secure token service* (STS). Le STS authentifie le client et émet ensuite un jeton pour ce dernier, généralement un jeton SAML (Security Assertions Markup Language). Le client retourne ensuite au service avec le jeton. Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client. Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé. Le [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) élément est le référentiel pour les certificats de service de jeton sécurisé ce type. Pour ajouter des certificats, utilisez le [ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Insérer un [ \<Ajouter >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pour chaque certificat, comme illustré dans l’exemple suivant.  
  
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
  
 Vous devez utiliser le [ \<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) collection dans une application fédérée qui utilise un *secure token service* (STS) qui émet `SamlSecurityToken` des jetons de sécurité. Lorsque le STS émet le jeton de sécurité, il peut spécifier l'URI des services Web pour lesquels le jeton de sécurité est prévu en ajoutant un `SamlAudienceRestrictionCondition` au jeton de sécurité. Cela permet au `SamlSecurityTokenAuthenticator` du service Web destinataire de vérifier que le jeton de sécurité émis est prévu pour ce service Web en spécifiant que ce contrôle doit arriver en effectuant les opérations suivantes :  
  
- Définir le `audienceUriMode` attribut de [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) à `Always` ou `BearerKeyOnly`.  
  
- Spécifiez le jeu d'URI valides en ajoutant les URI à cette collection. Pour ce faire, insérez un [ \<Ajouter >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) pour chaque URI  
  
 Pour plus d'informations, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : Configurer les informations d’identification sur un Service de fédération](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Autorisation d'accès aux utilisateurs CardSpace anonymes  
 L'affectation de `AllowUntrustedRsaIssuers` à l'attribut `<IssuedTokenAuthentication>` de l'élément `true` permet aux clients de présenter un jeton auto-émis signé avec une paire de clés RSA arbitraire. L’émetteur est *non approuvés* , car la clé ne comporte aucune donnée de l’émetteur associée. Un utilisateur [!INCLUDE[infocard](../../../../includes/infocard-md.md)] peut créer une carte auto-émise incluant des revendications d'identité auto-fournies. Utilisez cette fonction avec précaution. Pour utiliser cette fonctionnalité, considérez la clé publique RSA comme un mot de passe plus sécurisé qui doit être stocké dans une base de données avec un nom d’utilisateur. Avant d'autoriser l'accès d'un client au service, vérifiez la clé publique RSA présentée par celui-ci en le comparant avec celle stockée pour le nom d'utilisateur présenté. Cela suppose que vous ayez établi un processus d'inscription permettant aux utilisateurs d'enregistrer leurs noms d'utilisateur et de les associer avec les clés publiques RSA auto-émises.  
  
## <a name="client-credentials"></a>Informations d'identification du client  
 Les informations d'identification du client permettent d'authentifier le client auprès des services dans les cas où l'authentification mutuelle est requise. Vous pouvez utiliser la section pour spécifier des certificats de service pour les scénarios dans lesquels le client doit sécuriser des messages auprès d'un service à l'aide du certificat de ce dernier.  
  
 Vous pouvez également configurer un client dans le cadre d'un scénario de fédération afin d'utiliser des jetons émis par un service d'émission de jeton sécurisé ou un émetteur local de jetons. Pour plus d’informations sur les scénarios fédérés, consultez [fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Toutes les informations d’identification du client sont trouvent sous le [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), comme illustré dans le code suivant.  
  
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
```  
  
#### <a name="clientcertificate-element"></a>\<clientCertificate > élément  
 Définissez le certificat utilisé pour authentifier le client avec cet élément. Pour plus d'informations, voir [Procédure : Renseignez les informations d’identification Client](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 Cette fonction doit être activée avec Active Directory sur Windows et les services IIS (Internet Information Services). Pour plus d’informations, consultez [l’authentification Digest dans IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
#### <a name="issuedtoken-element"></a>\<issuedToken > élément  
 Le [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) contient les éléments utilisés pour configurer un émetteur local de jetons, ou les comportements utilisés avec un service de jeton de sécurité. Pour obtenir des instructions sur la configuration d’un client à utiliser un émetteur local, consultez [Comment : Configurer un émetteur Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress>  
 Spécifie une adresse de service d'émission de jeton de sécurité par défaut. Il est utilisé lorsque le <xref:System.ServiceModel.WSFederationHttpBinding> ne fournit pas d’URL pour le service de jeton de sécurité, ou lorsque l’adresse de l’émetteur d’une liaison fédérée est `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null`. Dans ce cas, vous devez configurer <xref:System.ServiceModel.Description.ClientCredentials> avec l’adresse de l’émetteur local et la liaison à utiliser pour communiquer avec celui-ci.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors>  
 Utilisez le [ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) pour ajouter des comportements de client WCF utilisés lors de la communication avec un service de jeton de sécurité. Définissez des comportements de client dans le [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) section. Pour utiliser un comportement défini, ajoutez un <`add`> élément à la `<issuerChannelBehaviors>` élément avec deux attributs. Affectez l'URL du service d'émission de jeton de sécurité à `issuerAddress`, et affectez le nom du comportement de point de terminaison défini à l'attribut `behaviorConfiguration`, tel qu'indiqué dans l'exemple suivant.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > élément  
 Cet élément vous permet de contrôler l'authentification des certificats de service.  
  
 Le [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) élément peut stocker un certificat unique utilisé lorsque le service ne spécifie aucun certificat.  
  
 Utilisez le [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) et [ \<Ajouter >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) pour définir les certificats de service qui sont associés à des services spécifiques. L'élément `<add>` inclut un attribut `targetUri` permettant d'associer le certificat au service.  
  
 Le [ \<authentification >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) élément spécifie le niveau de confiance utilisé pour authentifier les certificats. Par défaut, le niveau a la valeur « ChainTrust », laquelle spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne. C’est le mode le plus sécurisé. Vous pouvez également affecter la valeur « PeerOrChainTrust », laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée. Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée. Lorsque vous déployez un client, utilisez à la place la valeur "ChainTrust". Vous pouvez également affecter "Custom" ou "None". Pour utiliser la valeur "Custom", vous devez également définir l'attribut `CustomCertificateValidatorType` à un assembly et à un type utilisés pour valider le certificat. Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite. Pour plus d'informations, voir [Procédure : Créer un Service qui utilise un validateur de certificat personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 Le [ \<authentification >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) élément inclut un `RevocationMode` attribut qui spécifie la façon dont les certificats sont vérifiés pour révocation. La valeur par défaut est « online », laquelle indique que les certificats sont automatiquement vérifiés pour révocation. Pour plus d’informations, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 Le [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) élément contient des éléments qui affectent d’autorisation, les fournisseurs de rôles personnalisés et l’emprunt d’identité.  
  
 La classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliquée à une méthode de service. L'attribut spécifie les groupes d'utilisateurs à utiliser lors de l'autorisation d'utilisation d'une méthode protégée. La valeur par défaut est "UseWindowsGroups", laquelle spécifie qu'une identité essayant d'accéder à une ressource est recherchée dans les groupes Windows, tels que "Administrators" ou "Users". Vous pouvez également spécifier « UseAspNetRoles » pour utiliser un fournisseur de rôles personnalisé configuré sous le <`system.web` > élément, comme indiqué dans le code suivant.  
  
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
 Utilisez le [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) pour spécifier le journal à et les types d’événements pour vous connecter. Pour plus d’informations, consultez [audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```xml  
<system.serviceModel>  
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
 L'exportation des métadonnées vers des clients s'avère pratique pour les développeurs de service et de client car elle permet des téléchargements de la configuration et du code client. Pour éviter l'exposition d'un service aux utilisateurs malveillants, il est possible de sécuriser le transfert à l'aide du mécanisme HTTPS (SSL over HTTP). Pour ce faire, vous devez d'abord lier un certificat X.509 approprié à un port spécifique sur l'ordinateur qui héberge le service. (Pour plus d’informations, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Ensuite, ajoutez un [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) à la configuration du service et l’affectez le `HttpsGetEnabled` attribut `true`. Enfin, affectez l'URL du point de terminaison des métadonnées du service à l'attribut `HttpsGetUrl`, comme indiqué dans l'exemple suivant.  
  
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
- [Modèle de sécurité pour Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
