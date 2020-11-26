---
title: Corrélation demande-réponse
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: da7739af7368cd7ebb55ed0ea2511e10f0bcb3f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239066"
---
# <a name="request-reply-correlation"></a>Corrélation demande-réponse

La corrélation demande-réponse est utilisée avec une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire pour implémenter une opération bidirectionnelle dans un service de workflow et avec une <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire qui appelle une opération bidirectionnelle dans un autre service Web. Lors de l’appel d’une opération bidirectionnelle dans un service WCF, le service peut être soit un service de Windows Communication Foundation basé sur le code impératif traditionnel, soit un service de flux de travail. Pour utiliser la corrélation demande-réponse, une liaison bidirectionnelle doit être utilisée, telle que <xref:System.ServiceModel.BasicHttpBinding>. Qu'il s'agisse d'appeler ou d'implémenter une opération bidirectionnelle, les étapes d'initialisation de la corrélation sont similaires ; elles sont présentées dans cette section.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Utilisation de la corrélation dans une opération bidirectionnelle avec Receive/SendReply  

 Une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est utilisée pour implémenter une opération bidirectionnelle dans un service de Workflow. L'exécution utilise la corrélation demande-réponse pour vérifier que la réponse est distribuée à l'appelant approprié. Lorsqu'un workflow est hébergé à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>, ce qui est le cas des services de workflow, l'initialisation de la corrélation par défaut est suffisante. Dans ce scénario, une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est utilisée par un workflow et aucune configuration de corrélation spécifique n’est requise.  
  
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

 Si d'autres opérations bidirectionnelles existent en parallèle, la corrélation doit être configurée de manière explicite. Pour ce faire, vous pouvez spécifier un <xref:System.ServiceModel.Activities.CorrelationHandle> et un <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> , ou placer l' <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> intérieur d’un <xref:System.ServiceModel.Activities.CorrelationScope> . Dans cet exemple, la corrélation demande-réponse est configurée sur une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire.  
  
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
  
 Au lieu de configurer la corrélation de manière explicite, une activité <xref:System.ServiceModel.Activities.CorrelationScope> peut être utilisée. <xref:System.ServiceModel.Activities.CorrelationScope> fournit un <xref:System.ServiceModel.Activities.CorrelationHandle> implicite aux activités de messagerie qu'il contient. Dans cet exemple, une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est contenue dans un <xref:System.ServiceModel.Activities.CorrelationScope> . Aucune configuration de corrélation explicite n'est nécessaire.  
  
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

 Alors que l' <xref:System.ServiceModel.Activities.Receive> activité ne peut être utilisée que dans un service de workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost> , <xref:System.ServiceModel.Activities.Send> et la <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire peut être utilisée dans un flux de travail qui doit appeler une méthode sur un service Web. Si le workflow est hébergé à l'aide de l'objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la corrélation par défaut décrite dans la section précédente s'applique, mais si ce n'est pas le cas, la corrélation doit être configurée soit de manière explicite à l'aide des objets <xref:System.ServiceModel.Activities.CorrelationInitializer> et <xref:System.ServiceModel.Activities.CorrelationHandle> souhaités, soit en utilisant la gestion de handle implicite de l'objet <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Lors de l’utilisation de **Ajouter une référence de service** sur un service avec des opérations bidirectionnelles, les activités sont générées qui encapsulent une <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> activité de paire en interne avec la corrélation demande/réponse explicitement spécifiée.
