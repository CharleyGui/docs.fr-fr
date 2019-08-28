---
title: Charge à partir du XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: 2f45beb398e6d6b91bf7444dd590b862ff8c7515
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038083"
---
# <a name="load-from-xaml"></a>Charge à partir du XAML
Cet exemple montre comment charger dynamiquement un workflow XAML sans devoir exécuter l'outil XamlBuildTask. Au lieu de cela, l'exemple appelle la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>. L’exemple est une application cliente Windows Presentation Foundation (WPF) qui charge les workflows XAML <xref:System.Activities.XamlIntegration.ActivityXamlServices> à l’aide de la classe et les exécute. Une fois qu'ils ont été chargés à l'aide de la classe <xref:System.Activities.XamlIntegration.ActivityXamlServices>, un <xref:System.Activities.DynamicActivity%601> pouvant être exécuté est retourné.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2010, ouvrez le fichier solution LoadFromXAML. sln.

2. Pour générer la solution, appuyez sur Ctrl+Maj+B.

3. Pour exécuter la solution, appuyez sur Ctrl+F5.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
