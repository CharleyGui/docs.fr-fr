---
title: Extensibilité de la propriété grille - exemple WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: d22b6e21fbf2d5deb4d47fce683553378e990000
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637679"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="2633e-102">Extensibilité de grille de propriétés</span><span class="sxs-lookup"><span data-stu-id="2633e-102">Property grid extensibility</span></span>

<span data-ttu-id="2633e-103">Un développeur peut personnaliser la grille des propriétés qui s'affiche lorsqu'une activité donnée est sélectionnée dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="2633e-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="2633e-104">Cela permet de créer une expérience d'édition enrichie.</span><span class="sxs-lookup"><span data-stu-id="2633e-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="2633e-105">Cet exemple montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="2633e-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2633e-106">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="2633e-106">Demonstrates</span></span>

<span data-ttu-id="2633e-107">Extensibilité de la grille des propriétés du concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="2633e-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2633e-108">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2633e-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2633e-109">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2633e-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2633e-110">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="2633e-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2633e-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2633e-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="2633e-112">Discussion</span><span class="sxs-lookup"><span data-stu-id="2633e-112">Discussion</span></span>

<span data-ttu-id="2633e-113">Pour étendre la grille des propriétés, un développeur dispose d'options permettant de personnaliser l'apparence incluse d'un éditeur de grilles des propriétés ou de fournir une boîte de dialogue qui s'affiche pour offrir une surface d'édition plus avancée.</span><span class="sxs-lookup"><span data-stu-id="2633e-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="2633e-114">Deux éditeurs différents sont présentés dans cet exemple : un éditeur Inline et un éditeur de boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2633e-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="2633e-115">Éditeur inline</span><span class="sxs-lookup"><span data-stu-id="2633e-115">Inline editor</span></span>

<span data-ttu-id="2633e-116">L'exemple d'éditeur inline montre les points suivants :</span><span class="sxs-lookup"><span data-stu-id="2633e-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="2633e-117">Il crée un type qui dérive de <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="2633e-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="2633e-118">Dans le constructeur, le <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> a la valeur avec un modèle de données Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="2633e-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="2633e-119">Il peut être lié à un modèle XAML, mais dans cet exemple, le code est utilisé pour initialiser la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="2633e-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="2633e-120">Le modèle de données a un contexte de données du <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> de l'élément restitué dans la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="2633e-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="2633e-121">Notez, dans le code suivant (provenant de CustomInlineEditor.cs), que ce contexte crée ensuite une liaison avec la propriété `Value`.</span><span class="sxs-lookup"><span data-stu-id="2633e-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

    ```csharp
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));
    Binding sliderBinding = new Binding("Value");
    sliderBinding.Mode = BindingMode.TwoWay;
    slider.SetValue(Slider.MinimumProperty, 0.0);
    slider.SetValue(Slider.MaximumProperty, 100.0);
    slider.SetValue(Slider.ValueProperty, sliderBinding);
    stack.AppendChild(slider);
    ```

- <span data-ttu-id="2633e-122">Étant donné que l'activité et le concepteur se trouvent dans le même assembly, l'inscription des attributs du concepteur d'activités s'effectue dans le constructeur statique de l'activité elle-même, comme le montre l'exemple suivant issu de SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="2633e-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="2633e-123">Éditeur de boîtes de dialogue</span><span class="sxs-lookup"><span data-stu-id="2633e-123">Dialog editor</span></span>

<span data-ttu-id="2633e-124">L'exemple d'éditeur de boîtes de dialogue montre les points suivants :</span><span class="sxs-lookup"><span data-stu-id="2633e-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="2633e-125">Il crée un type qui dérive de <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="2633e-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="2633e-126">Il définit la valeur <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> dans le constructeur avec un modèle de données [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2633e-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="2633e-127">Cet élément peut être créé en XAML, mais dans cet exemple, il est créé dans le code.</span><span class="sxs-lookup"><span data-stu-id="2633e-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="2633e-128">Le modèle de données a un contexte de données du <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> de l'élément restitué dans la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="2633e-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="2633e-129">Dans le code suivant, ce contexte crée ensuite une liaison avec la propriété `Value`.</span><span class="sxs-lookup"><span data-stu-id="2633e-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="2633e-130">Il est essentiel d'inclure également un <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> pour fournir le bouton qui affiche la boîte de dialogue dans FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="2633e-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

    ```csharp
    this.InlineEditorTemplate = new DataTemplate();

    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));
    Binding labelBinding = new Binding("Value");
    label.SetValue(Label.ContentProperty, labelBinding);
    label.SetValue(Label.MaxWidthProperty, 90.0);

    stack.AppendChild(label);

    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));

    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);

    stack.AppendChild(editModeSwitch);

    this.InlineEditorTemplate.VisualTree = stack;
    ```

4. <span data-ttu-id="2633e-131">Substitue la méthode <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> dans le type concepteur pour gérer l'affichage de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2633e-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="2633e-132">Dans cet exemple, un <xref:System.Windows.Forms.FileDialog> de base est présenté.</span><span class="sxs-lookup"><span data-stu-id="2633e-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. <span data-ttu-id="2633e-133">Étant donné que l'activité et le concepteur se trouvent dans le même assembly, l'inscription des attributs du concepteur d'activités s'effectue dans le constructeur statique de l'activité elle-même, comme le montre l'exemple suivant issu de SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="2633e-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2633e-134">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="2633e-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2633e-135">Générez la solution, puis ouvrez Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="2633e-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="2633e-136">Faites glisser un **SimpleCodeActivity** à partir de la boîte à outils vers la zone de conception.</span><span class="sxs-lookup"><span data-stu-id="2633e-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="2633e-137">Cliquez sur le **SimpleCodeActivity** , puis ouvrez la grille des propriétés où il existe un contrôle slider et un fichier de contrôle de sélection.</span><span class="sxs-lookup"><span data-stu-id="2633e-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2633e-138">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2633e-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2633e-139">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2633e-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2633e-140">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="2633e-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2633e-141">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2633e-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
