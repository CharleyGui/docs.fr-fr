---
title: Création et exécution d'une instance de workflow
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016049"
---
# <a name="creating-and-running-a-workflow-instance"></a>Création et exécution d'une instance de workflow

Cet exemple montre comment exécuter une instance de workflow. Il indique comment l’exécuter de façon synchrone et de façon asynchrone.

## <a name="demonstrates"></a>Démonstrations

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Discussion

La première partie de l'exemple utilise <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Il s'agit de la façon la plus simple d'exécuter un workflow. Les workflows exécutés avec <xref:System.Activities.WorkflowInvoker.Invoke%2A> s’exécutent de façon synchrone.

La deuxième partie de l'exemple utilise la classe <xref:System.Activities.WorkflowApplication>. <xref:System.Activities.WorkflowApplication> vous permet d'avoir plus de contrôle sur chaque instance, notamment la possibilité d'interagir avec le workflow en cours d'exécution et d'exécuter le workflow de façon asynchrone.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Voir aussi

- [Utilisation de WorkflowInvoker et WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)
