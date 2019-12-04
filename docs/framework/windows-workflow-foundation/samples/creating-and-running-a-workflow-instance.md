---
title: Création et exécution d'une instance de workflow
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715205"
---
# <a name="creating-and-running-a-workflow-instance"></a>Création et exécution d'une instance de workflow

Cet exemple montre comment exécuter une instance de workflow. Il indique comment l’exécuter de façon synchrone et de façon asynchrone.

## <a name="demonstrates"></a>Montre

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Discussion

La première partie de l'exemple utilise <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Il s'agit de la façon la plus simple d'exécuter un workflow. Les workflows exécutés avec <xref:System.Activities.WorkflowInvoker.Invoke%2A> s’exécutent de façon synchrone.

La deuxième partie de l'exemple utilise la classe <xref:System.Activities.WorkflowApplication>. <xref:System.Activities.WorkflowApplication> vous permet d'avoir plus de contrôle sur chaque instance, notamment la possibilité d'interagir avec le workflow en cours d'exécution et d'exécuter le workflow de façon asynchrone.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Voir aussi

- [Utilisation de WorkflowInvoker et WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)
