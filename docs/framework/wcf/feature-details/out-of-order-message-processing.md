---
title: Traitement des messages dans le désordre
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7930f26cf5957158a16d65085267cf1bab2e4504
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598721"
---
# <a name="out-of-order-message-processing"></a>Traitement des messages dans le désordre
Les services de workflow peuvent dépendre de l'ordre dans lequel sont envoyés les messages. Un service de workflow contient une ou plusieurs activités <xref:System.ServiceModel.Activities.Receive> et chaque activité <xref:System.ServiceModel.Activities.Receive> attend un message spécifique. Sans garanties particulières de remise par le transport, les messages envoyés par des clients peuvent être différés et par conséquent remis dans un ordre non prévu par le service de workflow. L'implémentation d'un service de workflow qui ne requiert aucun ordre particulier d'envoi des messages s'effectue en principe à l'aide d'une activité Parallèle. Pour un protocole d'application plus complexe, le workflow risque de se compliquer très rapidement.  La fonctionnalité de traitement des messages non ordonnés dans Windows Communication Foundation (WCF) vous permet de créer un tel flux de travail sans la complexité des activités parallèles imbriquées. Le traitement des messages en désordre n’est pris en charge que sur les canaux qui prennent en charge <xref:System.ServiceModel.Channels.ReceiveContext> , tels que les liaisons MSMQ WCF.  
  
## <a name="enabling-out-of-order-message-processing"></a>Activation du traitement des messages dans le désordre  
 Le traitement des messages dans le désordre est activé en définissant la propriété <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> à la valeur `true` dans le WorkflowService. L'exemple suivant montre comment définir la propriété <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> dans le code.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Vous pouvez également appliquer l'attribut `AllowBufferedReceive` à un service de workflow en XAML, comme indiqué dans l'exemple suivant.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [Services de workflow](workflow-services.md)
- [Files d'attente et sessions fiables](queues-and-reliable-sessions.md)
