---
title: Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: dfb53096be59abd9924a024880d4125ca774d4b8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267492"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées

Cet exemple montre comment utiliser le <xref:System.Activities.Presentation.View.ExpressionTextBox> dans un concepteur d'activités personnalisées. L'activité personnalisée, `MultiAssign`, assigne deux valeurs de chaîne à deux variables String. Certains contrôles <xref:System.Activities.Presentation.View.ExpressionTextBox> sont liés à <xref:System.Activities.InArgument>s et d'autres à <xref:System.Activities.OutArgument>s.

## <a name="sample-details"></a>Détails de l'exemple

 Le `ArgumentToExpressionConverter` est le convertisseur de type utilisé lors de la liaison d’expressions aux arguments. Affectez `ConverterParameter` ou `In` à `Out`. `InOut` n’est pas pris en charge.

 L' `UseLocationExpression` attribut est utilisé sur `OutArgument` s pour spécifier que l’expression doit être une expression L-value (« valeur de gauche » ou « valeur d’emplacement »). Dans la plupart des cas, une expression L-value est un identificateur Visual Basic valide utilisé pour indiquer que le `OutArgument` qui est retourné est un nom de variable ou d’argument.

 L'attribut `MaxLines` a la valeur un dans cet exemple et `MinLines` n'est pas défini. Cela indique que le <xref:System.Activities.Presentation.View.ExpressionTextBox> a une taille fixe d'une ligne indépendamment de la quantité de texte tapée par l'utilisateur. Pour permettre au <xref:System.Activities.Presentation.View.ExpressionTextBox> de s'agrandir pour s'ajuster à l'entrée d'utilisateur, affectez à `MaxLines` une valeur supérieure à `MinLines`.

 Un ExpressionTextBox peut être lié uniquement aux arguments et ne peut pas être lié aux propriétés CLR.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2010, ouvrez le fichier ExpressionTextBoxSample. sln.

2. Pour générer la solution, appuyez sur Ctrl+Maj+B.

#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple

1. Ajoutez une nouvelle application console de workflow à la solution.

2. Ajoutez une référence au projet **ExpressionTextBoxSample** à partir du nouveau projet d’application console de Workflow.

3. Générez la solution.

4. Faites glisser l’activité **MultiAssign** à partir de la boîte à outils et déposez-la dans le Workflow.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Développement d’applications avec le Concepteur de flux de travail](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
