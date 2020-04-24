---
title: 'Procédure pas à pas : Contenu WPF de style'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646332"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="79eac-102">Procédure pas à pas : Contenu WPF de style</span><span class="sxs-lookup"><span data-stu-id="79eac-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="79eac-103">Cet article vous montre comment appliquer le style à un contrôle de la Windows Presentation Foundation (WPF) hébergé sur un formulaire Windows.</span><span class="sxs-lookup"><span data-stu-id="79eac-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79eac-104">Prérequis</span><span class="sxs-lookup"><span data-stu-id="79eac-104">Prerequisites</span></span>

<span data-ttu-id="79eac-105">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79eac-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="79eac-106">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="79eac-106">Create the project</span></span>

<span data-ttu-id="79eac-107">Ouvrez Visual Studio et créez un nouveau projet d’application de formulaires Windows dans Visual Basic ou Visual C . `StylingWpfContent`</span><span class="sxs-lookup"><span data-stu-id="79eac-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="79eac-108">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="79eac-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="79eac-109">Créer les types de contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="79eac-109">Create the WPF control types</span></span>

<span data-ttu-id="79eac-110">Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="79eac-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="79eac-111">Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.</span><span class="sxs-lookup"><span data-stu-id="79eac-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="79eac-112">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="79eac-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="79eac-113">Pour plus d’informations, voir [Procédure pas à pas: Créer du nouveau contenu WPF sur les formulaires Windows à Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="79eac-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="79eac-114">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="79eac-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="79eac-115">Dans la fenêtre **Propriétés,** <xref:System.Windows.FrameworkElement.Width%2A> définissez la valeur de la et <xref:System.Windows.FrameworkElement.Height%2A> des propriétés à **200**.</span><span class="sxs-lookup"><span data-stu-id="79eac-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="79eac-116">Ajoutez <xref:System.Windows.Controls.Button?displayProperty=nameWithType> un contrôle <xref:System.Windows.Controls.UserControl> à la et <xref:System.Windows.Controls.ContentControl.Content%2A> définissez la valeur de la propriété à **annuler**.</span><span class="sxs-lookup"><span data-stu-id="79eac-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="79eac-117">Ajouter un <xref:System.Windows.Controls.Button?displayProperty=nameWithType> deuxième <xref:System.Windows.Controls.UserControl> contrôle à la <xref:System.Windows.Controls.ContentControl.Content%2A> et définir la valeur de la propriété à **OK**.</span><span class="sxs-lookup"><span data-stu-id="79eac-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="79eac-118">Créez le projet.</span><span class="sxs-lookup"><span data-stu-id="79eac-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="79eac-119">Appliquer un style à un contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="79eac-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="79eac-120">Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.</span><span class="sxs-lookup"><span data-stu-id="79eac-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="79eac-121">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="79eac-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="79eac-122">Dans la **boîte à** `UserControl1` outils , double-clic pour créer une instance de `UserControl1` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="79eac-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="79eac-123">Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="79eac-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="79eac-124">Dans le panneau `elementHost1`d’étiquette intelligent pour , cliquez sur **Edit Contenu hébergé** de la liste d’abandon.</span><span class="sxs-lookup"><span data-stu-id="79eac-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="79eac-125">`UserControl1`s’ouvre dans le WPF Designer.</span><span class="sxs-lookup"><span data-stu-id="79eac-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="79eac-126">En mode XAML, insérez le code XAML suivant après l’étiquette d’ouverture `<UserControl>`.</span><span class="sxs-lookup"><span data-stu-id="79eac-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="79eac-127">Ce code XAML crée un dégradé avec une bordure de dégradé contrastée.</span><span class="sxs-lookup"><span data-stu-id="79eac-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="79eac-128">Quand l'utilisateur clique sur le contrôle, les dégradés sont modifiés pour générer une apparence de bouton enfoncé.</span><span class="sxs-lookup"><span data-stu-id="79eac-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="79eac-129">Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="79eac-129">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. <span data-ttu-id="79eac-130">Appliquer `SimpleButton` le style défini dans l’étape précédente sur le bouton `<Button>` Annuler en insérant le XAML suivant dans l’étiquette du bouton **Annuler.**</span><span class="sxs-lookup"><span data-stu-id="79eac-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="79eac-131">Votre déclaration de bouton ressemblera à la XAML suivante :</span><span class="sxs-lookup"><span data-stu-id="79eac-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="79eac-132">Créez le projet.</span><span class="sxs-lookup"><span data-stu-id="79eac-132">Build the project.</span></span>

1. <span data-ttu-id="79eac-133">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="79eac-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="79eac-134">Le nouveau style est appliqué au contrôle de bouton.</span><span class="sxs-lookup"><span data-stu-id="79eac-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="79eac-135">Dans le menu **Debug,** sélectionnez **Start Debugging** pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="79eac-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="79eac-136">Cliquez **sur** les boutons OK et **Annuler** et afficher les différences.</span><span class="sxs-lookup"><span data-stu-id="79eac-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="79eac-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79eac-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="79eac-138">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="79eac-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="79eac-139">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="79eac-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="79eac-140">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79eac-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="79eac-141">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="79eac-141">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="79eac-142">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="79eac-142">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
