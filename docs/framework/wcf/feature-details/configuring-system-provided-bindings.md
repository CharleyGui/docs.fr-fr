---
title: Configuration des liaisons fournies par le système
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: d6018c8339cb04471bf9ce0f2ee86e091e1d1e95
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597525"
---
# <a name="configuring-system-provided-bindings"></a>Configuration des liaisons fournies par le système
Les liaisons spécifient le mécanisme de communication à utiliser pour communiquer avec un point de terminaison et indiquer comment se connecter à un point de terminaison. Les liaisons se composent d’éléments qui définissent la façon dont les canaux Windows Communication Foundation (WCF) sont superposés pour fournir les fonctionnalités de communication requises. Une liaison contient trois types d'éléments :  
  
- Éléments de liaison de canal de protocole qui déterminent la sécurité, la fiabilité, des paramètres de flux de contexte ou des protocoles définis par l'utilisateur à utiliser avec les messages envoyés au point de terminaison.  
  
- Éléments de liaison de canal de transport qui déterminent le protocole de transport sous-jacent à utiliser lors de l’envoi des messages au point de terminaison, par exemple, le protocole TCP ou HTTP.  
  
- Éléments de liaison d’encodage de message qui déterminent le code de câble à utiliser pour les messages envoyés au point de terminaison, par exemple, texte/XML, binaire ou MTOM (Message Transmission Optimization Mechanism).  
  
 Cette rubrique présente toutes les liaisons Windows Communication Foundation fournies par le système (WCF). Si aucun de ces éléments ne répond aux exigences exactes de votre application, vous pouvez créer une liaison à l’aide de la classe <xref:System.ServiceModel.Channels.CustomBinding>. Pour plus d’informations sur la création de liaisons personnalisées, consultez [Liaisons personnalisées](../extending/custom-bindings.md).  
  
> [!IMPORTANT]
> Sélectionnez une liaison dont la sécurité est activée. Par défaut, toutes les liaisons, à l'exception de la liaison <xref:System.ServiceModel.BasicHttpBinding>, ont la sécurité activée. Si vous ne sélectionnez pas de liaison sécurisée, ou si vous désactivez la sécurité, assurez-vous que vos échanges de réseau sont protégés d’une autre manière, comme le fait d’appartenir à un centre de données sûr ou à un réseau isolé.  
  
> [!IMPORTANT]
> N’utilisez pas de contrats duplex avec les liaisons qui ne prennent pas en charge la sécurité, ou dont la sécurité est désactivée, sauf si l’échange de réseau est sécurisé par d’autres moyens.  
  
## <a name="system-provided-bindings"></a>Liaisons fournies par le système  
 Les liaisons suivantes sont fournies avec WCF.  
  
|Liaison|Élément de configuration|Description|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|Une liaison qui est appropriée pour communiquer avec les services Web conformes à WS-Basic Profil, par exemple, les services basés sur les services Web ASP.NET (ASMX). Cette liaison utilise HTTP comme le transport et texte/XML comme encodage de message par défaut.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|Une liaison sécurisée et interopérable adaptée aux contrats de service non duplex.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../configure-apps/file-schema/wcf/ws2007httpbinding.md)|Une liaison interopérable et sécurisée qui assure la prise en charge des versions appropriées des éléments de liaison <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession> et <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A>.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Une liaison sécurisée et interopérable appropriée pour les contrats de service duplex ou les communications par le biais des intermédiaires SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Une liaison sécurisée et interopérable qui prend en charge le protocole WS-Federation et permet aux organisations qui sont dans une fédération d’authentifier et d’autoriser efficacement les utilisateurs.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding>](../../configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Liaison sécurisée et interopérable qui dérive de <xref:System.ServiceModel.WS2007HttpBinding> et prend en charge la sécurité fédérée.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|Liaison sécurisée et optimisée, adaptée à la communication des applications WCF entre les machines.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../../configure-apps/file-schema/wcf/netnamedpipebinding.md)|Liaison sécurisée, fiable et optimisée adaptée à la communication des applications WCF sur les machines.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|Liaison en file d’attente adaptée à la communication des applications WCF entre les machines.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../../configure-apps/file-schema/wcf/netpeertcpbinding.md)|Une liaison qui permet la communication sécurisée entre plusieurs ordinateurs.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../configure-apps/file-schema/wcf/webhttpbinding.md)|Liaison utilisée afin de configurer des points de terminaison pour les services web WCF qui sont exposés via des requêtes HTTP au lieu de messages SOAP.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Une liaison adaptée à la communication entre ordinateurs entre une application WCF et des applications Message Queuing existantes (également appelées MSMQ).|  
  
## <a name="binding-features"></a>Fonctionnalités de liaison  
 Le tableau suivant répertorie certaines des fonctionnalités clés fournies par chacune des liaisons fournies par le système. Les liaisons sont répertoriées dans la première colonne et les information concernant les fonctionnalités sont décrites dans le tableau. Le tableau suivant fournit une clé pour les abréviations de liaison utilisées. Pour sélectionner une liaison, déterminez quelle colonne satisfait toutes les fonctionnalités de ligne dont vous avez besoin.  
  
|Liaison|Interopérabilité|Mode de sécurité (valeur par défaut)|Session<br /><br /> (Par défaut)|Transactions|Duplex|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Aucun), transport, message, mixte|Aucun, (aucun)|(aucune)|n/a|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Aucun, transport, (message), mixte|(Aucun), transport, session fiable|(Aucun), oui|n/a|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|Aucun, transport, (message), mixte|(Aucun), transport, session fiable|(Aucun), oui|n/a|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Aucun, (Message)|(Session fiable)|(Aucun), oui|Oui|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|Un certificat de fournisseur d'identité WS-Federation|Aucun, (Message), mixte|(Aucun), session fiable|(Aucun), oui|Non|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|Un certificat de fournisseur d'identité WS-Federation|Aucun, (Message), mixte|(Aucun), session fiable|(Aucun), oui|Non|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Aucun, (transport), message,<br /><br /> Mixte|Session fiable, (transport)|(Aucun), oui|Oui|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|Aucun,<br /><br /> (Transport)|Aucun, (Transport)|(Aucun), oui|Oui|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Aucun, message, (transport), les deux|(aucune)|(Aucun), oui|Non|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Homologue|Aucun, message, (transport), mixte|(aucune)|(aucune)|Oui|  
|<xref:System.ServiceModel.WebHttpBinding>|.Net|Aucun, transport, TransportCredentialOnly|(aucune)|(aucune)|n/a|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Aucun, (Transport)|(aucune)|(Aucun), oui|n/a|  
  
 Le tableau suivant explique les fonctionnalités répertoriées dans le tableau précédent.  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Type d'interopérabilité|Nomme le protocole ou la technologie avec laquelle la liaison garantit l'interopérabilité.|  
|Sécurité|Définit le mode de sécurisation du canal :<br /><br /> -None : le message SOAP n’est pas sécurisé et le client n’est pas authentifié.<br />-Transport : les exigences de sécurité sont satisfaites au niveau de la couche de transport.<br />-Message : les exigences de sécurité sont satisfaites au niveau de la couche de message.<br />-Mixed : ce mode de sécurité est connu sous le nom de `TransportWithMessageCredentials` . Il gère les informations d’identification au niveau du message, et les exigences relatives à l’intégrité et à la confidentialité sont traitées par la couche de transport.<br />-Both : la sécurité au niveau du message et au niveau du transport est utilisée. Cette fonction est propre à <xref:System.ServiceModel.NetMsmqBinding>.|  
|Session|Spécifie si cette liaison prend en charge des contrats de session.|  
|Transactions|Spécifie si les transactions sont activées.|  
|Duplex|Spécifie si les contrats duplex sont pris en charge. Notez que cette fonctionnalité requiert la prise en charge des sessions dans la liaison.|  
|Diffusion en continu|Spécifie si la diffusion en continu de message est prise en charge.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la création de points de terminaison](../endpoint-creation-overview.md)
- [Utilisation de liaisons pour configurer des services et des clients](../using-bindings-to-configure-services-and-clients.md)
- [Programmation WCF de base](../basic-wcf-programming.md)
