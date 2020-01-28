---
title: Utilisation des certificats
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
ms.openlocfilehash: e38ead0d378092af086218277fd2e85b4a6396c3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746886"
---
# <a name="working-with-certificates"></a>Utilisation des certificats

Pour programmer la sécurité relative à WCF (Windows Communication Foundation), les certificats numériques X.509 sont couramment utilisés pour authentifier les clients et les serveurs, ainsi que pour chiffrer et signer numériquement les messages. Cette rubrique décrit brièvement les fonctionnalités des certificats numériques X.509 et leur utilisation dans WCF. Elle inclut également des liens vers les rubriques qui présentent ces concepts de manière plus détaillée, ou qui montrent comment effectuer les tâches courantes à l’aide de WCF et des certificats.

En bref, un certificat numérique fait partie d’une infrastructure *PKI* (infrastructure à clé publique). Il s’agit d’un système composé de certificats numériques, d’autorités de certification et d’autorités d’inscription qui permettent de vérifier et d’authentifier la validité de chaque partie impliquée dans une transaction électronique grâce à l’utilisation d’un chiffrement à clé publique. Une autorité de certification émet des certificats qui comportent un ensemble de champs contenant des données telles que le *sujet* (entité pour laquelle le certificat est émis), les dates de validité (période de validité du certificat), l’émetteur (entité qui a émis le certificat) et la clé publique. Dans WCF, chacune de ces propriétés est traitée en tant que <xref:System.IdentityModel.Claims.Claim>, et chaque revendication est divisée en deux types : identité et droit. Pour plus d’informations sur les certificats X.509, consultez [Certificats de clé publique X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Pour plus d’informations sur les revendications et la notion d’autorisation dans WCF, consultez [Gestion des revendications et autorisation avec le modèle d’identité](managing-claims-and-authorization-with-the-identity-model.md). Pour plus d’informations sur l’implémentation d’une infrastructure à clé publique, consultez [Enterprise PKI with Windows Server 2012 R2 Active Directory Certificate Services](https://docs.microsoft.com/archive/blogs/yungchou/enterprise-pki-with-windows-server-2012-r2-active-directory-certificate-services-part-1-of-2).

La principale fonction d’un certificat est d’authentifier l’identité du propriétaire du certificat auprès des autres parties. Un certificat contient la *clé publique* du propriétaire, alors que le propriétaire conserve la clé privée. Les clés publiques peuvent être utilisées pour chiffrer les messages envoyés au propriétaire du certificat. Cependant, seul le propriétaire de la clé privée pourra déchiffrer ces messages.

Les certificats doivent être émis par une autorité de certification, c'est-à-dire le plus souvent par une partie tierce. Les domaines Windows intègrent une autorité de certification pouvant être utilisée afin d'émettre des certificats pour les ordinateurs figurant sur ces domaines.

## <a name="viewing-certificates"></a>Affichage des certificats

Si vous souhaitez utiliser des certificats, vous devrez souvent les afficher et examiner leurs propriétés au préalable. Pour ce faire, il vous suffit d'utiliser l'outil enfichable MMC (Microsoft Management Console). Pour plus d’informations, consultez [Guide pratique pour afficher des certificats à l’aide du composant logiciel enfichable MMC](how-to-view-certificates-with-the-mmc-snap-in.md).

## <a name="certificate-stores"></a>Magasin de certificats

Les certificats sont stockés dans des magasins. Deux emplacements de magasin majeurs existent et sont divisés en sous-magasins. Si vous disposez des droits administrateur sur un ordinateur, vous pouvez afficher ces deux principaux magasins à l'aide de l'outil enfichable MMC. Dans le cas contraire, vous pouvez uniquement afficher le magasin de l'utilisateur en cours.

- **Magasin de la machine locale**. Contient les certificats accessibles par les processus de l’ordinateur, tels que ASP.NET. Utilisez cet emplacement pour y stocker les certificats qui authentifient les serveurs auprès des clients.

- **Magasin de l’utilisateur actuel**. Les applications interactives stockent en principe les certificats à cet emplacement pour l'utilisateur en train d'utiliser l'ordinateur. Si vous créer des applications clientes, c'est également l'emplacement que vous utiliserez en principe pour stocker les certificats qui authentifient les utilisateurs auprès des services.

Ces deux magasins sont divisés en sous-magasins. Les plus importants d’entre eux pour la programmation avec WCF sont notamment :

- **Autorités de certification racine approuvées**. Vous pouvez utiliser les certificats stockés dans ce magasin pour créer une chaîne de certificats, dont l'origine remontera à un certificat d'autorité de certification figurant dans ce magasin.

  > [!IMPORTANT]
  > L'ordinateur local approuve de manière implicite tous les certificats figurant dans ce magasin, même si ces certificats n'émanent pas d'une autorité de certification tierce approuvée. C'est pourquoi ne stockez pas de certificats dans ce magasin, à moins qu'il ne s'agisse de certificats publiés par des émetteurs dans lesquels vous entièrement confiance et à moins d'avoir pleinement conscience des conséquences d'un tel stockage.

- **Personnel**. Ce magasin est utilisé pour stocker les certificats associés à l'utilisateur d'un ordinateur. Ce magasin est en principe utilisé pour stocker les certificats publiés par l'un des certificats d'autorité de certification stockés dans le magasin Autorités de certification racine approuvées. Les certificats stockés dans ce magasin peuvent également s'être auto-publiés et avoir été approuvés par une application.

Pour plus d’informations sur les magasins de certificats, consultez [Magasins de certificats](/windows/desktop/secauthn/certificate-stores).

### <a name="selecting-a-store"></a>Sélection d'un magasin

La sélection d'un magasin pour y stocker un certificat dépend de la manière dont un client ou service s'exécutent ainsi que de l'instant où ils s'exécutent. Les règles générales suivantes s'appliquent :

- Si le service WCF est hébergé dans un service Windows, utilisez le magasin **machine locale**. Remarque : des droits administrateur sont requis pour pouvoir stocker les certificats dans le magasin de l'ordinateur local.

- Si le service ou le client est une application qui s’exécute sous un compte d’utilisateur, utilisez le magasin **utilisateur actuel**.

### <a name="accessing-stores"></a>Accès aux magasins

Les magasins sont protégés par des listes de contrôle d’accès à l’instar des dossiers figurant sur un ordinateur. Lorsque vous créez un service hébergé par Internet Information Services (IIS), le processus ASP.NET s’exécute sous le compte ASP.NET. Ce compte doit avoir accès au magasin contenant les certificats utilisés par le service considéré. Chacun des principaux magasins est protégé par une liste d'accès par défaut, mais cette liste peut être modifiée. Si vous créez un rôle distinct pour l'accès à un magasin donné, vous devez accorder à ce rôle des droits d'accès. Pour apprendre à modifier la liste d’accès à l’aide de l’outil WinHttpCertConfig.exe, consultez [Guide pratique pour créer des certificats temporaires à utiliser au cours du développement](how-to-create-temporary-certificates-for-use-during-development.md).

## <a name="chain-trust-and-certificate-authorities"></a>Chaîne d'approbation et autorités de certification

Les certificats sont créés selone une hiérarchie où chaque certificat individuel est lié à l'autorité de certification qui l'a émis. Ce lien renvoie au certificat de l'autorité de certification. Le certificat de l’autorité de certification est ensuite lié à l’autorité de certification qui a émis le certificat de l’autorité de certification d’origine. Ce processus se répète jusqu'à ce que le certificat de l'autorité de certification racine soit atteint. Le certificat de l'autorité de certification racine est approuvé de manière inhérente.

Les certificats numériques sont utilisés pour authentifier une entité en s’appuyant sur cette hiérarchie, également appelée *chaîne de confiance*. Vous pouvez afficher n’importe quelle chaîne de certificat à l’aide du composant logiciel enfichable MMC en double-cliquant sur un certificat, puis en cliquant sur l’onglet **chemin d’accès du certificat** . Pour plus d’informations sur l’importation de chaînes de certificats pour une autorité de certification, consultez Guide pratique [pour spécifier la chaîne de certificats d’autorité de certification utilisée pour vérifier les signatures](specify-the-certificate-authority-chain-verify-signatures-wcf.md).

> [!NOTE]
> Le statut d'autorité racine approuvée peut être attribué à tout émetteur. Il suffit pour ce faire de placer le certificat de cet émetteur dans le magasin Autorités de certification racine approuvées.

### <a name="disabling-chain-trust"></a>Désactivation des chaînes d'approbation

Lorsque vous créez un nouveau service, il est possible que vous utilisiez un certificat non émis par un certificat racine approuvé ou que le certificat émetteur lui-même ne figure pas dans le magasin Autorités de certification racine approuvées. Vous pouvez désactiver le mécanisme assurant la vérification de la chaîne d'approbation d'un certificat uniquement à des fins de développement. Pour ce faire, affectez à la propriété `CertificateValidationMode``PeerTrust` ou `PeerOrChainTrust`. L'un et l'autre des modes ci-dessus permettent de spécifier que le certificat doit s'auto-publier (approbation homologue) ou faire partie d'une chaîne d'approbation. Vous pouvez définir la propriété de n'importe laquelle des classes suivantes.

|Classe|Les|
|-----------|--------------|
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|

Vous pouvez également définir la propriété à l'aide de la configuration. Les éléments suivants sont utilisés pour spécifier le mode de validation :

- [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)

- [\<peerAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)

- [\<messageSenderAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)

## <a name="custom-authentication"></a>Authentification personnalisée

La propriété `CertificateValidationMode` vous permet également de personnaliser les modalités d'authentification des certificats. Par défaut, le niveau a la valeur `ChainTrust`. Pour utiliser la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, vous devez également affecter à l'attribut `CustomCertificateValidatorType` l'assembly et le type utilisés pour valider le certificat. Pour créer un validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.

Lorsque vous créez un authentificateur personnalisé, la méthode la plus importante à substituer correspond à la méthode <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A>. Pour obtenir un exemple d’authentification personnalisée, consultez [Validateur de certificat X.509](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md). Pour plus d’informations, consultez [Informations d’identification personnalisées et validation d’informations d’identification](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).

## <a name="using-the-powershell-new-selfsignedcertificate-cmdlet-to-build-a-certificate-chain"></a>Utilisation de l’applet de commande PowerShell New-SelfSignedCertificate pour créer une chaîne de certificats

L’applet de commande PowerShell New-SelfSignedCertificate crée des certificats X. 509 et des paires clé privée/clé publique. Vous pouvez enregistre les clés privées sur votre disque, puis les utiliser pour émettre et signer de nouveaux certificats, instaurant ainsi une hiérarchie de certificats sous forme de chaîne. L’applet de commande est destinée à être utilisée uniquement comme une aide lors du développement de services et ne doit jamais être utilisée pour créer des certificats pour le déploiement réel. Lors du développement d’un service WCF, procédez comme suit pour générer une chaîne de confiance avec l’applet de commande New-SelfSignedCertificate.

#### <a name="to-build-a-chain-of-trust-with-the-new-selfsignedcertificate-cmdlet"></a>Pour générer une chaîne d’approbation avec l’applet de commande New-SelfSignedCertificate

1. Créez un certificat d’autorité racine temporaire (auto-signé) à l’aide de l’applet de commande New-SelfSignedCertificate. Enregistrez la clé privée sur le disque.

2. Utilisez ce nouveau certificat pour émettre un autre certificat contenant la clé publique.

3. Importez le certificat d'autorité racine dans le magasin Autorités de certification racine approuvées.

4. Pour obtenir des instructions pas à pas, consultez [Guide pratique pour créer des certificats temporaires à utiliser au cours du développement](how-to-create-temporary-certificates-for-use-during-development.md).

## <a name="which-certificate-to-use"></a>Quel certificat utiliser ?

Parmi les questions les plus fréquemment posées concernant les certificats figurent notamment : quel certificat choisir et pourquoi ? La réponse à ces questions n'est pas la même que vous programmiez un service ou un client. Les informations ci-dessous contiennent des directives générales et n'offrent pas une réponse exhaustive à ces questions.

### <a name="service-certificates"></a>Certificats de service

La principale tâche des certificats de service consiste à authentifier le serveur auprès des clients. Quand un client authentifie un serveur, il compare d’abord la valeur du champ **Sujet** à celle de l’URI (Uniform Resource Identifier) utilisé pour contacter le service : les DNS respectifs doivent correspondre. Par exemple, si l’URI du service est `http://www.contoso.com/endpoint/`, le champ **objet** doit également contenir la valeur `www.contoso.com`.

Remarque : ce champ peut contenir plusieurs valeurs, chacune préfixée par une initialisation spécifiant la valeur. Le plus souvent, l’initialisation est « CN » pour le nom commun, par exemple, `CN = www.contoso.com`. Il est également possible que le champ **Sujet** soit vide. Dans ce cas, le champ **Autre nom de l’objet** peut contenir la valeur **Nom DNS**.

Notez également que le champ **Rôles prévus** du certificat doit contenir une valeur appropriée, par exemple « Authentification du serveur » ou « Authentification du client ».

### <a name="client-certificates"></a>Certificats clients

Les certificats de client ne sont en principe pas publiés par une autorité de certification tierce. Le magasin personnel de l'utilisateur en cours contient en principe des certificats qui y sont stockés par l'autorité racine, le rôle prévu étant « Authentification de client ». Le client peut utiliser ce genre de certificat lorsque l'authentification mutuelle requise.

## <a name="online-revocation-and-offline-revocation"></a>Révocations en ligne et hors ligne

### <a name="certificate-validity"></a>Validité des certificats

Chaque certificat est valide uniquement pour une période de temps donnée, appelée *période de validité*. Cette période est définie par les champs **Valide à partir du** et **Valide jusqu’au** d’un certificat X.509. Au cours de l'authentification, le certificat est contrôlé afin de vérifier que sa période de validité n'est pas échue.

### <a name="certificate-revocation-list"></a>Liste de révocation des certificats

L'autorité de certification peut à tout moment révoquer un certificat tant que sa période de validité n'est pas échue. Une telle révocation peut avoir lieu pour plusieurs raisons, notamment lorsque la clé privée du certificat est compromise.

En cas de révocation, toutes les chaînes descendant du certificat révoqué ne sont plus considérées comme valables et ne sont plus approuvées pendant les procédures d'authentification. Pour savoir quels certificats sont révoqués, chaque émetteur publie une *CRL* (liste de révocation de certificats) horodatée et datée. Cette liste peut être consultée à l'aide des révocations en ligne ou hors connexion en affectant à la propriété `RevocationMode` ou `DefaultRevocationMode` de l'une des classes suivantes l'une des valeurs d'énumération <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> : <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> et les classes <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>. La valeur par défaut de toutes les propriétés est `Online`.

Vous pouvez également définir le mode dans la configuration à l’aide de l’attribut `revocationMode` de l’élément [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (de [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) et de l’élément [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (de [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).

## <a name="the-setcertificate-method"></a>Méthode SetCertificate

Dans WCF, vous devez souvent spécifier un certificat ou un ensemble de certificats qu’un service ou un client doit utiliser pour authentifier, chiffrer ou signer numériquement un message. Pour ce faire, il vous suffit de rédiger un programme à l'aide de la méthode `SetCertificate` des diverses classes représentant les certificats X.509. Les classes suivantes utilisent la méthode `SetCertificate` pour spécifier un certificat.

|Classe|Méthode|
|-----------|------------|
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|

La méthode `SetCertificate` désigne un emplacement de magasin et y stocke un type « trouver » (paramètre `x509FindType`) qui spécifie un champ de certificat et la valeur de ce champ. Par exemple, le code suivant crée une instance de <xref:System.ServiceModel.ServiceHost> et définit le certificat de service utilisé pour authentifier le service auprès des clients à l’aide de la méthode `SetCertificate`.

[!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
[!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]

### <a name="multiple-certificates-with-the-same-value"></a>Plusieurs certificats ayant la même valeur

Un magasin peut contenir plusieurs certificats ayant le même nom de sujet. En d’autres termes, si vous spécifiez que `x509FindType` a la valeur <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> ou <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>, et si plusieurs certificats ont la même valeur, une exception est levée, car il est impossible de distinguer le certificat nécessaire. Vous pouvez résoudre ce problème en affectant à `x509FindType` la valeur <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. Le champ d'empreinte contient une valeur unique qui peut être utilisée afin de trouver un certificat particulier figurant dans un magasin. Cette solution présente cependant un inconvénient : si le certificat a été révoqué ou renouvelé, la méthode `SetCertificate` échouera, l'empreinte du certificat n'existant plus. Si le certificat n'est plus valable, l'authentification échouera également. Pour résoudre ce problème, vous pouvez affecter au paramètre `x590FindType` la valeur <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName>, puis spécifier le nom de l'émetteur. Si aucun émetteur n'est requis, vous pouvez également lui affecter l'une des autres valeurs d'énumération <xref:System.Security.Cryptography.X509Certificates.X509FindType> telles que <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.

## <a name="certificates-in-configuration"></a>Certificats dans la configuration

Vous pouvez également définir des certificats à l'aide de la configuration. Si vous créez un service, les informations d’identification, notamment les certificats, sont spécifiées sous [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Quand vous programmez un client, les certificats sont spécifiés sous [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).

## <a name="mapping-a-certificate-to-a-user-account"></a>Mappage d'un certificat à un compte utilisateur

Les services IIS et Active Directory proposent une fonctionnalité qui permet de mapper un certificat à un compte utilisateur Windows. Pour plus d’informations sur la fonctionnalité, consultez [Mapper des certificats aux comptes d’utilisateurs](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc736706(v=ws.10)).

Pour plus d’informations sur l’utilisation du mappage Active Directory, consultez [Mappage des certificats clients à l’aide du mappage du service d’annuaire](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc758484(v=ws.10)).

Lorsque cette fonctionnalité est activée, vous pouvez affecter à la propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> de la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> la valeur `true`. Dans la configuration, vous pouvez affecter à l’attribut `mapClientCertificateToWindowsAccount` de l’élément [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) la valeur `true`, comme indiqué dans le code suivant.

```xml
<serviceBehaviors>
 <behavior name="MappingBehavior">
  <serviceCredentials>
   <clientCertificate>
    <authentication certificateValidationMode="None" mapClientCertificateToWindowsAccount="true" />
   </clientCertificate>
  </serviceCredentials>
 </behavior>
</serviceBehaviors>
```

Le mappage d'un certificat X.509 au jeton représentant le compte utilisateur Windows est considéré comme un rehaussement des droits de ce compte. Une fois mappé, le jeton Windows peut en effet être utilisé pour accéder à des ressources protégées. C'est pourquoi la stratégie de domaine spécifie que le certificat X.509 doit être conforme aux règles qu'elle contient avant de pouvoir être mappé. Le package de sécurité *SChannel* applique cette exigence.

Lorsque vous utilisez .NET Framework 3,5 ou versions ultérieures, WCF garantit que le certificat est conforme à la stratégie de domaine avant d’être mappé à un compte Windows.

Dans la première version de WCF, le mappage est effectué sans prise en compte de la stratégie de domaine. Par conséquent, avec d'anciennes applications habituées à s'exécuter sous la première version, il est possible que le mappage échoue si la fonctionnalité de mappage est activée et si le certificat X.509 n'est pas conforme à la stratégie de domaine.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Security>
- <xref:System.ServiceModel>
- <xref:System.Security.Cryptography.X509Certificates.X509FindType>
- [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
