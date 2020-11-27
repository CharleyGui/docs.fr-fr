---
title: Formateurs de messages personnalisés
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: e238eb134772c0a95934a460edda62ca9dba2518
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254751"
---
# <a name="custom-message-formatters"></a>Formateurs de messages personnalisés

Le contenu d'un message est souvent au format XML, ce qui n'est pas généralement un format pratique pour une application. Les applications manipulent des objets, obtiennent et définissent leurs propriétés. Windows Communication Foundation (WCF) utilise le *contrat de données* pour convertir un <xref:System.ServiceModel.Channels.Message> objet en un objet facilement géré par une application. Ces processus sont appelés sérialisation et désérialisation. Notez que ces mêmes termes sont utilisés pour décrire la sérialisation et la désérialisation effectuées par la couche transport en direction et à partir du format de transmission de message, qui est un processus non apparenté.  
  
 Vous pouvez utiliser un formateur de messages personnalisés si vous devez implémenter une conversion spécialisée entre des messages et des objets que vous ne pouvez pas accomplir au moyen d'un contrat de données. Pour ce faire, modifiez ou étendez le comportement d'exécution d'une opération de contrat spécifique sur un client ou un service.  
  
## <a name="custom-message-formatters-on-the-client"></a>Formateurs de messages personnalisés sur le client  

 L'interface <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> définit les méthodes utilisées pour contrôler la conversion de messages en objets et d'objets en messages pour les applications clientes.  
  
 Vous devez implémenter cette interface. Commencez par substituer la méthode <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> pour désérialiser un message. Cette méthode est appelée après la réception d'un message entrant, mais avant sa distribution à l'opération cliente.  
  
 Puis, substituez la méthode <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> pour sérialiser un objet. Cette méthode est appelée avant l'envoi d'un message sortant.  
  
 Pour insérer le formateur personnalisé dans l'application de service, assignez l'objet <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> à la propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> à l'aide d'un comportement d'opération. Pour plus d’informations sur les comportements, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Formateurs de messages personnalisés sur le service  

 L'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> définit des méthodes qui convertissent un objet <xref:System.ServiceModel.Channels.Message> en paramètres pour une opération et de paramètres en objet <xref:System.ServiceModel.Channels.Message> dans une application de service.  
  
 Vous devez implémenter cette interface. Commencez par substituer la méthode <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> pour désérialiser un message. Cette méthode est appelée après la réception d'un message entrant, mais avant sa distribution à l'opération cliente.  
  
 Puis, substituez la méthode <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> pour sérialiser un objet. Cette méthode est appelée avant l'envoi d'un message sortant.  
  
 Pour insérer le formateur personnalisé dans l'application de service, assignez l'objet <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> à la propriété <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> à l'aide d'un comportement d'opération. Pour plus d’informations sur les comportements, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [Configuration et extension de l'exécution à l'aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md)
