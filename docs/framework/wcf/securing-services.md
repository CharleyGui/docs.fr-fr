---
title: Sécurisation de services
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
ms.openlocfilehash: f2a8e10aaf9c1dbe3065344963fcc712776cd2db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242225"
---
# <a name="securing-services"></a>Sécurisation de services

La sécurité d’un service Windows Communication Foundation (WCF) est constituée de deux exigences principales : la sécurité de transfert et l’autorisation. (Une troisième exigence, l’audit des événements de sécurité, est décrite dans [audit](./feature-details/auditing-security-events.md).) En bref, la sécurité de transfert comprend l’authentification (vérification de l’identité du service et du client), de la confidentialité (chiffrement des messages) et de l’intégrité (signature numérique pour détecter la falsification). L'autorisation est le contrôle d'accès aux ressources, par exemple en autorisant uniquement les utilisateurs privilégiés à lire un fichier. À l’aide des fonctionnalités de WCF, les deux exigences principales sont facilement implémentées.  
  
 À l’exception de la <xref:System.ServiceModel.BasicHttpBinding> classe (ou de l' [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) élément dans la configuration), la sécurité de transfert est activée par défaut pour toutes les liaisons prédéfinies. Les rubriques de cette section présentent deux scénarios de base : implémentation de la sécurité de transfert et de l'autorisation sur un service intranet hébergé sur IIS (Internet Information Services) et implémentation de la sécurité de transfert et de l'autorisation sur un service hébergé sur IIS.  
  
> [!NOTE]
> Windows XP Édition Familiale ne prend pas en charge l'authentification Windows. Par conséquent, vous ne devez pas exécuter un service sur ce système.  
  
## <a name="security-basics"></a>Concepts de base de la sécurité  

 La sécurité repose sur des *informations d'identification*. Les informations d'identification prouvent qu'une entité est bien celle qu'elle prétend être. (Une *entité* peut être une personne, un processus logiciel, une société ou tout ce qui peut être autorisé.) Par exemple, un client d’un service fait une *revendication* d' *identité* et les informations d’identification prouvent cette revendication d’une certaine manière. Dans un scénario typique, un échange d'informations d'identification se produit. Tout d'abord, un service fait une revendication de son identité et la prouve au client avec des informations d'identification. À son tour, le client fait une revendication d'identité et présente des informations d'identification au service. Si les deux partis approuvent les informations d'identification de l'autre parti, un nouveau *contexte de sécurité* peut être établi dans lequel tous les messages sont échangés en toute confidentialité et sont signés afin de protéger leur intégrité. Une fois que la service a établi l'identité du client, il peut mettre en correspondre les revendications des informations d'identification à un *rôle* ou une *appartenance* à un groupe. Dans les deux cas, à l'aide du rôle ou du groupe auquel le client appartient, le service *autorise* le client à exécuter un jeu limité d'opérations qui dépend des privilèges du rôle ou du groupe.  
  
## <a name="windows-security-mechanisms"></a>Mécanismes de la sécurité Windows  

 Si l'ordinateur client et l'ordinateur de service se trouvent tous deux dans un domaine Windows qui requiert que tous deux se connectent au réseau, les informations d'identification sont fournies par l'infrastructure Windows. Dans ce cas, les informations d'identification sont établies lorsqu'un utilisateur se connecte au réseau. Chaque utilisateur et chaque ordinateur du réseau doit être validé comme appartenant au jeu approuvé d'utilisateurs et d'ordinateurs. Sur un système Windows, chacun de ces utilisateurs et ordinateurs est également appelé *principal de sécurité*.  
  
 Sur un domaine Windows assorti d'un contrôleur *Kerberos* , le contrôleur Kerberos utilise un schéma reposant sur l'octroi de tickets à chaque principal de sécurité. Les tickets octroyés par le contrôleur sont approuvés par d'autres octroyeurs de tickets du système. Dès lors qu'une entité essaie d'exécuter une opération ou d'accéder à une *ressource* (comme un fichier ou un répertoire sur un ordinateur), la validité du ticket est vérifiée et, si elle est établie, un autre ticket est fourni à la principal de sécurité pour cette opération. Cette méthode d'octroi de tickets est plus efficace que l'autre solution qui consiste à essayer de valider l'entité principale pour chaque opération.  
  
 Un mécanisme plus ancien et moins sécurisé est utilisé sur les domaines Windows ; il s'agit de NT LAN Manager (NTLM). Lorsque Kerberos ne peut pas être utilisé (généralement à l'extérieur d'un domaine Windows, comme dans un groupe de travail), NTLM peut être utilisé à la place. NTLM est également disponible comme option de sécurité d'IIS.  
  
 Sur un système Windows, l'autorisation consiste à assigner chaque ordinateur et utilisateur à un jeu de rôles et de groupes. Par exemple, chaque ordinateur Windows doit être configuré et contrôlé par une personne (ou un groupe de personnes) ayant le rôle d' *administrateur*. Il existe également un autre rôle, celui d' *utilisateur*, qui dispose d'un jeu beaucoup plus limité d'autorisations. Outre le rôle, les utilisateurs sont assignés à des groupes. Un groupe permet à plusieurs utilisateurs de travailler avec le même rôle. Dans la pratique, un ordinateur Windows est par conséquent administré en assignant des utilisateurs à des groupes. Par exemple, plusieurs utilisateurs peuvent être assignés au groupe d'utilisateurs d'un ordinateur et un jeu beaucoup plus limité d'utilisateurs peut être assigné au groupe des administrateurs. Sur un ordinateur local, un administrateur peut également créer des groupes et assigner d'autres utilisateurs (voire d'autres groupes) à ces groupes.  
  
 Sur un ordinateur qui exécute Windows, chaque dossier d'un répertoire peut être protégé. Autrement dit, vous pouvez sélectionner un dossier et contrôler qui peut accéder aux fichiers et si ces utilisateurs peuvent ou non copier, modifier ou supprimer un fichier, ou encore ajouter des fichiers au dossier. Il s'agit du contrôle d'accès. Le mécanisme associé est appelé la liste de contrôle d'accès (ACL, Access Control List). Lors de la création de l'ACL, vous pouvez assigner des privilèges d'accès à tout groupe, de même qu'aux membres individuels d'un domaine.  
  
 L’infrastructure WCF est conçue pour utiliser ces mécanismes de sécurité Windows. Par conséquent, si vous créez un service déployé sur un intranet dont les clients sont limités aux membres du domaine Windows, la sécurité est facilement implémentée. Seuls les utilisateurs valides peuvent se connecter au domaine. Une fois les utilisateurs connectés, le contrôleur Kerberos permet à chaque utilisateur d'établir des contextes de sécurité avec tout autre ordinateur ou application. Sur un ordinateur local, des groupes peuvent facilement être créés, et lors de la protection de dossiers spécifiques, ces groupes peuvent être utilisés pour assigner des privilèges d'accès sur l'ordinateur.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implémentation de la sécurité Windows sur des services intranet  

 Pour sécuriser une application qui s'exécute exclusivement sur un domaine Windows, vous pouvez utiliser les paramètres de sécurité par défaut de la liaison <xref:System.ServiceModel.WSHttpBinding> ou <xref:System.ServiceModel.NetTcpBinding> . Par défaut, toute personne se trouvant dans le même domaine Windows peut accéder aux services WCF. Ces utilisateurs s'étant connectés au réseau, ils sont approuvés. Les messages entre un service et un client sont chiffrés à des fins de confidentialité et archivés à des fins d'intégrité. Pour plus d’informations sur la création d’un service qui utilise la sécurité Windows, consultez [Comment : sécuriser un service avec des informations d’identification Windows](how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autorisation à l'aide de la classe PrincipalPermissionAttribute  

 Si vous devez limiter l'accès aux ressources d'un ordinateur, le moyen le plus simple est d'utiliser la classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> . Cet attribut vous permet de limiter l'invocation des opérations de service en exigeant que l'utilisateur appartienne à un groupe ou un rôle Windows spécifique ou qu'il soit un utilisateur spécifique. Pour plus d’informations, consultez [Comment : restreindre l’accès avec la classe PrincipalPermissionAttribute](how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Emprunt d'identité  

 L'emprunt d'identité est un autre mécanisme que vous pouvez utiliser pour contrôler l'accès aux ressources. Par défaut, un service hébergé par IIS s'exécutera sous l'identité du compte ASPNET. Le compte ASPNET peut accéder uniquement aux ressources pour lesquelles il possède une autorisation. Toutefois, il est possible de définir l'ACL pour un dossier de manière à exclure le compte de service ASPNET tout en autorisant certaines autres identités à accéder au dossier. Reste ensuite à savoir comment autoriser ces utilisateurs à accéder au dossier si le compte ASPNET n'y est pas autorisé. La solution consiste à utiliser l'emprunt d'identité. Le service est alors autorisé à utiliser les informations d'identification du client pour accéder à une ressource particulière. L'accès à une base de données SQL Server à laquelle seuls certains utilisateurs sont autorisés à accéder est un autre exemple. Pour plus d’informations sur l’utilisation de l’emprunt d’identité, consultez [Comment : emprunter l’identité d’un client sur un service](how-to-impersonate-a-client-on-a-service.md) et [délégation et emprunt d’identité](./feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Sécurité sur Internet  

 La sécurité sur Internet revêt les mêmes spécifications que la sécurité sur un intranet. Un service doit présenter ses informations d'identification pour prouver son authenticité, et les clients doivent prouver leur identité au service. Une fois l'identité d'un client prouvée, le service peut contrôler le niveau d'accès du client aux ressources. Toutefois, en raison de la nature hétérogène d'Internet, les informations d'identification présentées diffèrent de celles utilisées sur un domaine Windows. Alors qu'un contrôleur Kerberos gère l'authentification des utilisateurs sur un domaine avec des tickets pour les informations d'identification, sur Internet, les services et les clients peuvent utiliser de nombreuses méthodes pour présenter les informations d'identification. Toutefois, l’objectif de cette rubrique est de présenter une approche commune qui vous permet de créer un service WCF accessible sur Internet.  
  
### <a name="using-iis-and-aspnet"></a>Utilisation d'IIS et d'ASP.NET  

 Les spécifications de la sécurité Internet, tout comme les mécanismes de résolution de ces problèmes, ne sont pas nouveaux. IIS est le serveur Web de Microsoft pour Internet et propose de nombreuses fonctionnalités de sécurité qui répondent à ces problèmes. en outre, ASP.NET comprend des fonctionnalités de sécurité que les services WCF peuvent utiliser. Pour tirer parti de ces fonctionnalités de sécurité, hébergez un service WCF sur IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Utilisation de fournisseurs d'appartenances et de rôles ASP.NET  

 ASP.NET inclut un fournisseur d'appartenances et de rôles. Ce fournisseur est une base de données de paires nom d'utilisateur/mot de passe utilisées pour l'authentification des appelants, qui vous permet également de spécifier les privilèges d'accès de chaque appelant. Avec WCF, vous pouvez facilement utiliser un fournisseur d’appartenances et de rôles préexistant par le biais de la configuration. Pour obtenir un exemple d'application démontrant ces propos, consultez l'exemple [Membership and Role Provider](./samples/membership-and-role-provider.md) .  
  
### <a name="credentials-used-by-iis"></a>Informations d'identification utilisées par IIS  

 À la différence d'un domaine Windows assorti d'un contrôleur Kerberos, Internet est un environnement qui ne dispose d'aucun contrôleur pour gérer les millions d'utilisateurs qui se connectent à tout moment. Au lieu de cela, les informations d'identification sur Internet ont très souvent la forme de certificats X.509 (également appelés certificats Secure Sockets Layer ou SSL). Ces certificats sont généralement émis par une *autorité de certification*, qui peut être une société tierce qui se porte garant de l'authenticité du certificat et de la personne pour laquelle il a été émis. Pour exposer votre service sur Internet, vous devez également fournir un tel certificat approuvé pour authentifier votre service.  
  
 Là se pose la question suivante : comment obtenir un tel certificat ? Une approche consiste à s'adresser à une autorité de certification tierce, telle qu'Authenticode ou VeriSign, lorsque vous êtes prêt à déployer votre service et à acheter un certificat pour votre service. Toutefois, si vous êtes dans la phase de développement avec WCF et que vous n’êtes pas encore prêt à vous engager à acheter un certificat, il existe des outils et des techniques pour créer des certificats X. 509 que vous pouvez utiliser pour simuler un déploiement de production. Pour plus d’informations, consultez [utilisation des certificats](./feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Modes de sécurité  

 La programmation de la sécurité WCF implique quelques points de décision essentiels. L'un des plus basiques est le choix du *mode de sécurité*. Les deux principaux modes de sécurité sont le *mode de transport* et le *mode de message*.  
  
 Un troisième mode, qui combine la sémantique des deux principaux modes, est le *mode de transport avec informations d'identification de message*.  
  
 Le mode de sécurité détermine de quelle manière les messages sont sécurisés. Chaque mode présente des avantages et des inconvénients, comme expliqué ci-après. Pour plus d’informations sur la définition du mode de sécurité, consultez [Comment : définir le mode de sécurité](how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>mode de transport  

 Il existe plusieurs couches entre le réseau et l'application. L'une d'elles est la *couche**transport* , qui gère le transfert de messages entre des points de terminaison. Dans le cadre de cet objectif, il est nécessaire de comprendre que WCF utilise plusieurs protocoles de transport, chacun pouvant sécuriser le transfert des messages. (Pour plus d’informations sur les transports, consultez [transports](./feature-details/transports.md).)  
  
 Le protocole HTTP est très largement utilisé. Il en existe un autre, le protocole TCP. Chacun de ces protocoles peut sécuriser le transfert de messages par un ou plusieurs mécanismes propres au protocole. Par exemple, le protocole HTTP est sécurisé à l'aide de SSL sur HTTP, généralement abrégé en « HTTPS ». Ainsi, lorsque vous sélectionnez le mode de transport pour la sécurité, vous choisissez d'utiliser le mécanisme imposé par le protocole. Par exemple, si vous sélectionnez la classe <xref:System.ServiceModel.WSHttpBinding> et lui assignez le mode de sécurité Transport, vous sélectionnez SSL sur HTTP (HTTPS) comme mécanisme de sécurité. Le mode de transport présente l'avantage d'être plus efficace que le mode de message car la sécurité est intégrée à un niveau comparativement bas. Si le mode de transport est utilisé, le mécanisme de sécurité doit être implémenté conformément à la spécification du transport. Les messages peuvent donc transiter en toute sécurité en allant uniquement d'un point à un autre sur le transport.  
  
#### <a name="message-mode"></a>mode de message  

 Par opposition, le mode de message assure la sécurité en incluant les données de sécurité dans chaque message. Avec l'utilisation des en-têtes de sécurité XML et SOAP, les informations d'identification et autres données nécessaires pour assurer l'intégrité et la confidentialité du message sont incluses dans chaque message. Chaque message inclut des données de sécurité, ce qui a un impact sur les performances dans la mesure où chaque message doit être traité individuellement. (En mode de transport, une fois la couche de transport sécurisée, tous les messages sont acheminés librement.) Toutefois, la sécurité des messages présente un avantage sur la sécurité du transport : elle est plus flexible. En effet, les spécifications de sécurité ne sont pas déterminées par le transport. Vous pouvez utiliser tout type d'informations d'identification du client pour sécuriser le message. (En mode de transport, le protocole de transport détermine le type d'informations d'identification du client que vous pouvez utiliser.)  
  
#### <a name="transport-with-message-credentials"></a>Transport avec informations d'identification de message  

 Le troisième mode combine le meilleur de la sécurité de transport et de la sécurité de message. Dans ce mode, la sécurité de transport est utilisée pour garantir efficacement la confidentialité et l'intégrité de chaque message. En même temps, chaque message inclut ses propres informations d'identification, ce qui permet au message d'être authentifié. Avec l'authentification, l'autorisation peut également être implémentée. En authentifiant un expéditeur, l'accès aux ressources peut être accordé (ou refusé) en fonction de l'identité de l'expéditeur.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Spécification du type d'informations d'identification du client et de la valeur des informations d'identification  

 Après avoir sélectionné un mode de sécurité, vous voudrez sans doute spécifier un type d'informations d'identification du client. Le type d'informations d'identification du client spécifie quel type un client doit utiliser pour s'authentifier auprès du serveur.  
  
 Un type d'informations d'identification du client n'est pas requis dans tous les scénarios. Avec SSL sur HTTP (HTTPS), un service s'authentifie auprès du client. Dans le cadre de cette authentification, le certificat du service est envoyé au client dans un processus appelé *négociation*. Le transport sécurisé par SSL garantit que tous les messages sont confidentiels.  
  
 Si vous créez un service qui requiert l'authentification du client, le type d'informations d'identification du client que vous choisirez dépend du transport et du mode sélectionnés. Par exemple, l'utilisation du transport HTTP et la sélection du mode de transport vous laissent différents choix, comme Basic ou Digest. (Pour plus d’informations sur ces types d’informations d’identification, consultez [Présentation de l’authentification http](./feature-details/understanding-http-authentication.md).)  
  
 Si vous créez un service sur un domaine Windows qui sera uniquement disponible pour d'autres utilisateurs du réseau, le plus facile à utiliser est le type d'informations d'identification du client Windows. Toutefois, vous pouvez également avoir besoin de fournir un service avec un certificat. Pour cela, consultez [How to: Specify Client Credential Values](how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Valeurs d'informations d'identification  

 Une *valeur d'informations d'identification* représente les informations d'identification utilisées par le service. Après avoir spécifié un type d'informations d'identification, vous pouvez également avoir besoin de configurer votre service avec les informations d'identification réelles. Si vous avez sélectionné Windows (et si le service s'exécutera sur un domaine Windows), vous ne spécifiez pas de valeur d'informations d'identification réelle.  
  
## <a name="identity"></a>Identité  

 Dans WCF, le terme *identité* a des significations différentes pour le serveur et le client. Brièvement, lors de l'exécution d'un service, une identité est assignée au contexte de sécurité après l'authentification. Pour afficher l'identité réelle, vérifiez les propriétés <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> et <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> de la classe <xref:System.ServiceModel.ServiceSecurityContext> . Pour plus d’informations, consultez [Comment : examiner le contexte de sécurité](how-to-examine-the-security-context.md).  
  
 Par opposition, sur le client, l'identité est utilisée pour valider le service. Au moment du design, un développeur client peut affecter [\<identity>](../configure-apps/file-schema/wcf/identity.md) à l’élément une valeur obtenue du service. Au moment de l'exécution, le client vérifie la valeur de l'élément par rapport à l'identité réelle du service. Si la vérification échoue, le client termine la communication. La valeur peut être un nom d'utilisateur principal (UPN, User Principal Name) si le service s'exécute sous l'identité d'un utilisateur particulier ou un nom de principal du service (SPN, Service Principal Name) si le service s'exécute sous un compte d'ordinateur. Pour plus d’informations, consultez [identité du service et authentification](./feature-details/service-identity-and-authentication.md). Les informations d'identification peuvent également être un certificat ou un champ d'un certificat qui identifie le certificat.  
  
## <a name="protection-levels"></a>Niveaux de protection  

 La propriété `ProtectionLevel` est présente sur plusieurs classes d'attributs (telles que les classes <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> ). Le niveau de protection est une valeur qui spécifie si les messages (ou parties de messages) qui prennent en charge un service sont signés, signés et chiffrés, ou envoyés sans signature ou chiffrement. Pour plus d’informations sur la propriété, consultez [Présentation du niveau de protection](understanding-protection-level.md)et pour obtenir des exemples de programmation, consultez [How to : Set the ProtectionLevel Property](how-to-set-the-protectionlevel-property.md). Pour plus d’informations sur la conception d’un contrat de service avec le `ProtectionLevel` en contexte, consultez [conception de contrats de service](designing-service-contracts.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Identité du service et authentification](./feature-details/service-identity-and-authentication.md)
- [Fonctionnement des niveaux de protection](understanding-protection-level.md)
- [Délégation et emprunt d’identité](./feature-details/delegation-and-impersonation-with-wcf.md)
- [Conception de contrats de service](designing-service-contracts.md)
- [Sécurité](./feature-details/security.md)
- [Présentation de la sécurité](./feature-details/security-overview.md)
- [Procédure : définir la propriété ProtectionLevel](how-to-set-the-protectionlevel-property.md)
- [Procédure : sécuriser un service avec des informations d’identification Windows](how-to-secure-a-service-with-windows-credentials.md)
- [Procédure : définir le mode de sécurité](how-to-set-the-security-mode.md)
- [Procédure : spécifier le type d’informations d’identification de client](how-to-specify-the-client-credential-type.md)
- [Procédure : restreindre l’accès à la classe PrincipalPermissionAttribute](how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Procédure : emprunter l’identité d’un client sur un service](how-to-impersonate-a-client-on-a-service.md)
- [Procédure : examiner le contexte de sécurité](how-to-examine-the-security-context.md)
