---
title: Corrélation demande-réponse
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: 34a41a149e740faf0f3816bba2c9bd9b47d4996e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184542"
---
# <a name="request-reply-correlation"></a>Corrélation demande-réponse
La corrélation demande-réponse <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> est utilisée avec une paire pour implémenter <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> une opération bidirectionnel dans un service de flux de travail et avec une paire qui invoque une opération bidirectionnel dans un autre service Web. Lors de l’invocation d’une opération bidirectionnelle dans un service WCF, le service peut être soit un service traditionnel impératif basé sur le code Windows Communication Foundation (WCF) ou il peut être un service de flux de travail. Pour utiliser la corrélation demande-réponse, une liaison bidirectionnelle doit être utilisée, telle que <xref:System.ServiceModel.BasicHttpBinding>. Qu'il s'agisse d'appeler ou d'implémenter une opération bidirectionnelle, les étapes d'initialisation de la corrélation sont similaires ; elles sont présentées dans cette section.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Utilisation de la corrélation dans une opération bidirectionnelle avec Receive/SendReply  
 <xref:System.ServiceModel.Activities.Receive> / Une <xref:System.ServiceModel.Activities.SendReply> paire est utilisée pour mettre en œuvre une opération bidirectionnel dans un service de flux de travail. L'exécution utilise la corrélation demande-réponse pour vérifier que la réponse est distribuée à l'appelant approprié. Lorsqu'un workflow est hébergé à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>, ce qui est le cas des services de workflow, l'initialisation de la corrélation par défaut est suffisante. Dans ce scénario, une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est utilisée par un flux de travail, et aucune configuration de corrélation spécifique n’est requise.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Initialisation explicite de la corrélation demande-réponse  
 Si d'autres opérations bidirectionnelles existent en parallèle, la corrélation doit être configurée de manière explicite. Cela peut être fait <xref:System.ServiceModel.Activities.CorrelationHandle> en <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>spécifiant <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> un <xref:System.ServiceModel.Activities.CorrelationScope>et , ou en plaçant l’intérieur d’un . Dans cet exemple, la corrélation demande-réponse est configurée sur une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire.  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 Au lieu de configurer la corrélation de manière explicite, une activité <xref:System.ServiceModel.Activities.CorrelationScope> peut être utilisée. <xref:System.ServiceModel.Activities.CorrelationScope> fournit un <xref:System.ServiceModel.Activities.CorrelationHandle> implicite aux activités de messagerie qu'il contient. Dans cet exemple, une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire <xref:System.ServiceModel.Activities.CorrelationScope>est contenue à l’intérieur d’un . Aucune configuration de corrélation explicite n'est nécessaire.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 Si nécessaire, des corrélations supplémentaires peuvent être configurées à l'aide de la propriété <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> des activités de messagerie respectives utilisant les types `CorrelationInitializer` souhaités.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Utilisation de la corrélation dans une opération bidirectionnelle avec Send/ReceiveReply  
 Alors <xref:System.ServiceModel.Activities.Receive> que l’activité ne peut être utilisée <xref:System.ServiceModel.Activities.WorkflowServiceHost>que <xref:System.ServiceModel.Activities.Send> dans <xref:System.ServiceModel.Activities.Send> / un service de flux de travail hébergé par , et la <xref:System.ServiceModel.Activities.ReceiveReply> paire peut être utilisée dans n’importe quel flux de travail qui doit invoquer une méthode sur un service Web. Si le workflow est hébergé à l'aide de l'objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la corrélation par défaut décrite dans la section précédente s'applique, mais si ce n'est pas le cas, la corrélation doit être configurée soit de manière explicite à l'aide des objets <xref:System.ServiceModel.Activities.CorrelationInitializer> et <xref:System.ServiceModel.Activities.CorrelationHandle> souhaités, soit en utilisant la gestion de handle implicite de l'objet <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Lors de l’utilisation **de Add Service Reference** sur un <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> service avec des opérations bidirectionnels, des activités sont générées qui enveloppent une activité de paire en interne avec la corrélation demande/réponse explicitement spécifiée.
