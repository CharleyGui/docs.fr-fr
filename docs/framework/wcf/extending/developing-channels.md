---
title: Développement de canaux
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 11e7a78282a3c9f7cd221e2ef44bc43c625e447b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286797"
---
# <a name="developing-channels"></a>Développement de canaux

Le développement d’un protocole ou d’un canal de transport pouvant être utilisé avec la couche d’application Windows Communication Foundation (WCF) requiert plusieurs étapes. Cette rubrique liste ces étapes et renvoie à des rubriques spécifiques qui vous permettront d'en savoir plus. Pour comprendre le modèle de canal et les différents types mentionnés dans cette rubrique, consultez [vue d’ensemble du modèle de canal](channel-model-overview.md). Pour obtenir un exemple complet de canal de transport, consultez [transport : UDP](../samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Liste des tâches à effectuer dans le cadre du développement d'un canal  

 Les étapes pour créer un canal défini par l'utilisateur sont les suivantes : Pour tous les canaux :  
  
1. Choisissez quel modèle d’échange de messages de canal (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IReplyChannel>) que vos <xref:System.ServiceModel.Channels.IChannelFactory> et <xref:System.ServiceModel.Channels.IChannelListener> prendront en charge. Décidez également si ces derniers devront prendre en charge les versions avec session de ces interfaces. Pour plus d’informations, consultez [choix d’un modèle d’échange de messages](choosing-a-message-exchange-pattern.md).  
  
2. Créez une fabrication de canal ainsi qu’un écouteur (<xref:System.ServiceModel.Channels.IChannelFactory> et <xref:System.ServiceModel.Channels.IChannelListener>) qui prennent en charge votre modèle d’échange de messages. Pour plus d’informations sur le développement de fabriques, consultez [client : fabriques de canaux et canaux](client-channel-factories-and-channels.md). Pour plus d’informations sur le développement d’écouteurs, consultez [service : écouteurs de canal et canaux](service-channel-listeners-and-channels.md).  
  
3. Assurez-vous que toutes les exceptions spécifiques au réseau sont normalisées en fonction de <xref:System.TimeoutException?displayProperty=nameWithType> ou de la classe dérivée appropriée de <xref:System.ServiceModel.CommunicationException>. Pour plus d’informations, consultez [gestion des exceptions et des erreurs](handling-exceptions-and-faults.md).  
  
4. Pour permettre une utilisation depuis la couche d'application, ajoutez un <xref:System.ServiceModel.Channels.BindingElement> qui ajoute votre canal personnalisé à la pile des canaux. Pour plus d’informations, consultez [création d’un BindingElement](creating-a-bindingelement.md).  
  
 Les étapes supplémentaires suivantes sont requises pour permettre une prise en charge plus exhaustive au niveau de la couche d'application :  
  
1. Ajoutez une section d’extension d’élément de liaison afin d’exposer le nouvel élément de liaison au système de configuration. Pour plus d’informations, consultez [configuration et prise en charge des métadonnées](configuration-and-metadata-support.md).  
  
2. Ajoutez des extensions de métadonnées pour communiquer des fonctionnalités à d'autres points de terminaison. Pour plus d’informations, consultez [configuration et prise en charge des métadonnées](configuration-and-metadata-support.md).  
  
3. Ajoutez une liaison qui préconfigure une pile d’éléments de liaison d’après un profil bien défini. Pour plus d’informations, consultez [création de liaisons de User-Defined](creating-user-defined-bindings.md).  
  
4. Ajoutez une section de liaison ainsi qu'un élément de configuration de liaison afin d'exposer la liaison au système de configuration. Pour plus d’informations, consultez [configuration et prise en charge des métadonnées](configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Voir aussi

- [Extension de liaisons](extending-bindings.md)
