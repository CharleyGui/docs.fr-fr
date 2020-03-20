---
title: Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182769"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées
Cet exemple montre comment utiliser le <xref:System.Activities.Presentation.View.ExpressionTextBox> dans un concepteur d'activités personnalisées. L'activité personnalisée, `MultiAssign`, assigne deux valeurs de chaîne à deux variables String. Certains contrôles <xref:System.Activities.Presentation.View.ExpressionTextBox> sont liés à <xref:System.Activities.InArgument>s et d'autres à <xref:System.Activities.OutArgument>s.

## <a name="sample-details"></a>Détails de l'exemple
 Le `ArgumentToExpressionConverter` est le convertisseur de type utilisé lors de la liaison d’expressions aux arguments. Affectez `ConverterParameter` ou `In` à `Out`. La fonction `InOut` n'est pas prise en charge.

 L’attribut `UseLocationExpression` est `OutArgument`utilisé sur s pour spécifier que l’expression doit être une expression de valeur L (« valeur gauche » ou « valeur de localisation »). Dans la plupart des cas, une expression L-value est un identificateur Visual Basic valide utilisé pour indiquer que le `OutArgument` qui est retourné est un nom de variable ou d’argument.

 L'attribut `MaxLines` a la valeur un dans cet exemple et `MinLines` n'est pas défini. Cela indique que le <xref:System.Activities.Presentation.View.ExpressionTextBox> a une taille fixe d'une ligne indépendamment de la quantité de texte tapée par l'utilisateur. Pour permettre au <xref:System.Activities.Presentation.View.ExpressionTextBox> de s'agrandir pour s'ajuster à l'entrée d'utilisateur, affectez à `MaxLines` une valeur supérieure à `MinLines`.

 Un ExpressionTextBox peut être lié uniquement aux arguments et ne peut pas être lié aux propriétés CLR.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2010, ouvrez le fichier ExpressionTextBoxSample.sln.

2. Pour générer la solution, appuyez sur Ctrl+Maj+B.

#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple

1. Ajoutez une nouvelle application console de workflow à la solution.

2. Ajoutez une référence au projet **ExpressionTextBoxSample** du nouveau projet Workflow Console Application.

3. Générez la solution.

4. Faites glisser l’activité **MultiAssign** de la boîte à outils et laissez-la tomber dans le flux de travail.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Développement d’applications avec le Concepteur de flux de travail](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
