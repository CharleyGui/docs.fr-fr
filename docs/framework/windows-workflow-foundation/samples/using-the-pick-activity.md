---
title: Utilisation de l'activité Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: df8570a61c7bfbfacc00b0896156135ecf2a0c32
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267453"
---
# <a name="using-the-pick-activity"></a>Utilisation de l'activité Pick

Cet exemple montre comment utiliser l'activité <xref:System.Activities.Statements.Pick>.

 L'activité <xref:System.Activities.Statements.Pick> fournit une modélisation de contrôle basée sur les événements. Le comportement est semblable à celui de l’instruction `switch` de C#, qui exécute une seule des branches dans l’instruction `switch`. Contrairement à l’instruction `switch` dans laquelle une branche est exécutée en fonction d’une valeur, l’activité <xref:System.Activities.Statements.Pick> exécute une branche en fonction de l’exécution d’une activité.

 Cet exemple invite un utilisateur à taper son nom sur la console dans une période de temps donné. L’activité <xref:System.Activities.Statements.Pick> dans l’exemple a deux branches qui sont exécutées selon si l’utilisateur tape son nom dans les 5 secondes ou non. Si l'utilisateur tape son nom dans les 5 secondes, la première branche, qui contient une activité `ReadLine` personnalisée est exécutée ; sinon, l'autre branche, qui contient une activité <xref:System.Activities.Statements.Delay> est exécutée. Une fois qu'un nom d'utilisateur est tapé sur la console, il est imprimé sur la console. Si rien n'est entré dans les 5 secondes, l'opération expire.

## <a name="demonstrates"></a>Illustre le

 Activité <xref:System.Activities.Statements.Pick>

## <a name="discussion"></a>Discussions

 L'exemple inclut un workflow de concepteur et un workflow encodé.

 Flux de travail du concepteur la version du concepteur de l’exemple montre comment créer un flux de travail dans le concepteur. Les fichiers suivants sont inclus :

- Program.cs : inclut la fonction `Main` qui exécute l'exemple de workflow.

- ReadString.cs : activité personnalisée qui lit une entrée de la console.

- Sequence1.xaml : workflow créé à l'aide du concepteur qui utilise Pick.

 Flux de travail codé la version codée de l’exemple montre comment créer un flux de travail dans le concepteur. Les fichiers suivants sont inclus :

- Program.cs : inclut la fonction `Main` qui exécute l'exemple de workflow.

- ReadString.cs : activité personnalisée qui lit une entrée de la console.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2010, ouvrez le fichier solution Pick. sln.

2. Pour générer la solution, appuyez sur Ctrl+Maj+B.

3. Pour exécuter la solution, appuyez sur F5.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
