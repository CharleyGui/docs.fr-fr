---
title: "Procédure : créer un concepteur d'activités personnalisées"
description: Cet article explique comment créer un concepteur d’activités personnalisées Workflow Foundation qui a une zone de dépôt où une activité arbitraire peut être placée.
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 015efd1e482e2b531d28b9caec411c76116c9653
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419783"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="96be1-103">Procédure : créer un concepteur d'activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="96be1-103">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="96be1-104">Les concepteurs d'activités personnalisées sont généralement implémentés de telle sorte que les activités qui leur sont associées soient composables avec d'autres activités dont les concepteurs peuvent être déposés dans l'aire de conception avec eux.</span><span class="sxs-lookup"><span data-stu-id="96be1-104">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="96be1-105">Cette fonctionnalité requiert qu’un concepteur d’activités personnalisées fournisse une « zone de dépôt » où une activité arbitraire peut être placée, ainsi que le moyen de gérer la collection d’éléments résultante sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="96be1-105">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="96be1-106">Cette rubrique décrit comment créer un concepteur d'activités personnalisées qui contient une telle zone de dépôt et comment créer un concepteur d'activités personnalisées qui fournit cette fonctionnalité d'édition requise pour gérer la collection d'éléments de concepteur.</span><span class="sxs-lookup"><span data-stu-id="96be1-106">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

<span data-ttu-id="96be1-107">Les concepteurs d'activités personnalisées héritent généralement d'<xref:System.Activities.Presentation.ActivityDesigner>, qui est le type du concepteur d'activités de base par défaut pour toutes activités sans concepteur particulier.</span><span class="sxs-lookup"><span data-stu-id="96be1-107">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="96be1-108">Ce type fournit l'expérience au moment du design tirée de l'interaction avec la grille des propriétés et de la configuration des aspects de base comme la gestion des couleurs et des icônes.</span><span class="sxs-lookup"><span data-stu-id="96be1-108">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

<span data-ttu-id="96be1-109">Pour faciliter le développement de concepteurs d'activités personnalisées, <xref:System.Activities.Presentation.ActivityDesigner> utilise deux contrôles d'assistance, <xref:System.Activities.Presentation.WorkflowItemPresenter> et <xref:System.Activities.Presentation.WorkflowItemsPresenter>.</span><span class="sxs-lookup"><span data-stu-id="96be1-109"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="96be1-110">Ceux-ci gèrent les fonctionnalités communes telles que le glisser-déposer, la suppression, la sélection et l’ajout d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="96be1-110">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="96be1-111">Le <xref:System.Activities.Presentation.WorkflowItemPresenter> autorise un seul élément d’interface utilisateur enfant dans, en fournissant la « zone de dépôt », tandis que le <xref:System.Activities.Presentation.WorkflowItemsPresenter> peut fournir une prise en charge de plusieurs éléments d’interface utilisateur, notamment des fonctionnalités supplémentaires telles que le classement, le déplacement, la suppression et l’ajout d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="96be1-111">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

<span data-ttu-id="96be1-112">L’autre partie clé de l’article qui nécessite une mise en évidence dans l’implémentation d’un concepteur d’activités personnalisées concerne la façon dont les modifications visuelles sont liées à l’aide de la liaison de données WPF à l’instance stockée en mémoire de ce que nous modifions dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="96be1-112">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using WPF data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="96be1-113">Cette tâche est effectuée par l’arborescence des éléments de modèles, qui est également chargée de l’activation de la notification de modification et du suivi d’événements tels que les modifications d’états.</span><span class="sxs-lookup"><span data-stu-id="96be1-113">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

<span data-ttu-id="96be1-114">Cette rubrique présente deux procédures.</span><span class="sxs-lookup"><span data-stu-id="96be1-114">This topic outlines two procedures.</span></span>

1. <span data-ttu-id="96be1-115">La première procédure décrit comment créer un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemPresenter> qui fournit la zone de dépôt qui reçoit d'autres activités.</span><span class="sxs-lookup"><span data-stu-id="96be1-115">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="96be1-116">Cette procédure est basée sur l’exemple [personnalisé composite designers-Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) .</span><span class="sxs-lookup"><span data-stu-id="96be1-116">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2. <span data-ttu-id="96be1-117">La deuxième procédure décrit comment créer un concepteur d’activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemsPresenter> qui fournit les fonctionnalités requises pour modifier d’une collection d’éléments contenus.</span><span class="sxs-lookup"><span data-stu-id="96be1-117">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="96be1-118">Cette procédure est basée sur l’exemple [personnalisé composite designers-Workflow items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) .</span><span class="sxs-lookup"><span data-stu-id="96be1-118">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="96be1-119">Pour créer un concepteur d’activités personnalisées avec une zone de dépôt à l’aide de WorkflowItemPresenter</span><span class="sxs-lookup"><span data-stu-id="96be1-119">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1. <span data-ttu-id="96be1-120">Démarrez Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="96be1-120">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="96be1-121">Dans le menu **fichier** , pointez sur **nouveau**, puis sélectionnez **projet...**.</span><span class="sxs-lookup"><span data-stu-id="96be1-121">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="96be1-122">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="96be1-122">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="96be1-123">Dans le volet **modèles installés** , sélectionnez **Windows** dans la catégorie langue de votre choix.</span><span class="sxs-lookup"><span data-stu-id="96be1-123">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4. <span data-ttu-id="96be1-124">Dans le volet **modèles** , sélectionnez **application WPF**.</span><span class="sxs-lookup"><span data-stu-id="96be1-124">In the **Templates** pane, select **WPF Application**.</span></span>

5. <span data-ttu-id="96be1-125">Dans la zone **nom** , entrez `UsingWorkflowItemPresenter` .</span><span class="sxs-lookup"><span data-stu-id="96be1-125">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6. <span data-ttu-id="96be1-126">Dans la zone **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="96be1-126">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7. <span data-ttu-id="96be1-127">Dans la zone **solution** , acceptez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="96be1-127">In the **Solution** box, accept the default value.</span></span>

8. <span data-ttu-id="96be1-128">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="96be1-128">Click **OK**.</span></span>

9. <span data-ttu-id="96be1-129">Cliquez avec le bouton droit sur le fichier *MainWindows. Xaml* dans la **Explorateur de solutions**, sélectionnez **supprimer** , puis confirmez **OK** dans la boîte de dialogue **Microsoft Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="96be1-129">Right-click the *MainWindows.xaml* file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialog box.</span></span>

10. <span data-ttu-id="96be1-130">Cliquez avec le bouton droit sur le projet UsingWorkflowItemPresenter dans **Explorateur de solutions**, sélectionnez **Ajouter**, puis **nouvel élément...**</span><span class="sxs-lookup"><span data-stu-id="96be1-130">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="96be1-131">pour afficher la boîte de dialogue **Ajouter un nouvel élément** et sélectionnez la catégorie **WPF** dans la section **modèles installés** sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="96be1-131">to bring up the **Add New Item** dialog and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="96be1-132">Sélectionnez le modèle **fenêtre (WPF)** , nommez-le `RehostingWFDesigner` , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="96be1-132">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="96be1-133">Ouvrez le fichier *RehostingWFDesigner. Xaml* et collez le code suivant dans celui-ci pour définir l’interface utilisateur de l’application :</span><span class="sxs-lookup"><span data-stu-id="96be1-133">Open the *RehostingWFDesigner.xaml* file and paste the following code into it to define the UI for the application:</span></span>

    ```xaml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
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
                <sapt:ToolboxControl Name="Toolbox">
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

13. <span data-ttu-id="96be1-134">Pour associer un concepteur d'activités à un type d'activité, vous devez enregistrer ce concepteur auprès du magasin des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="96be1-134">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="96be1-135">Pour ce faire, ajoutez la méthode `RegisterMetadata` à la classe `RehostingWFDesigner`.</span><span class="sxs-lookup"><span data-stu-id="96be1-135">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="96be1-136">Dans l'étendue de la méthode `RegisterMetadata`, créez un objet <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> et appelez la méthode <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> pour lui ajouter les attributs.</span><span class="sxs-lookup"><span data-stu-id="96be1-136">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="96be1-137">Appelez la méthode <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> pour ajouter l'objet <xref:System.Activities.Presentation.Metadata.AttributeTable> au magasin des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="96be1-137">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="96be1-138">Le code suivant contient la logique de réhébergement pour le concepteur.</span><span class="sxs-lookup"><span data-stu-id="96be1-138">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="96be1-139">Il enregistre les métadonnées, place `SimpleNativeActivity` dans la boîte à outils, puis crée le workflow.</span><span class="sxs-lookup"><span data-stu-id="96be1-139">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="96be1-140">Placez ce code dans le fichier *RehostingWFDesigner.Xaml.cs* .</span><span class="sxs-lookup"><span data-stu-id="96be1-140">Put this code into the *RehostingWFDesigner.xaml.cs* file.</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. <span data-ttu-id="96be1-141">Dans Explorateur de solutions, cliquez avec le bouton droit sur le répertoire références, puis sélectionnez **Ajouter une référence...**</span><span class="sxs-lookup"><span data-stu-id="96be1-141">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="96be1-142">pour afficher la boîte de dialogue **Ajouter une référence** .</span><span class="sxs-lookup"><span data-stu-id="96be1-142">to bring up the **Add Reference** dialog.</span></span>

15. <span data-ttu-id="96be1-143">Cliquez sur l’onglet **.net** , recherchez l’assembly nommé **System. Activities. Core. Presentation**, sélectionnez-le, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="96be1-143">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="96be1-144">En utilisant la même procédure, ajoutez des références aux assemblys suivants :</span><span class="sxs-lookup"><span data-stu-id="96be1-144">Using the same procedure, add references to the following assemblies:</span></span>

    1. <span data-ttu-id="96be1-145">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="96be1-145">System.Data.DataSetExtensions.dll</span></span>

    2. <span data-ttu-id="96be1-146">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="96be1-146">System.Activities.Presentation.dll</span></span>

    3. <span data-ttu-id="96be1-147">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="96be1-147">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="96be1-148">Ouvrez le fichier *app. Xaml* et remplacez la valeur de StartupUri par « RehostingWFDesigner. Xaml ».</span><span class="sxs-lookup"><span data-stu-id="96be1-148">Open the *App.xaml* file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="96be1-149">Cliquez avec le bouton droit sur le projet UsingWorkflowItemPresenter dans **Explorateur de solutions**, sélectionnez **Ajouter**, puis **nouvel élément...**</span><span class="sxs-lookup"><span data-stu-id="96be1-149">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="96be1-150">pour afficher la boîte de dialogue **Ajouter un nouvel élément** et sélectionnez la catégorie **Workflow** dans la section **modèles installés** sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="96be1-150">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="96be1-151">Sélectionnez le modèle **Concepteur d’activités** , nommez-le `SimpleNativeDesigner` , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="96be1-151">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="96be1-152">Ouvrez le fichier *SimpleNativeDesigner. Xaml* et collez le code suivant dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="96be1-152">Open the *SimpleNativeDesigner.xaml* file and paste the following code into it.</span></span> <span data-ttu-id="96be1-153">Notez que ce code utilise <xref:System.Activities.Presentation.ActivityDesigner> comme élément racine et montre comment la liaison est utilisée pour intégrer <xref:System.Activities.Presentation.WorkflowItemPresenter> à votre concepteur afin qu'un type enfant puisse être affiché dans votre concepteur d'activités composites.</span><span class="sxs-lookup"><span data-stu-id="96be1-153">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="96be1-154">Le schéma de l'objet <xref:System.Activities.Presentation.ActivityDesigner> permet l'ajout d'un seul élément enfant à la définition de votre concepteur d'activités personnalisées. Toutefois, cet élément peut être un `StackPanel`, un `Grid` ou tout autre élément d'interface utilisateur composite.</span><span class="sxs-lookup"><span data-stu-id="96be1-154">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
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

21. <span data-ttu-id="96be1-155">Cliquez avec le bouton droit sur le projet UsingWorkflowItemPresenter dans **Explorateur de solutions**, sélectionnez **Ajouter**, puis **nouvel élément...**</span><span class="sxs-lookup"><span data-stu-id="96be1-155">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="96be1-156">pour afficher la boîte de dialogue **Ajouter un nouvel élément** et sélectionnez la catégorie **Workflow** dans la section **modèles installés** sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="96be1-156">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="96be1-157">Sélectionnez le modèle d' **activité code** , nommez-le `SimpleNativeActivity` , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="96be1-157">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="96be1-158">Implémentez la `SimpleNativeActivity` classe en entrant le code suivant dans le fichier *SimpleNativeActivity.cs* :</span><span class="sxs-lookup"><span data-stu-id="96be1-158">Implement the `SimpleNativeActivity` class by entering the following code into the *SimpleNativeActivity.cs* file:</span></span>

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. <span data-ttu-id="96be1-159">Dans le menu **générer** , sélectionnez **générer la solution** .</span><span class="sxs-lookup"><span data-stu-id="96be1-159">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="96be1-160">Sélectionnez **exécuter sans débogage** dans le menu **Déboguer** pour ouvrir la fenêtre de conception personnalisée réhébergée.</span><span class="sxs-lookup"><span data-stu-id="96be1-160">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="96be1-161">Pour créer un concepteur d'activités personnalisées à l'aide de WorkflowItemsPresenter</span><span class="sxs-lookup"><span data-stu-id="96be1-161">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1. <span data-ttu-id="96be1-162">La procédure pour le deuxième concepteur d’activités personnalisées est le parallèle la première avec quelques modifications, la première étant de nommer la deuxième application `UsingWorkflowItemsPresenter` .</span><span class="sxs-lookup"><span data-stu-id="96be1-162">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="96be1-163">De plus, cette application ne définit pas une nouvelle activité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="96be1-163">Also this application does not define a new custom activity.</span></span>

2. <span data-ttu-id="96be1-164">Les principales différences sont contenues dans les fichiers *CustomParallelDesigner. Xaml* et *RehostingWFDesigner.Xaml.cs* .</span><span class="sxs-lookup"><span data-stu-id="96be1-164">Key differences are contained in the *CustomParallelDesigner.xaml* and *RehostingWFDesigner.xaml.cs* files.</span></span> <span data-ttu-id="96be1-165">Voici le code du fichier *CustomParallelDesigner. Xaml* qui définit l’interface utilisateur :</span><span class="sxs-lookup"><span data-stu-id="96be1-165">Here is the code from the *CustomParallelDesigner.xaml* file that defines the UI:</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
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
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. <span data-ttu-id="96be1-166">Voici le code du fichier *RehostingWFDesigner.Xaml.cs* qui fournit la logique de réhébergement :</span><span class="sxs-lookup"><span data-stu-id="96be1-166">Here is the code from the *RehostingWFDesigner.xaml.cs* file that provides the rehosting logic:</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="96be1-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96be1-167">See also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="96be1-168">Personnalisation de l'expérience de conception de workflow</span><span class="sxs-lookup"><span data-stu-id="96be1-168">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
