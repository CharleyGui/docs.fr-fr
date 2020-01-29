---
title: 'Procédure pas à pas : style de contenu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e52297f51c74fc3dba93c987fd5b9bd5b6801777
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732544"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="1bf92-102">Procédure pas à pas : style de contenu WPF</span><span class="sxs-lookup"><span data-stu-id="1bf92-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="1bf92-103">Cet article vous explique comment appliquer un style à un contrôle Windows Presentation Foundation (WPF) hébergé sur un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="1bf92-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bf92-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="1bf92-104">Prerequisites</span></span>

<span data-ttu-id="1bf92-105">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1bf92-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="1bf92-106">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="1bf92-106">Create the project</span></span>

<span data-ttu-id="1bf92-107">Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel nommé `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="1bf92-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="1bf92-108">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1bf92-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="1bf92-109">Créer les types de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="1bf92-109">Create the WPF control types</span></span>

<span data-ttu-id="1bf92-110">Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="1bf92-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="1bf92-111">Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.</span><span class="sxs-lookup"><span data-stu-id="1bf92-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="1bf92-112">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="1bf92-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="1bf92-113">Pour plus d’informations, consultez [procédure pas à pas : création de contenu WPF sur Windows Forms au moment du design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="1bf92-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="1bf92-114">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1bf92-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="1bf92-115">Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="1bf92-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="1bf92-116">Ajoutez un contrôle de <xref:System.Windows.Controls.Button?displayProperty=nameWithType> au <xref:System.Windows.Controls.UserControl> et définissez la valeur de la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="1bf92-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="1bf92-117">Ajoutez un deuxième contrôle de <xref:System.Windows.Controls.Button?displayProperty=nameWithType> au <xref:System.Windows.Controls.UserControl> et définissez la valeur de la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1bf92-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="1bf92-118">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="1bf92-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="1bf92-119">Appliquer un style à un contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="1bf92-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="1bf92-120">Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.</span><span class="sxs-lookup"><span data-stu-id="1bf92-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="1bf92-121">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bf92-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="1bf92-122">Dans la **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="1bf92-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="1bf92-123">Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="1bf92-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="1bf92-124">Dans le panneau des balises actives pour `elementHost1`, cliquez sur **modifier le contenu hébergé** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="1bf92-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="1bf92-125">`UserControl1` s’ouvre dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="1bf92-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="1bf92-126">En mode XAML, insérez le code XAML suivant après l’étiquette d’ouverture `<UserControl>`.</span><span class="sxs-lookup"><span data-stu-id="1bf92-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="1bf92-127">Ce code XAML crée un dégradé avec une bordure de dégradé contrastée.</span><span class="sxs-lookup"><span data-stu-id="1bf92-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="1bf92-128">Quand l'utilisateur clique sur le contrôle, les dégradés sont modifiés pour générer une apparence de bouton enfoncé.</span><span class="sxs-lookup"><span data-stu-id="1bf92-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="1bf92-129">Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1bf92-129">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

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

1. <span data-ttu-id="1bf92-130">Appliquez le style de `SimpleButton` défini à l’étape précédente au bouton Annuler en insérant le code XAML suivant dans la balise `<Button>` du bouton **Annuler** .</span><span class="sxs-lookup"><span data-stu-id="1bf92-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="1bf92-131">Votre déclaration de bouton ressemble au code XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="1bf92-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="1bf92-132">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="1bf92-132">Build the project.</span></span>

1. <span data-ttu-id="1bf92-133">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bf92-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="1bf92-134">Le nouveau style est appliqué au contrôle de bouton.</span><span class="sxs-lookup"><span data-stu-id="1bf92-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="1bf92-135">Dans le menu **Déboguer** , sélectionnez **Démarrer le débogage** pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="1bf92-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="1bf92-136">Cliquez sur les boutons **OK** et **Annuler** et affichez les différences.</span><span class="sxs-lookup"><span data-stu-id="1bf92-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bf92-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bf92-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="1bf92-138">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1bf92-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="1bf92-139">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="1bf92-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="1bf92-140">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1bf92-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="1bf92-141">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1bf92-141">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="1bf92-142">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="1bf92-142">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
