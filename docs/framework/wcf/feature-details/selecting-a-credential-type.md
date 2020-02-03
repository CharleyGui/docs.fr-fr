---
title: Sélection d'un type d'informations d'identification
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 6737f7daeb37e2e296ca0429d73b963743c409a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746138"
---
# <a name="selecting-a-credential-type"></a>Sélection d'un type d'informations d'identification
Les *informations d’identification* sont utilisées par le Windows Communication Foundation de données (WCF) pour établir une identité ou des fonctionnalités demandées. Par exemple, un passeport est une information d'identification émise par un gouvernement pour établir la citoyenneté dans un pays ou une région. Dans WCF, les informations d’identification peuvent prendre plusieurs formes, telles que les jetons de nom d’utilisateur et les certificats X. 509. Cette rubrique décrit les informations d’identification, comment elles sont utilisées dans WCF et comment sélectionner les informations d’identification appropriées pour votre application.  
  
 Dans de nombreux pays et régions, un permis de conduire est un exemple d'informations d'identification. Un permis contient des données qui représentent l'identité d'une personne et ses fonctions. Elle contient la preuve de propriété sous la forme de la photographie du propriétaire. Le permis est délivré par une autorité approuvée, habituellement un service public chargé d'accorder des permis. Le permis est scellé et peut contenir un hologramme qui indique qu'il n'a pas été falsifié.  
  
 La présentation d'informations d'identification implique la présentation à la fois des données et la preuve de la propriété de ces données. WCF prend en charge divers types d’informations d’identification au niveau du transport et de la sécurité des messages. Par exemple, considérez deux types d’informations d’identification pris en charge dans WCF : nom d’utilisateur et informations d’identification de certificat (X. 509).  
  
 Pour les informations d'identification de nom d'utilisateur, le nom d'utilisateur représente l'identité déclarée et le mot de passe fournit la preuve de la propriété. L'autorité approuvée dans ce cas est le système qui valide le nom d'utilisateur et le mot de passe.  
  
 Avec les informations d’identification de certificat X. 509, le nom d’objet, l’autre nom de l’objet ou des champs spécifiques dans le certificat peuvent être utilisés comme revendications d’identité, tandis que d’autres champs, tels que les champs `Valid From` et `Valid To`, spécifient la validité du certificat.  
  
## <a name="transport-credential-types"></a>Types d'informations d'identification  
 Le tableau suivant affiche les types possibles d’informations d’identification du client qui peuvent être utilisés par une liaison en mode de sécurité de transport. Lorsque vous créez un service, affectez à la propriété `ClientCredentialType` une de ces valeurs pour spécifier le type d'information d'identification que le client doit fournir pour communiquer avec votre service. Vous pouvez définir les types dans les fichiers de code ou de configuration.  
  
|Paramètre|Description|  
|-------------|-----------------|  
|Aucune|Spécifie que le client n'a pas besoin de présenter d'informations d'identification. Cela se traduit en un client anonyme.|  
|Basique|Spécifie l'authentification de base pour le client. Pour plus d’informations, consultez RFC2617 :[authentification http : authentification de base et Digest](ftp://ftp.rfc-editor.org/in-notes/rfc2617.txt).|  
|Digest|Spécifie l’authentification Digest pour le client. Pour plus d’informations, consultez RFC2617 :[authentification http : authentification de base et Digest](ftp://ftp.rfc-editor.org/in-notes/rfc2617.txt).|  
|Ntlm|Spécifie l'authentification NTLM (NT LAN Manager). S'utilise si pour une raison quelconque vous ne pouvez pas utiliser l'authentification Kerberos. Vous pouvez également désactiver son utilisation comme solution de secours en affectant à la propriété <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> la valeur `false`, ce qui amène WCF à faire un meilleur effort pour lever une exception si NTLM est utilisé. Notez que l'affectation de la valeur `false` à cette propriété peut ne pas empêcher la transmission des informations d'identification NTLM.|  
|Windows|Spécifie l'authentification Windows. Pour spécifier uniquement le protocole Kerberos sur un domaine Windows, affectez à la propriété <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> la valeur `false` (la valeur par défaut est `true`).|  
|Certificat|Effectue l'authentification du client à l'aide d'un certificat X.509.|  
|Password|L'utilisateur doit fournir un nom d'utilisateur et un mot de passe. Validez la paire nom d'utilisateur/mot de passe à l'aide de l'authentification Windows ou d'une autre solution personnalisée.|  
  
### <a name="message-client-credential-types"></a>Types d'informations d'identification du client de message  
 Le tableau suivant illustre les types d'informations d'identification possibles que vous pouvez utiliser lors de la création d'une application qui utilise la sécurité de message. Vous pouvez utiliser ces valeurs dans les fichiers de code ou de configuration.  
  
|Paramètre|Description|  
|-------------|-----------------|  
|Aucune|Spécifie que le client n'a pas besoin de présenter d'informations d'identification. Cela se traduit en un client anonyme.|  
|Windows|Permet les échanges de messages SOAP dans le contexte de sécurité établi avec des informations d'identification Windows.|  
|Nom d’utilisateur|Autorise le service à exiger que le client soit authentifié avec des informations d'identification de nom d'utilisateur. Notez que WCF n’autorise pas les opérations de chiffrement avec les noms d’utilisateur, comme la génération d’une signature ou le chiffrement de données. WCF s’assure que le transport est sécurisé lors de l’utilisation des informations d’identification de nom d’utilisateur.|  
|Certificat|Autorise le service à exiger que le client soit authentifié à l'aide d'un certificat X.509.|  
|Jeton émis|Type de jeton personnalisé configuré en fonction d'une stratégie de sécurité. Le type de jeton par défaut est le jeton SAML (Security Assertions Markup Language). Le jeton est émis par un service de jetons sécurisé. Pour plus d’informations, consultez [Fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Modèle de négociation des informations d'identification du service  
 La *négociation* est le processus qui consiste à établir une relation de confiance entre un client et un service en échangeant des informations d’identification. Le processus est exécuté de manière itérative entre le client et le service afin de divulguer uniquement les informations nécessaires pour l'étape suivante dans le processus de négociation. En pratique, le résultat final consiste à remettre les informations d'identification d'un service au client pour qu'elles soient utilisées dans des opérations ultérieures.  
  
 À une exception près, par défaut, les liaisons fournies par le système dans WCF négocient automatiquement les informations d’identification du service lors de l’utilisation de la sécurité au niveau du message. (L’exception est la <xref:System.ServiceModel.BasicHttpBinding>, qui n’active pas la sécurité par défaut.) Pour désactiver ce comportement, consultez les propriétés <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> et <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A>.  
  
> [!NOTE]
> Lorsque la sécurité SSL est utilisée avec .NET Framework 3,5 et versions ultérieures, un client WCF utilise à la fois les certificats intermédiaires dans son magasin de certificats et les certificats intermédiaires reçus pendant la négociation SSL pour effectuer la validation de la chaîne de certificats sur le service certificat. .NET Framework 3.0 n'utilise que les certificats intermédiaires installés dans le magasin de certificats local.  
  
#### <a name="out-of-band-negotiation"></a>Négociation hors bande  
 Si la négociation automatique est désactivée, les informations d'identification du service doivent être configurées au niveau du client avant l'envoi de messages au service. Il s’agit également d’une configuration *hors bande* . Par exemple, si le type d'informations d'identification spécifié est un certificat et que la négociation automatique est désactivée, le client doit contacter le propriétaire de service pour recevoir et installer le certificat sur l'ordinateur qui exécute l'application cliente. Cette opération peut avoir lieu, par exemple, lorsque vous souhaitez contrôler de manière stricte les clients pouvant accéder à un service dans un scénario interentreprises. Cette négociation hors bande peut être effectuée par courrier électronique et le certificat X. 509 est stocké dans le magasin de certificats Windows, à l’aide d’un outil tel que le composant logiciel enfichable Certificats de la console MMC (Microsoft Management Console).  
  
> [!NOTE]
> La propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> est utilisée pour fournir au service un certificat obtenu dans le cadre d'une négociation hors bande. Celui-ci est nécessaire pour utiliser la classe <xref:System.ServiceModel.BasicHttpBinding> parce que la liaison n'autorise pas de négociation automatisée. La propriété est également utilisée dans un scénario duplex non corrélé. Dans ce scénario, un serveur envoie un message au client sans exiger que le client envoie en premier une demande au serveur. Comme le serveur ne reçoit pas de demande du client, il doit utiliser le certificat du client pour chiffrer le message au client.  
  
## <a name="setting-credential-values"></a>Définition des valeurs d'informations d'identification  
 Une fois que vous sélectionnez un mode de sécurité, vous devez spécifier les informations d'identification à proprement dites. Par exemple, si le type d'informations d'identification a pour valeur « certificate », vous devez associer une information d'identification spécifique (tel qu'un certificat X.509 spécifique) au service ou au client.  
  
 Selon que vous programmez un service ou un client, la méthode pour définir la valeur des informations d'identification diffère légèrement.  
  
### <a name="setting-service-credentials"></a>Définition des informations d'identification de service  
 Si vous utilisez le mode de transport et que vous utilisez le protocole HTTP comme transport, vous devez utiliser les services Internet (IIS) ou configurer le port avec un certificat. Pour plus d’informations, consultez [vue d’ensemble de la sécurité du transport](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) et [sécurité du transport http](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pour configurer un service avec les informations d'identification dans le code, créez une instance de la classe <xref:System.ServiceModel.ServiceHost> et spécifiez les informations d'identification appropriées à l'aide de la classe <xref:System.ServiceModel.Description.ServiceCredentials>, accessible par la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>.  
  
#### <a name="setting-a-certificate"></a>Définition d'un certificat  
 Pour configurer un service avec un certificat X.509 à utiliser pour authentifier le service auprès des clients, utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>.  
  
 Pour configurer un service avec un certificat client, utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>.  
  
#### <a name="setting-windows-credentials"></a>Définition des informations d'identification Windows  
 Si le client spécifie un nom d'utilisateur et un mot de passe valides, ces informations d'identification sont utilisées pour authentifier le client. Sinon, les informations d'identification de l'utilisateur actuellement connecté sont utilisées.  
  
### <a name="setting-client-credentials"></a>Définition des informations d'identification du client  
 Dans WCF, les applications clientes utilisent un client WCF pour se connecter aux services. Chaque client dérive de la classe <xref:System.ServiceModel.ClientBase%601> et la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> sur le client autorise la spécification de différentes valeurs d'informations d'identification du client.  
  
#### <a name="setting-a-certificate"></a>Définition d'un certificat  
 Pour configurer un service avec un certificat X.509 qui est utilisé pour authentifier le client auprès d'un service, utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Comment sont utilisées les informations d'identification du client pour authentifier un client auprès du service  
 Les informations d'identification du client requises pour communiquer avec un service sont fournies à l'aide de la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> ou de la propriété <xref:System.ServiceModel.ChannelFactory.Credentials%2A>. Le canal de sécurité utilise ces informations pour authentifier le client auprès du service. L'authentification est accomplie par l'intermédiaire d'un des deux modes :  
  
- Les informations d’identification du client sont utilisées une fois avant l’envoi du premier message, à l’aide de l’instance du client WCF pour établir un contexte de sécurité. Tous les messages d'application sont ensuite sécurisés par l'intermédiaire du contexte de sécurité.  
  
- Les informations d'identification du client sont utilisées pour authentifier chaque message d'application envoyé au service. Dans ce cas, aucun contexte n'est établi entre le client et le service.  
  
### <a name="established-identities-cannot-be-changed"></a>Les identités établies ne peuvent pas être modifiées  
 Lorsque la première méthode est utilisée, le contexte établi est associé définitivement à l'identité du client. Autrement dit, une fois le contexte de sécurité établi, l'identité associée au client ne peut pas être modifiée.  
  
> [!IMPORTANT]
> Il existe un cas où l'identité ne peut pas être établie (autrement dit, lorsque le contexte de sécurité établi est activé, ce qui est le comportement par défaut). Si vous créez un service qui communique avec un deuxième service, l’identité utilisée pour ouvrir le client WCF auprès du deuxième service ne peut pas être modifiée. Cela devient problématique si plusieurs clients sont autorisés à utiliser le premier service et que le service emprunte l'identité des clients lors de l'accès au deuxième service. Si le service réutilise le même client pour tous les appelants, tous les appels au deuxième service sont effectués sous l'identité du premier appelant ayant été utilisé pour ouvrir le client au deuxième service. En d'autres termes, le service utilise l'identité du premier client pour tous ses clients afin de communiquer avec le deuxième service. Cette situation peut entraîner l'élévation des privilèges. Si ce comportement n'est pas souhaité pour votre service, vous devez suivre chaque appelant et créer un client au deuxième service pour chaque appelant et veiller à ce que le service utilise uniquement le bon client pour le bon appelant en vue de communiquer avec le deuxième service.  
  
 Pour plus d’informations sur les informations d’identification et les sessions sécurisées, consultez Considérations sur la [sécurité pour les sessions sécurisées](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>
- [Concepts relatifs à la sécurité](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Sécurisation des services et des clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Programmation de la sécurité dans WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Sécurité de transport HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
