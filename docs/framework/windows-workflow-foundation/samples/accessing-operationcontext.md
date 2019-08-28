---
title: Accès à OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 8d1c8543180a282a1b196393e5823dc3686aa16e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038406"
---
# <a name="accessing-operationcontext"></a>Accès à OperationContext
Cet exemple montre comment les activités de messagerie<xref:System.ServiceModel.Activities.Receive> ( <xref:System.ServiceModel.Activities.Send>et) peuvent être utilisées avec une activité d’étendue personnalisée <xref:System.ServiceModel.OperationContext.Current%2A> pour accéder à et attacher ou récupérer un en-tête de message personnalisé dans un message sortant ou entrant.  
  
## <a name="demonstrates"></a>Démonstrations  
 Activités de messagerie, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Discussion  
 Cet exemple montre comment utiliser des points d'extensibilité (<xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) dans les activités de messagerie pour accéder à <xref:System.ServiceModel.OperationContext.Current%2A>. Les rappels sont inscrits dans le runtime du workflow sous la forme d'une implémentation d'<xref:System.Activities.IExecutionProperty> qui est choisie par les activités de messagerie lors de l'exécution. Toute activité de messagerie de la même étendue que cette implémentation <xref:System.Activities.IExecutionProperty> est affectée. Plus particulièrement, cet exemple utilise une activité d'étendue personnalisée pour appliquer le comportement de rappel. <xref:System.ServiceModel.Activities.ISendMessageCallback> est utilisé dans le workflow client pour inclure l'<xref:System.Activities.WorkflowApplication.Id%2A> du workflow en tant que <xref:System.ServiceModel.Channels.MessageHeader> sortant. Cet en-tête est ensuite choisi dans le service à l'aide d'<xref:System.ServiceModel.Activities.IReceiveMessageCallback> et la valeur de l'en-tête est imprimée sur la console.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP. Pour exécuter cet exemple, des listes de contrôle d’accès d’URL appropriées doivent être ajoutées (pour plus d’informations, consultez [configuration de http et HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) ), soit en exécutant Visual Studio en tant qu’administrateur, soit en exécutant la commande suivante à une invite de commandes avec élévation de privilèges pour ajouter les listes de contrôle d’accès appropriées. Vérifiez que vos domaine et nom d'utilisateur sont substitués.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Une fois les listes de contrôle d'accès (ACL) d'URL ajoutées, effectuez les étapes suivantes.  
  
    1. Générez la solution.  
  
    2. Pour définir plusieurs projets de démarrage, cliquez avec le bouton droit sur la solution et sélectionnez **définir les projets de démarrage**.  
  
    3. Ajoutez le **service** et le **client** (dans cet ordre) en tant que plusieurs projets de démarrage.  
  
    4. Exécutez l'application. La console cliente affiche un workflow qui est exécuté deux fois et la fenêtre Service affiche l'ID d'instance de ces workflows.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
