---
title: Programmation de l'arborescence des éléments de modèle
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 059bb3edcfe41f52e2244ff6f5bf3fc78a4262bb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235803"
---
# <a name="programming-model-item-tree"></a>Programmation de l'arborescence des éléments de modèle

Cet exemple montre comment naviguer dans l' <xref:System.Activities.Presentation.Model.ModelItem> arborescence à l’aide de la liaison de données déclarative à partir de l’arborescence Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Détails de l'exemple

 L' <xref:System.Activities.Presentation.Model.ModelItem> arborescence est l’abstraction utilisée par l’infrastructure de concepteur de flux de travail Windows pour exposer les données relatives à l’instance sous-jacente en cours de modification. L’illustration suivante est une représentation des différentes couches d’infrastructure au sein du Concepteur de flux de travail.

 ![Diagramme qui montre l’architecture Concepteur de flux de travail.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 Un <xref:System.Activities.Presentation.Model.ModelItem> se compose d'un pointeur vers la valeur sous-jacente, ainsi que d'une collection d'objets <xref:System.Activities.Presentation.Model.ModelProperty>. Un objet <xref:System.Activities.Presentation.Model.ModelProperty>, quant à lui, se compose de données telles que le nom et le type de la propriété, puis d'un pointeur vers la valeur qui, à son tout, est un autre <xref:System.Activities.Presentation.Model.ModelItem>. Un convertisseur de valeurs est utilisé pour manipuler certains des <xref:System.Activities.Presentation.Model.ModelItem> retournés à partir d’un <xref:System.Activities.Presentation.Model.ModelProperty> pour les faire apparaître correctement dans l’arborescence. L’exemple montre ensuite comment effectuer une programmation de façon impérative sur l’arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l’aide de la syntaxe impérative.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. Ouvrez la solution ProgrammingModelItemTree. sln dans Visual Studio 2010.

2. Générez la solution en sélectionnant **générer la solution** dans le menu **générer** .

3. Appuyez sur F5 pour exécuter l'application. Le formulaire WPF s’affiche alors.

4. Cliquez sur le bouton **charger WF** pour charger <xref:System.Activities.Presentation.Model.ModelItem> et le lier à l’arborescence.

5. En cliquant sur le bouton **modifier l’arborescence d’éléments de modèle** , vous exécutez le code précédent pour ajouter un élément à l’arborescence et définir une propriété.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.IValueConverter>
