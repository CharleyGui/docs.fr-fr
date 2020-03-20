---
title: Programmation de l'arborescence des éléments de modèle
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f14b140fdac95f3763cc5625841a725793876fa4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142691"
---
# <a name="programming-model-item-tree"></a>Programmation de l'arborescence des éléments de modèle
Cet exemple montre comment <xref:System.Activities.Presentation.Model.ModelItem> naviguer dans l’arbre à l’aide de données déclaratives liant de la Windows Presentation Foundation (WPF) Tree View.

## <a name="sample-details"></a>Détails de l'exemple
 L’arbre <xref:System.Activities.Presentation.Model.ModelItem> est l’abstraction qui est utilisée par l’infrastructure Windows Workflow Designer pour exposer les données sur l’instance sous-jacente en cours d’édition. L’illustration suivante est une représentation des différentes couches d’infrastructure au sein du Concepteur de flux de travail.

 ![Diagramme qui montre l’architecture Workflow Designer.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 Un <xref:System.Activities.Presentation.Model.ModelItem> se compose d'un pointeur vers la valeur sous-jacente, ainsi que d'une collection d'objets <xref:System.Activities.Presentation.Model.ModelProperty>. Un objet <xref:System.Activities.Presentation.Model.ModelProperty>, quant à lui, se compose de données telles que le nom et le type de la propriété, puis d'un pointeur vers la valeur qui, à son tout, est un autre <xref:System.Activities.Presentation.Model.ModelItem>. Un convertisseur de valeurs est utilisé pour manipuler certains des <xref:System.Activities.Presentation.Model.ModelItem> retournés à partir d’un <xref:System.Activities.Presentation.Model.ModelProperty> pour les faire apparaître correctement dans l’arborescence. L’exemple montre ensuite comment effectuer une programmation de façon impérative sur l’arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l’aide de la syntaxe impérative.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. Ouvrez la solution ProgrammingModelItemTree.sln dans Visual Studio 2010.

2. Construisez la solution en sélectionnant **la solution build** à partir du menu **Build.**

3. Appuyez sur F5 pour exécuter l'application. Le formulaire WPF est alors affiché.

4. Cliquez sur le bouton Load <xref:System.Activities.Presentation.Model.ModelItem> **WF** pour charger le et lier à la vue de l’arbre.

5. En cliquant sur le bouton **Modifier l’arbre d’élément modèle,** le code précédent exécute le code précédent pour ajouter un élément dans l’arbre et définir une propriété.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.IValueConverter>
