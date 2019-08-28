---
title: Concepteurs composites personnalisés - Présentateur d'éléments de workflow
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 239f7ccd81d5bb60eed32298220df215b09e3e47
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038371"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="4abb4-102">Concepteurs composites personnalisés - Présentateur d'éléments de workflow</span><span class="sxs-lookup"><span data-stu-id="4abb4-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="4abb4-103">Le <xref:System.Activities.Presentation.WorkflowItemPresenter> est un type de clé dans le modèle de programmation de concepteur WF qui permet la création d’une «zone de dépôt» où une activité arbitraire peut être placée.</span><span class="sxs-lookup"><span data-stu-id="4abb4-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="4abb4-104">Cet exemple montre comment générer un concepteur d’activités qui couvre une telle «zone de dépôt».</span><span class="sxs-lookup"><span data-stu-id="4abb4-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

 <span data-ttu-id="4abb4-105">Cet exemple illustre les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4abb4-105">This sample demonstrates:</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4abb4-106">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="4abb4-106">Demonstrates</span></span>

- <span data-ttu-id="4abb4-107">Création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="4abb4-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="4abb4-108">Inscription du concepteur personnalisé à l'aide du magasin des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4abb4-108">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="4abb4-109">Programmation de la boîte à outils réhébergée de façon déclarative et impérative.</span><span class="sxs-lookup"><span data-stu-id="4abb4-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="4abb4-110">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="4abb4-110">Sample Details</span></span>
 <span data-ttu-id="4abb4-111">Le code de cet exemple illustre les points suivants :</span><span class="sxs-lookup"><span data-stu-id="4abb4-111">The code for this sample shows:</span></span>

- <span data-ttu-id="4abb4-112">Le concepteur d'activités personnalisées est généré pour la classe `SimpleNativeActivity`.</span><span class="sxs-lookup"><span data-stu-id="4abb4-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="4abb4-113">La création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="4abb4-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 <span data-ttu-id="4abb4-114">Notez l'utilisation de la liaison de données WPF pour lier à `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="4abb4-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="4abb4-115">`ModelItem`est la propriété sur <xref:System.Activities.Presentation.ActivityDesigner> qui fait référence à l’objet sous-jacent pour lequel le concepteur est utilisé, dans ce cas, **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="4abb4-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="4abb4-116">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="4abb4-116">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="4abb4-117">Ouvrez la solution dans Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="4abb4-117">Open the solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="4abb4-118">Appuyez sur F5 pour compiler et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="4abb4-118">Press F5 to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4abb4-119">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4abb4-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4abb4-120">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="4abb4-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4abb4-121">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="4abb4-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4abb4-122">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="4abb4-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="4abb4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4abb4-123">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="4abb4-124">Développement d’applications avec le Concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="4abb4-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
