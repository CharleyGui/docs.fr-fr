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
# <a name="programming-model-item-tree"></a><span data-ttu-id="8e6e5-102">Programmation de l'arborescence des éléments de modèle</span><span class="sxs-lookup"><span data-stu-id="8e6e5-102">Programming Model Item Tree</span></span>
<span data-ttu-id="8e6e5-103">Cet exemple montre comment <xref:System.Activities.Presentation.Model.ModelItem> naviguer dans l’arbre à l’aide de données déclaratives liant de la Windows Presentation Foundation (WPF) Tree View.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="8e6e5-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="8e6e5-104">Sample Details</span></span>
 <span data-ttu-id="8e6e5-105">L’arbre <xref:System.Activities.Presentation.Model.ModelItem> est l’abstraction qui est utilisée par l’infrastructure Windows Workflow Designer pour exposer les données sur l’instance sous-jacente en cours d’édition.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="8e6e5-106">L’illustration suivante est une représentation des différentes couches d’infrastructure au sein du Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-106">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![Diagramme qui montre l’architecture Workflow Designer.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="8e6e5-108">Un <xref:System.Activities.Presentation.Model.ModelItem> se compose d'un pointeur vers la valeur sous-jacente, ainsi que d'une collection d'objets <xref:System.Activities.Presentation.Model.ModelProperty>.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="8e6e5-109">Un objet <xref:System.Activities.Presentation.Model.ModelProperty>, quant à lui, se compose de données telles que le nom et le type de la propriété, puis d'un pointeur vers la valeur qui, à son tout, est un autre <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="8e6e5-110">Un convertisseur de valeurs est utilisé pour manipuler certains des <xref:System.Activities.Presentation.Model.ModelItem> retournés à partir d’un <xref:System.Activities.Presentation.Model.ModelProperty> pour les faire apparaître correctement dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="8e6e5-111">L’exemple montre ensuite comment effectuer une programmation de façon impérative sur l’arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l’aide de la syntaxe impérative.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="8e6e5-112">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="8e6e5-112">To use this sample</span></span>

1. <span data-ttu-id="8e6e5-113">Ouvrez la solution ProgrammingModelItemTree.sln dans Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="8e6e5-114">Construisez la solution en sélectionnant **la solution build** à partir du menu **Build.**</span><span class="sxs-lookup"><span data-stu-id="8e6e5-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="8e6e5-115">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-115">Press F5 to run the application.</span></span> <span data-ttu-id="8e6e5-116">Le formulaire WPF est alors affiché.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="8e6e5-117">Cliquez sur le bouton Load <xref:System.Activities.Presentation.Model.ModelItem> **WF** pour charger le et lier à la vue de l’arbre.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="8e6e5-118">En cliquant sur le bouton **Modifier l’arbre d’élément modèle,** le code précédent exécute le code précédent pour ajouter un élément dans l’arbre et définir une propriété.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e6e5-119">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8e6e5-120">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8e6e5-121">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e6e5-122">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="8e6e5-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="8e6e5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e6e5-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
