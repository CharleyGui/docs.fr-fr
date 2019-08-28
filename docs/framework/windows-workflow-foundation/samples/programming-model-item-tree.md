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
# <a name="programming-model-item-tree"></a><span data-ttu-id="60db8-102">Programmation de l'arborescence des éléments de modèle</span><span class="sxs-lookup"><span data-stu-id="60db8-102">Programming Model Item Tree</span></span>
<span data-ttu-id="60db8-103">Cet exemple montre comment naviguer dans l' <xref:System.Activities.Presentation.Model.ModelItem> arborescence à l’aide de la liaison de données déclarative à partir de l’arborescence Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="60db8-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="60db8-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="60db8-104">Sample Details</span></span>
 <span data-ttu-id="60db8-105">L’arborescence <xref:System.Activities.Presentation.Model.ModelItem> est l’abstraction utilisée par l’infrastructure du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] pour exposer les données relatives à l’instance sous-jacente en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="60db8-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="60db8-106">L'illustration suivante est une description des différentes couches d'infrastructure dans le [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60db8-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>

 ![Diagramme qui montre l’architecture Concepteur de flux de travail.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="60db8-108">Un <xref:System.Activities.Presentation.Model.ModelItem> se compose d'un pointeur vers la valeur sous-jacente, ainsi que d'une collection d'objets <xref:System.Activities.Presentation.Model.ModelProperty>.</span><span class="sxs-lookup"><span data-stu-id="60db8-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="60db8-109">Un objet <xref:System.Activities.Presentation.Model.ModelProperty>, quant à lui, se compose de données telles que le nom et le type de la propriété, puis d'un pointeur vers la valeur qui, à son tout, est un autre <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="60db8-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="60db8-110">Un convertisseur de valeurs est utilisé pour manipuler certains des <xref:System.Activities.Presentation.Model.ModelItem> retournés à partir d’un <xref:System.Activities.Presentation.Model.ModelProperty> pour les faire apparaître correctement dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="60db8-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="60db8-111">L’exemple montre ensuite comment effectuer une programmation de façon impérative sur l’arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l’aide de la syntaxe impérative.</span><span class="sxs-lookup"><span data-stu-id="60db8-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="60db8-112">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="60db8-112">To use this sample</span></span>

1. <span data-ttu-id="60db8-113">Ouvrez la solution ProgrammingModelItemTree. sln dans Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="60db8-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="60db8-114">Générez la solution en sélectionnant **générer la solution** dans le menu **générer** .</span><span class="sxs-lookup"><span data-stu-id="60db8-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="60db8-115">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="60db8-115">Press F5 to run the application.</span></span> <span data-ttu-id="60db8-116">Le formulaire WPF s’affiche alors.</span><span class="sxs-lookup"><span data-stu-id="60db8-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="60db8-117">Cliquez sur le bouton **charger WF** pour charger <xref:System.Activities.Presentation.Model.ModelItem> et le lier à l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="60db8-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="60db8-118">En cliquant sur le bouton **modifier l’arborescence d’éléments de modèle** , vous exécutez le code précédent pour ajouter un élément à l’arborescence et définir une propriété.</span><span class="sxs-lookup"><span data-stu-id="60db8-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="60db8-119">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60db8-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="60db8-120">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="60db8-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="60db8-121">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="60db8-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="60db8-122">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="60db8-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="60db8-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60db8-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
