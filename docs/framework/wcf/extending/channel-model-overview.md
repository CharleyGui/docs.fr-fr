---
title: Vue d'ensemble du modèle de canal
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: 8a71adbc9c9b3f13cde250ff0bfbca67e9f23df9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262175"
---
# <a name="channel-model-overview"></a>Vue d'ensemble du modèle de canal

La pile de canaux Windows Communication Foundation (WCF) est une pile de communication en couches avec un ou plusieurs canaux qui traitent les messages. Le canal de transport, qui figure tout en bas de la pile, est chargé d'adapter la pile de canaux au transport sous-jacent (par exemple, au transport TCP, HTTP, SMTP ainsi qu'à d'autres types de transports). Les canaux fournissent un modèle de programmation de bas niveau pour l'envoi et la réception des messages. Ce modèle de programmation repose sur plusieurs interfaces et autres types collectivement appelés modèle de canal WCF. Cette rubrique aborde les thèmes suivants : formes de canal, construction d'un écouteur de canal de base (côté service) et fabrication de canal (côté client).  
  
## <a name="channel-stack"></a>Pile de canaux  

 Les points de terminaison WCF communiquent avec le monde à l’aide d’une pile de communication appelée pile de canaux. Le diagramme suivant compare la pile de canaux avec d'autres piles de communication, notamment avec la pile TCP/IP.  
  
 ![Modèle de canal](./media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Pour commencer, leurs points communs : chaque couche de la pile fournit une abstraction du monde figurant en dessous d'elle et expose cette abstraction uniquement à la couche se trouvant immédiatement au-dessus d'elle. Chaque couche utilise uniquement l'abstraction de la couche se trouvant immédiatement en dessous d'elle. Lorsque deux piles communiquent, chacune de leurs couches communique avec la couche lui correspondant de l'autre pile, par exemple la couche IP avec la couche IP, la couche TCP avec la couche TCP, etc.  
  
 À présent, leurs différences : alors que la pile TCP a été conçue pour fournir une abstraction du réseau physique, la pile de canaux a été conçue pour fournir une abstraction de la manière dont les messages sont remis, à savoir le transport, mais également pour fournir d’autres fonctionnalités permettant de connaître le contenu des messages, le protocole utilisé pour communiquer (notamment le transport), etc. Par exemple, l’élément de liaison de session fiable fait partie de la pile de canaux mais ne figure pas en dessous du transport ou du transport lui-même. Pour obtenir une abstraction, le canal inférieur dans la pile doit adapter le protocole de transport sous-jacent à l'architecture de la pile de canaux, puis en s'appuyant sur les canaux figurant plus haut dans la pile doit fournir des fonctionnalités de communication, notamment en matière de garanties de fiabilité et de sécurité.  
  
 Les messages circulent via la pile de communication sous forme d'objets <xref:System.ServiceModel.Channels.Message>. Comme illustré sur le schéma ci-dessus, le canal inférieur est appelé canal de transport. Ce canal est chargé de l'envoi des messages depuis leur expéditeur et de leur réception par leur destinataire. Il lui incombe notamment de transformer l'objet <xref:System.ServiceModel.Channels.Message> dans le format utilisé pour communiquer avec les autres correspondants. Au-dessus de ce canal de transport, peuvent figurer un nombre indéfini de canaux de protocole, chacun d'entre eux offrant des fonctionnalités de communication spécifiques, par exemple en matière de garantie de remise fiable. Les canaux de protocole interviennent sur les messages qui circulent dans la pile sous forme d'objet <xref:System.ServiceModel.Channels.Message>. En principe, leur tâche consiste à transformer ces messages, par exemple en y ajoutant des en-têtes ou en chiffrant leur contenu. Elle peut également consister à envoyer ou recevoir leurs propres messages de contrôle de protocole, par exemple des accusés de réception.  
  
## <a name="channel-shapes"></a>Formes de canal  

 Chaque canal implémente une ou plusieurs interfaces également désignées par les termes « interfaces de forme de canal » ou « formes de canal ». Ces formes de canal fournissent des méthodes orientées communication, par exemple les méthodes « envoyer et recevoir » ou « demande-réponse » implémentées par le canal ou appelées par l'utilisateur du canal. La base des formes de canal est l' <xref:System.ServiceModel.Channels.IChannel> interface, qui est une interface qui fournit une `GetProperty` \<T> méthode conçue comme un mécanisme superposé pour accéder aux fonctionnalités arbitraires exposées par les canaux de la pile. Les cinq formes de canal qui étendent un objet <xref:System.ServiceModel.Channels.IChannel> sont :  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 À chacune de ces formes correspond un équivalent qui étend <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> pour prendre en charge des sessions. Celles-ci sont les suivantes :  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Les modèles des formes de canal s’inspirent de certains des principaux modèles d’échange de messages pris en charge par les protocoles de transport existants. Par exemple, la messagerie unidirectionnelle correspond à une <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> paire, demande-réponse correspond aux <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> paires et les communications duplex bidirectionnelles correspondent à <xref:System.ServiceModel.Channels.IDuplexChannel> (qui étend à la fois <xref:System.ServiceModel.Channels.IInputChannel> et <xref:System.ServiceModel.Channels.IOutputChannel> ).  
  
## <a name="programming-with-the-channel-stack"></a>Programmation avec la pile de canaux  

 Les piles de canaux sont créées en principe à l'aide d'un modèle de fabrication, plus précisément à l'aide de liaisons. Du côté expédition, une liaison est utilisée pour générer une fabrication <xref:System.ServiceModel.ChannelFactory>, qui génère ensuite une pile de canaux et renvoie une référence au canal figurant en haut de la pile. L'application peut utiliser ensuite ce canal pour envoyer des messages. Pour plus d’informations, consultez Channel-Level de la [programmation du client](client-channel-level-programming.md).  
  
 Du côté réception, une liaison est utilisée pour générer un écouteur <xref:System.ServiceModel.Channels.IChannelListener>, qui écoute les messages entrants. L'écouteur <xref:System.ServiceModel.Channels.IChannelListener> envoie des messages à l'application écoutant en créant des piles de canaux et en remettant la référence d'application au canal supérieur. L'application utilise ensuite ce canal pour recevoir les messages entrants. Pour plus d’informations, consultez [Service Channel-Level programmation](service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Modèle d'objet de canal  

 Le modèle d'objet de canal correspond à l'ensemble principal d'interfaces nécessaire à l'implémentation des canaux, des écouteurs de canal et des fabrications de canaux. Certaines classes de base sont également disponibles pour faciliter les implémentations personnalisées.  
  
 Les écouteurs de canal sont chargés d'écouter les messages entrants, puis de les remettre à la couche supérieure à l'aide des canaux qu'ils ont eux-mêmes créés.  
  
 Les fabrications de canaux sont chargées de créer les canaux utilisés pour l'envoi des messages et de fermer ces mêmes canaux à leur propre fermeture.  
  
 <xref:System.ServiceModel.ICommunicationObject> est la principale interface qui définit la machine à états de base que tous les objets de communication implémentent. <xref:System.ServiceModel.Channels.CommunicationObject> fournit une implémentation de cette interface principale dont d'autres classes de canal peuvent dériver au lieu de réimplémenter l'interface. Toutefois, ceci n'est pas obligatoire : un canal personnalisé peut implémenter <xref:System.ServiceModel.ICommunicationObject> directement et ne pas hériter de <xref:System.ServiceModel.Channels.CommunicationObject>. Aucune des classes de l'illustration 3 n'est considérée comme faisant partie du modèle de canal. Elles sont disponibles afin d'aider les implémenteurs de canaux personnalisés à construire ces derniers.  
  
 ![Modèle de canal](./media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Les rubriques suivantes contiennent des informations sur le modèle d'objet de canal ainsi que sur diverses zones de développement qui facilitent la construction de canaux personnalisés.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Service : Écouteurs de canal et canaux](service-channel-listeners-and-channels.md)|Contient des informations sur les écouteurs de canal, qui écoutent les canaux entrants dans une application de service.|  
|[Client : Fabrications de canaux et canaux](client-channel-factories-and-channels.md)|Contient des informations sur les fabrications de canaux, lesquelles créent des canaux pour pouvoir se connecter aux applications de service.|  
|[Fonctionnement des modifications d'état](understanding-state-changes.md)|Contient des informations qui expliquent comment l'état des modèles d'interface <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> change dans les canaux.|  
|[Sélection d’un modèle d’échange de messages](choosing-a-message-exchange-pattern.md)|Présente les six modèles d’échange de messages de base pris en charge par les canaux.|  
|[Gestion des exceptions et des erreurs](handling-exceptions-and-faults.md)|Contient des instructions indiquant comment gérer les erreurs et les exceptions qui surviennent sur les canaux personnalisés.|  
|[Prise en charge de la configuration et des métadonnées](configuration-and-metadata-support.md)|Contient des instructions indiquant comment procéder pour assurer la prise en charge des canaux personnalisés à partir du modèle d’application ainsi que pour exporter et importer des métadonnées à l’aide de liaisons et d’éléments de liaison.|
