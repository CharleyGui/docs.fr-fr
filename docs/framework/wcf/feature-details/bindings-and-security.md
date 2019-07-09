---
title: Liaisons et sécurité
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 47d0df1e93e97c6398b794e62d9fd2e821d54f93
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663237"
---
# <a name="bindings-and-security"></a>Liaisons et sécurité

Les liaisons fournies par le système incluses avec Windows Communication Foundation (WCF) offrent un moyen rapide de programmer des applications WCF. À une exception près, la méthode de sécurité par défaut de toutes les liaisons est activée. Cette rubrique vous permet de sélectionner la liaison appropriée à vos besoins de sécurité.

Pour une vue d’ensemble de la sécurité WCF, consultez [vue d’ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md). Pour plus d’informations sur la programmation WCF à l’aide de liaisons, consultez [de programmation de sécurité de WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).

Si vous avez déjà sélectionné une liaison, vous trouverez plus d’informations sur les comportements d’exécution qui sont associés à la sécurité dans [comportements de sécurité](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).

Certaines fonctions de sécurité ne sont pas programmables à l'aide des liaisons fournies par le système. Pour plus de contrôle à l’aide d’une liaison personnalisée, consultez [des fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).

## <a name="security-functions-of-bindings"></a>Fonctions de sécurité des liaisons

WCF inclut plusieurs liaisons fournies par le système qui répondent à la plupart des besoins. Si une liaison spécifique ne suffit pas, vous pouvez également créer une liaison personnalisée. Pour obtenir la liste des liaisons fournies par le système, consultez [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md). Pour plus d’informations sur les liaisons personnalisées, consultez [liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).

Chaque liaison dans WCF a deux formes : sous la forme d’une API et un élément XML utilisé dans un fichier de configuration. Par exemple, le `WSHttpBinding` (API) a un équivalent le [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).

La section suivante répertorie ces deux formulaires pour chaque de liaison et récapitule les fonctionnalités de sécurité.

### <a name="basichttp"></a>BasicHttp

Dans le code, utilisez le <xref:System.ServiceModel.BasicHttpBinding> classe ; dans la configuration, utilisez le [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).

Cette liaison est conçue pour être utilisées avec une vaste gamme de technologies existantes, dont les suivantes :

- Services Web ASP.NET (ASMX), version 1.

- Applications WSE (Web Service Enhancements).

- Basic Profile tel que défini dans l’interopérabilité de Services Web (WS-I) spécification (<https://go.microsoft.com/fwlink/?LinkId=38955>).

- Profil de sécurité de base tel que défini dans WS-I.

Par défaut, cette liaison n’est pas sécurisée. Elle est conçue pour interagir avec les services ASMX. Lorsque la sécurité est activée, la liaison fournit une interopérabilité transparente avec les mécanismes de sécurité IIS (Internet Information Services), tels que l'authentification de base, Digest et la sécurité Windows intégrée. Pour plus d’informations, consultez [vue d’ensemble de sécurité de Transport](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). Cette liaison prend en charge les fonctionnalités suivantes :

- Sécurité du transport HTTPS.

- Authentification de base HTTP.

- WS-Security.

Pour plus d'informations, voir <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType> et <xref:System.ServiceModel.BasicHttpSecurityMode>.

### <a name="wshttpbinding"></a>WSHttpBinding

Dans le code, utilisez le <xref:System.ServiceModel.WSHttpBinding> classe ; dans la configuration, utilisez le [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).

Par défaut, cette liaison implémente la spécification WS-Security et fournit l’interopérabilité avec les services qui implémentent les spécifications WS-*. Elle prend en charge les fonctionnalités suivantes :

- Sécurité du transport HTTPS.

- WS-Security.

- Protection du transport HTTPS avec sécurité des informations d'identification de message SOAP permettant d'authentifier l'appelant.

Pour plus d’informations, consultez <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, et <xref:System.ServiceModel.HttpProxyCredentialType>.

### <a name="wsdualhttpbinding"></a>WSDualHttpBinding

Dans le code, utilisez le <xref:System.ServiceModel.WSDualHttpBinding> classe ; dans la configuration, utilisez le [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).

Cette liaison est conçue pour activer des applications de service duplex. Elle implémente la spécification WS-Security pour la sécurité de transfert basée sur les messages. La sécurité de transport n'est pas disponible. Par défaut, elle fournit les fonctionnalités suivantes :

- Implémente WS-Reliable Messaging pour la fiabilité.

- Implémente WS-Security pour l'authentification et la sécurité de transfert.

- Utilise HTTP pour la remise de messages.

- Utilise l'encodage de message Text/XML.

 À l'aide de WS-Security (sécurité au niveau de la couche de message), la liaison vous permet de configurer les paramètres suivants :

- La suite algorithmique de sécurité afin de déterminer l'algorithme de chiffrement.

- Options de liaison pour les éléments suivants :

  - Fourniture des informations d'identification de service disponibles hors bande au niveau du client.

  - Fourniture des informations d'identification de service négociées à partir du service dans le cadre de l'installation des canaux.

Pour plus d’informations, consultez <xref:System.ServiceModel.WSDualHttpSecurity> et <xref:System.ServiceModel.WSDualHttpSecurityMode>.

### <a name="nettcpbinding"></a>NetTcpBinding

Dans le code, utilisez le <xref:System.ServiceModel.NetTcpBinding> classe ; dans la configuration, utilisez le [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).

Cette liaison est optimisée pour la communication d’un ordinateur à l’autre. Par défaut, elle présente les caractéristiques suivantes :

- Elle implémente la sécurité au niveau de la couche de transport.

- Elle tire parti de la sécurité Windows pour l'authentification et la sécurité de transfert.

- Elle utilise TCP pour le transport.

- Elle implémente l'encodage de message binaire.

- Elle implémente WS-Reliable Messaging.

Les options disponibles sont les suivantes :

- Sécurité au niveau de la couche de message (à l'aide de WS-Security).

- Sécurité de transport à l'aide des informations d'identification du message : confidentialité et intégrité fournies par TLS (Transport Layer Security), informations d'identification pour l'autorisation fournies par WS-Security.

Pour plus d’informations, consultez <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, et <xref:System.ServiceModel.MessageCredentialType>.

### <a name="netnamedpipebinding"></a>NetNamedPipeBinding

Dans le code, utilisez le <xref:System.ServiceModel.NetNamedPipeBinding> classe ; dans la configuration, utilisez le [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).

Cette liaison est optimisée pour la communication interprocessus (généralement sur le même ordinateur). Par défaut, elle présente les caractéristiques suivantes :

- Elle utilise la sécurité de transport pour l'authentification et le transfert de messages.

- Elle utilise des canaux nommés pour la remise de messages.

- Elle implémente l'encodage de message binaire.

- Chiffrement et signature des messages

Les options disponibles sont les suivantes :

- Authentification à l'aide de la sécurité Windows.

Pour plus d'informations, consultez <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode> et <xref:System.ServiceModel.NamedPipeTransportSecurity>.

### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding

Dans le code, utilisez le <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> classe ; dans la configuration, utilisez le [ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).

Cette liaison est optimisée pour la création des clients WCF et des services qui interagissent avec les points de terminaison non - WCF MSMQ Microsoft Message Queuing.

Par défaut, elle utilise la sécurité de transport et fournit les caractéristiques de sécurité suivantes :

- La sécurité peut être désactivée (None).

- Sécurité de transport MSMQ (Transport).

Pour plus d’informations, consultez <xref:System.ServiceModel.NetMsmqSecurity> et <xref:System.ServiceModel.NetMsmqSecurityMode>.

### <a name="netmsmqbinding"></a>NetMsmqBinding

Dans le code, utilisez le <xref:System.ServiceModel.NetMsmqBinding> classe ; dans la configuration, utilisez le [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).

Cette liaison est prévue pour une utilisation lors de la création de services WCF nécessitant MSMQ prise en charge de message en file d’attente.

Par défaut, elle utilise la sécurité de transport et fournit les caractéristiques de sécurité suivantes :

- La sécurité peut être désactivée (None).

- Sécurité de transport MSMQ (Transport).

- Sécurité des messages SOAP (Message).

- Transport simultané et sécurité des messages (Both).

- Types d’informations d’identification de client pris en charge : None, Windows, nom d’utilisateur, certificat, IssuedToken.

L'information d'identification <xref:System.ServiceModel.MessageCredentialType.Certificate> est uniquement prise en charge lorsque le mode de sécurité a la valeur <xref:System.ServiceModel.NetMsmqSecurityMode.Both> ou <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.

Pour plus d’informations, consultez <xref:System.ServiceModel.MessageSecurityOverMsmq> et <xref:System.ServiceModel.MsmqTransportSecurity>.

### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding

Dans le code, utilisez le <xref:System.ServiceModel.WSFederationHttpBinding> classe ; dans la configuration, utilisez le [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).

Par défaut, cette liaison utilise WS-Security (sécurité au niveau de la couche de message).

Pour plus d’informations, consultez [fédération](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, et <xref:System.ServiceModel.WSFederationHttpSecurityMode>.

## <a name="custom-bindings"></a>Liaisons personnalisées

Si aucune des liaisons fournies par le système ne répondent à vos besoins, vous pouvez créer une liaison personnalisée à l’aide d’un élément de liaison de sécurité personnalisé. Pour plus d’informations, consultez [fonctionnalités de sécurité avec les liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).

## <a name="binding-choices"></a>Options de liaison

Le tableau suivant récapitule les fonctionnalités offertes par le paramètre de mode de sécurité défini ; autrement dit, il répertorie les fonctionnalités disponibles lorsque le mode de sécurité a la valeur `Transport`, `Message`ou `TransportWithMessageCredential`. Utilisez-le pour rechercher les fonctionnalités de sécurité que votre application requiert.

|Paramètre|Fonctionnalités|
|-------------|--------------|
|Transport|Authentification du serveur<br /><br /> Authentification du client<br /><br /> Sécurité point à point<br /><br /> Interopérabilité<br /><br /> Accélération matérielle<br /><br /> Haut débit<br /><br /> Pare-feu sécurisé<br /><br /> Applications à latence élevée<br /><br /> Rechiffrement sur des sauts multiples|
|Message|Authentification du serveur<br /><br /> Authentification du client<br /><br /> Sécurité de bout en bout<br /><br /> Interopérabilité<br /><br /> Revendications enrichies<br /><br /> Fédération<br /><br /> Authentification multifacteur<br /><br /> Jetons personnalisés<br /><br /> Service de notaire/horodatage<br /><br /> Applications à latence élevée<br /><br /> Persistance des signatures de message|
|TransportWithMessageCredential|Authentification du serveur<br /><br /> Authentification du client<br /><br /> Sécurité point à point<br /><br /> Interopérabilité<br /><br /> Accélération matérielle<br /><br /> Haut débit<br /><br /> Revendications client enrichies<br /><br /> Fédération<br /><br /> Authentification multifacteur<br /><br /> Jetons personnalisés<br /><br /> Pare-feu sécurisé<br /><br /> Applications à latence élevée<br /><br /> Rechiffrement sur des sauts multiples|

Le tableau suivant répertorie les liaisons qui prennent en charge les divers paramètres de mode. Sélectionnez dans le tableau la liaison à utiliser pour créer votre point de terminaison de service.

|Liaison|Prise en charge du mode Transport|Prise en charge du mode Message|Prise en charge de TransportWithMessageCredential|
|-------------|----------------------------|--------------------------|--------------------------------------------|
|`BasicHttpBinding`|Oui|Oui|Oui|
|`WSHttpBinding`|Oui|Oui|Oui|
|`WSDualHttpBinding`|Non|Oui|Non|
|`NetTcpBinding`|Oui|Oui|Oui|
|`NetNamedPipeBinding`|Oui|Non|Non|
|`NetMsmqBinding`|Oui|Oui|Non|
|`MsmqIntegrationBinding`|Oui|Non|Non|
|`wsFederationHttpBinding`|Non|Oui|Oui|

## <a name="transport-credentials-in-bindings"></a>Informations d'identification de transport dans les liaisons

Le tableau suivant répertorie les types d'informations d'identification du client disponibles lors de l'utilisation de `BasicHttpBinding` ou `WSHttpBinding` en mode de sécurité Transport.

|Type|Description|
|----------|-----------------|
|None|Spécifie que le client n'a pas besoin de présenter d'informations d'identification. Cela se traduit en un client anonyme.|
|Basic|Authentification de base. Pour plus d’informations, consultez la RFC 2617 – authentification HTTP : Base et Digest, disponible à l’adresse <https://go.microsoft.com/fwlink/?LinkId=84023>.|
|Digest|Authentification Digest. Pour plus d’informations, consultez la RFC 2617 – authentification HTTP : Base et Digest, disponible à l’adresse <https://go.microsoft.com/fwlink/?LinkId=84023>.|
|NTLM|Authentification NTLM (NT LAN Manager).|
|Windows|Authentification Windows.|
|Certificat|Authentification effectuée à l'aide d'un certificat.|
|IssuedToken|Permet au service d’exiger que le client soit authentifié à l’aide d’un jeton émis par un service de jeton de sécurité ou CardSpace. Pour plus d’informations, consultez [fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|

### <a name="message-client-credentials-in-bindings"></a>Informations d'identification du client de message dans les liaisons

Le tableau suivant répertorie les types d'informations d'identification du client disponibles lors de l'utilisation d'une liaison en mode de sécurité Message.

|Type|Description|
|----------|-----------------|
|None|Autorise le service à interagir avec des clients anonymes.|
|Windows|Autorise les échanges de messages SOAP à se produire sous le contexte authentifié d'une information d'identification Windows.|
|UserName|Autorise le service à imposer que le client soit authentifié à l'aide d'une information d'identification de nom d'utilisateur. Notez que lorsque le mode de sécurité est défini sur `TransportWithMessageCredential`, WCF ne prend pas en charge l’envoi d’un mot de passe digest ou des clés dérivantes à l’aide du mot de passe et à l’aide de ces clés pour le mode de sécurité Message. Par conséquent, WCF met en œuvre que le transport est sécurisé lors de l’utilisation des informations d’identification utilisateur.|
|Certificat|Autorise le service à exiger une authentification du client via un certificat.|
|IssuedToken|Autorise le service à utiliser un service d'émission de jeton de sécurité afin de fournir un jeton personnalisé.|

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Sécurisation des services et des clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Sélection d’un type d’informations d’identification](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Comportements de sécurité](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Modèle de sécurité pour Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
