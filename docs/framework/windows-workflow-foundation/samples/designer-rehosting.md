---
title: Réhébergement du concepteur
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: b72e3450799db40988c8b99e4db3707de330d8ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182817"
---
# <a name="designer-rehosting"></a><span data-ttu-id="48ac4-102">Réhébergement du concepteur</span><span class="sxs-lookup"><span data-stu-id="48ac4-102">Designer Rehosting</span></span>
<span data-ttu-id="48ac4-103">Le réhébergement du concepteur est un scénario courant qui fait référence à l'hébergement de la zone de dessin de conception du workflow dans une application personnalisée.</span><span class="sxs-lookup"><span data-stu-id="48ac4-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="48ac4-104">L'application d'hébergement avec laquelle la plupart des personnes sont familières est Visual Studio, mais il existe plusieurs scénarios où l'affichage du concepteur de workflow dans une application peut être utile :</span><span class="sxs-lookup"><span data-stu-id="48ac4-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="48ac4-105">Applications d'analyse (permettant à un utilisateur final de visualiser le processus ainsi que les données d'exécution sur le processus, telles que l'état actuellement actif, les données de durée d'exécution agrégées ou d'autres informations relatives à une instance du workflow).</span><span class="sxs-lookup"><span data-stu-id="48ac4-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="48ac4-106">Applications qui permettent à un utilisateur de personnaliser le processus avec un ensemble limité d'activités.</span><span class="sxs-lookup"><span data-stu-id="48ac4-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="48ac4-107">Pour prendre en charge ces types d'applications, le concepteur de workflow accompagne le .NET Framework et peut être hébergé à l'intérieur d'une application WPF, ou dans une application WinForms avec le code d'hébergement WPF approprié.</span><span class="sxs-lookup"><span data-stu-id="48ac4-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="48ac4-108">Cet exemple montre :</span><span class="sxs-lookup"><span data-stu-id="48ac4-108">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="48ac4-109">Réhébergement du concepteur WF.</span><span class="sxs-lookup"><span data-stu-id="48ac4-109">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="48ac4-110">Utilisation de la boîte à outils réhébergée ainsi que de la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="48ac4-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="48ac4-111">Réhébergement du concepteur</span><span class="sxs-lookup"><span data-stu-id="48ac4-111">Rehosting the designer</span></span>  
 <span data-ttu-id="48ac4-112">Cet exemple montre comment créer la disposition WPF pour contenir le concepteur, comme dans la disposition de grille suivante (code de boîte à outils omis pour des raisons d'espace).</span><span class="sxs-lookup"><span data-stu-id="48ac4-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="48ac4-113">Notez la désignation des bordures qui contiennent le concepteur et la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="48ac4-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="48ac4-114">Ensuite, l'exemple crée le concepteur et associe son <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> primaire et <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> au conteneur approprié dans l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="48ac4-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="48ac4-115">Quelques lignes supplémentaires de code dans l'exemple suivant méritent une explication.</span><span class="sxs-lookup"><span data-stu-id="48ac4-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="48ac4-116">L’appel <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> est nécessaire pour associer les concepteurs d’activités par défaut pour les activités expédiées avec .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48ac4-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="48ac4-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> est appelé pour passer l'élément WF à modifier.</span><span class="sxs-lookup"><span data-stu-id="48ac4-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="48ac4-118">Enfin, le <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (zone de dessin primaire) et le <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (grille des propriétés) sont placés sur la surface d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="48ac4-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="48ac4-119">Utilisation de la boîte à outils réhébergée</span><span class="sxs-lookup"><span data-stu-id="48ac4-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="48ac4-120">Cet exemple utilise de façon déclarative le contrôle de boîte à outils réhébergée dans XAML.</span><span class="sxs-lookup"><span data-stu-id="48ac4-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="48ac4-121">Notez que, dans le code, un type peut être passé au constructeur <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper>.</span><span class="sxs-lookup"><span data-stu-id="48ac4-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a><span data-ttu-id="48ac4-122">Utilisation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="48ac4-122">Using the sample</span></span>  
  
1. <span data-ttu-id="48ac4-123">Ouvrez la solution DesignerRehosting.sln dans Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="48ac4-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="48ac4-124">Appuyez sur F5 pour compiler et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="48ac4-124">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="48ac4-125">Une application WPF démarre avec un concepteur réhébergé.</span><span class="sxs-lookup"><span data-stu-id="48ac4-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="48ac4-126">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="48ac4-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48ac4-127">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="48ac4-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="48ac4-128">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="48ac4-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48ac4-129">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="48ac4-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
