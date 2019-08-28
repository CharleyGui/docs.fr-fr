---
title: Programmation de l'arborescence des éléments de modèle
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f2d89cb2a3b0f6167f043148ea793ec1c264a556
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038171"
---
# <a name="programming-model-item-tree"></a>Programmation de l'arborescence des éléments de modèle
Cet exemple montre comment naviguer dans l' <xref:System.Activities.Presentation.Model.ModelItem> arborescence à l’aide de la liaison de données déclarative à partir de l’arborescence Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Détails de l'exemple
 L’arborescence <xref:System.Activities.Presentation.Model.ModelItem> est l’abstraction utilisée par l’infrastructure du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] pour exposer les données relatives à l’instance sous-jacente en cours de modification. L'illustration suivante est une description des différentes couches d'infrastructure dans le [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].

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
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.IValueConverter>
