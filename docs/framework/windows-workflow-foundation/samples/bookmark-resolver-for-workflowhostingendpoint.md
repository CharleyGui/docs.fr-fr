---
title: Programme de résolution de signets pour WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 113e6e52214d482dcd733bbd07ef2aab9f1b8c3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142808"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Programme de résolution de signets pour WorkflowHostingEndpoint
Cet exemple montre comment <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> peut être utilisé avec <xref:System.ServiceModel.Activities.WorkflowServiceHost> pour créer des instances de workflow.  
  
## <a name="demonstrates"></a>Illustre le  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Discussions  
 Cet exemple utilise <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pour créer des instances de workflow hébergées à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> est un point d'extensibilité pour <xref:System.ServiceModel.Activities.WorkflowServiceHost> qui peut être utilisé dans les scénarios suivants :  
  
- Création d'instances de workflow.  
  
- Reprise de signets sur une instance de workflow hébergée dans un <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 L'exemple de point de terminaison inclus expose un contrat qui fournit des opérations pour créer un workflow et retourne l'ID d'instance ou crée une instance avec un ID spécifique. L'exemple d'application console crée une instance <xref:System.ServiceModel.Activities.WorkflowServiceHost> avec une définition de workflow et ajoute un `CreationEndpoint` à l'hôte. Il fait alors appel à l'opération `Create` sur le point de terminaison pour créer une instance de workflow.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Générez la solution.  
  
2. Exécutez l'application. La console `CreationEndpoint` affiche un message qui inclut l'ID d'instance lorsque l'instance de workflow est créée. Le message "Bonjour monde!" est imprimé par l’instance du flux de travail.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
