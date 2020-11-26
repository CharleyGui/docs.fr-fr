---
title: Gestion des erreurs WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 72db5db9f6b4a3cd2ba62fe938fcfeed2dfda1e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240938"
---
# <a name="wcf-error-handling"></a>Gestion des erreurs WCF

Les erreurs rencontrées par une application WCF appartiennent à l'un de ces trois groupes :  
  
1. Erreurs de communication  
  
2. Erreurs de proxy/canal  
  
3. Erreurs d'application  
  
 Les erreurs de communication se produisent lorsqu'un réseau n'est pas disponible, lorsqu'un client utilise une adresse incorrecte ou lorsque l'hôte de service n'écoute pas les messages entrants. Des erreurs de ce type sont retournées au client comme classes dérivées <xref:System.ServiceModel.CommunicationException> ou <xref:System.ServiceModel.CommunicationException>.  
  
 Les erreurs de proxy/canal sont des erreurs qui se produisent dans le canal ou le proxy lui-même. Les erreurs de ce type incluent : une tentative d'utilisation d'un proxy ou d'un canal qui a été fermé, des contrats qui ne correspondent pas entre le client et le service ou des informations d'identification de client rejetées par le service. Cette catégorie inclut de nombreux types différents d'erreurs, qu'il serait trop long d'énumérer ici. Les erreurs de ce type sont retournées au client en l'état (les objets d'exception ne subissent aucune transformation).  
  
 Les erreurs d'application se produisent au cours de l'exécution d'une opération de service. Les erreurs se ce genre sont envoyées au client en tant que <xref:System.ServiceModel.FaultException> ou <xref:System.ServiceModel.FaultException%601>.  
  
 Le traitement des erreurs dans WCF est effectué par un ou plusieurs des éléments suivants :  
  
- Traitement direct de l'exception levée. Uniquement effectué pour les erreurs de communication et de proxy/canal.  
  
- Utilisation des contrats d'erreur  
  
- Implémentation de l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>  
  
- Gestion des événements <xref:System.ServiceModel.ServiceHost>  
  
## <a name="fault-contracts"></a>Contrats d'erreur  

 Les contrats d'erreur vous permettent de définir les erreurs qui peuvent se produire au cours du fonctionnement du service de façon indépendante de la plate-forme. Par défaut, toutes les exceptions levées à partir d'une opération de service seront retournées au client en tant qu'objet <xref:System.ServiceModel.FaultException>. L'objet <xref:System.ServiceModel.FaultException> contiendra très peu d'informations. Vous pouvez contrôler les informations envoyées au client en définissant un contrat d'erreur et en retournant l'erreur en tant que <xref:System.ServiceModel.FaultException%601>. Pour plus d’informations, consultez [spécification et gestion des erreurs dans les contrats et les services](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  

 L'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> vous permet de mieux contrôler la façon dont votre application WCF répond aux erreurs.  Elle vous donne le contrôle total sur les messages d'erreur retournés au client et vous permet un traitement d'erreur personnalisé tel que la journalisation.  Pour plus d’informations sur et sur l' <xref:System.ServiceModel.Dispatcher.IErrorHandler> [extension du contrôle sur la gestion des erreurs et la création de rapports](./samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>Événements ServiceHost  

 La classe <xref:System.ServiceModel.ServiceHost> héberge les services et définit plusieurs événements qui peuvent être nécessaires au traitement des erreurs. Par exemple :  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Pour plus d'informations, consultez <xref:System.ServiceModel.ServiceHost>
