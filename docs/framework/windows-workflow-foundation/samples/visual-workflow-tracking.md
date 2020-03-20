---
title: Suivi de workflow visuel
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 22c91a12bba148e1fa823bb2bf9b3eaf16704c46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182750"
---
# <a name="visual-workflow-tracking"></a>Suivi de workflow visuel
Cet exemple montre comment écrire une application de suivi de workflow visuel à l'aide des fonctionnalités de débogage disponibles via le [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].

## <a name="sample-details"></a>Détails de l'exemple
 L'application exécute un workflow d'organigramme simple (défini dans Workflow.xaml) et héberge à nouveau le concepteur de workflow pour afficher le workflow en cours d'exécution. Lorsque le workflow est exécuté, l'activité en cours d'exécution est indiquée par un contour jaune et une flèche de débogage. En outre, les enregistrements de suivi générés par le workflow s'affichent également dans la fenêtre d'application. Pour plus d’informations sur le suivi des flux de travail, voir [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md). Pour plus d’informations sur la ré-hébergement du concepteur de flux de travail, voir [Rehosting le concepteur de flux de travail](../rehosting-the-workflow-designer.md).

 Le simulateur de workflow fonctionne en conservant deux dictionnaires. L'un contient un mappage entre l'objet d'activité en cours d'exécution et le numéro de ligne XAML dans lequel l'activité est instanciée. L'autre contient un mappage entre l'ID de l'instance d'activité et l'objet d'activité. Lorsque les enregistrements de suivi sont émis à l'aide d'un modèle de suivi personnalisé, l'application détermine l'ID d'instance de l'activité en cours d'exécution et le mappe à nouveau au fichier XAML qui l'a instancié. Le concepteur de workflow réhébergé a ensuite pour instruction de mettre en surbrillance l'activité sur l'aire du concepteur et d'utiliser la même méthode que le débogueur de workflow, en dessinant spécifiquement une bordure jaune autour de l'activité et en affichant une flèche jaune le long du côté gauche du concepteur.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. Ouvrez le fichier WorkflowSimulator.sln à partir du répertoire de l’échantillon dans Visual Studio 2010.

2. Appuyez sur Ctrl+Maj+B pour générer la solution.

3. Appuyez sur CTRL+F5 pour exécuter l'exemple. Cela affiche le fichier Workflow.xaml dans une fenêtre de concepteur de workflow réhébergé.

4. Cliquez sur le menu **Fichier** et **sélectionnez Run Workflow...**.

5. Notez que l'activité en cours d'exécution est mise en surbrillance comme décrit précédemment et que les enregistrements de suivi sont affichés à le côté droit de la fenêtre d'application.

6. Lorsque le workflow est terminé, vous pouvez cliquer sur l'un des enregistrements de suivi pour vérifier à quelle activité il correspond.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`
