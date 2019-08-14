---
title: 'Procédure pas à pas : application d’un style au contenu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 32ca9658ddf4ab6e8690f29797b7ac7b09df2ca7
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012955"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="cecf3-102">Procédure pas à pas : Contenu WPF du style</span><span class="sxs-lookup"><span data-stu-id="cecf3-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="cecf3-103">Cette procédure pas à pas montre comment appliquer des styles à un contrôle WPF (Windows Presentation Foundation) hébergé sur un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="cecf3-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="cecf3-104">Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="cecf3-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="cecf3-105">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="cecf3-105">Create the project.</span></span>

- <span data-ttu-id="cecf3-106">créer le type de contrôle WPF ;</span><span class="sxs-lookup"><span data-stu-id="cecf3-106">Create the WPF control type.</span></span>

- <span data-ttu-id="cecf3-107">appliquer un style au contrôle WPF.</span><span class="sxs-lookup"><span data-stu-id="cecf3-107">Apply a style to the WPF control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cecf3-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="cecf3-108">Prerequisites</span></span>

<span data-ttu-id="cecf3-109">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cecf3-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="cecf3-110">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="cecf3-110">Create the project</span></span>

<span data-ttu-id="cecf3-111">Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel `StylingWpfContent`nommé.</span><span class="sxs-lookup"><span data-stu-id="cecf3-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="cecf3-112">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cecf3-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="cecf3-113">Créer les types de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="cecf3-113">Create the WPF control types</span></span>

<span data-ttu-id="cecf3-114">Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="cecf3-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="cecf3-115">Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.</span><span class="sxs-lookup"><span data-stu-id="cecf3-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="cecf3-116">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="cecf3-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="cecf3-117">Pour plus d’informations, consultez [Procédure pas à pas : Création d’un contenu WPF sur Windows Forms au moment](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de la conception.</span><span class="sxs-lookup"><span data-stu-id="cecf3-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="cecf3-118">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="cecf3-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="cecf3-119">Pour plus d'informations, voir [Procédure : Sélectionner et déplacer des éléments sur la](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))aire de conception.</span><span class="sxs-lookup"><span data-stu-id="cecf3-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="cecf3-120">Dans la fenêtre **Propriétés** , affectez à <xref:System.Windows.FrameworkElement.Width%2A> `200`la valeur des <xref:System.Windows.FrameworkElement.Height%2A> propriétés et la valeur.</span><span class="sxs-lookup"><span data-stu-id="cecf3-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="cecf3-121">Ajoutez un <xref:System.Windows.Controls.Button?displayProperty=nameWithType> <xref:System.Windows.Controls.UserControl> contrôle au et <xref:System.Windows.Controls.ContentControl.Content%2A> affectez la valeur **Cancel**à la propriété.</span><span class="sxs-lookup"><span data-stu-id="cecf3-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="cecf3-122">Ajoutez un deuxième <xref:System.Windows.Controls.Button?displayProperty=nameWithType> contrôle <xref:System.Windows.Controls.UserControl> à et <xref:System.Windows.Controls.ContentControl.Content%2A> affectez la valeur **OK**à la propriété.</span><span class="sxs-lookup"><span data-stu-id="cecf3-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="cecf3-123">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="cecf3-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="cecf3-124">Appliquer un style à un contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="cecf3-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="cecf3-125">Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.</span><span class="sxs-lookup"><span data-stu-id="cecf3-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="cecf3-126">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cecf3-126">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="cecf3-127">Dans la **boîte à outils**, double `UserControl1` -cliquez sur pour créer `UserControl1` une instance de sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="cecf3-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="cecf3-128">Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="cecf3-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="cecf3-129">Dans le panneau des `elementHost1`balises actives, cliquez sur modifier le **contenu hébergé** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="cecf3-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="cecf3-130">`UserControl1` s'ouvre dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cecf3-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

1. <span data-ttu-id="cecf3-131">En mode XAML, insérez le code XAML suivant après la balise d'ouverture `<UserControl>`.</span><span class="sxs-lookup"><span data-stu-id="cecf3-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="cecf3-132">Ce code XAML crée un dégradé avec une bordure de dégradé contrastée.</span><span class="sxs-lookup"><span data-stu-id="cecf3-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="cecf3-133">Quand l'utilisateur clique sur le contrôle, les dégradés sont modifiés pour générer une apparence de bouton enfoncé.</span><span class="sxs-lookup"><span data-stu-id="cecf3-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="cecf3-134">Pour plus d’informations, consultez [Application d’un style et création de modèles](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="cecf3-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

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

1. <span data-ttu-id="cecf3-135">Appliquez le style `SimpleButton` défini à l’étape précédente au bouton Annuler en insérant le code XAML suivant dans l’étiquette `<Button>` du bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="cecf3-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="cecf3-136">Votre déclaration de bouton ressemble au code XAML suivant:</span><span class="sxs-lookup"><span data-stu-id="cecf3-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="cecf3-137">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="cecf3-137">Build the project.</span></span>

1. <span data-ttu-id="cecf3-138">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cecf3-138">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="cecf3-139">Le nouveau style est appliqué au contrôle de bouton.</span><span class="sxs-lookup"><span data-stu-id="cecf3-139">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="cecf3-140">Dans le menu Déboguer, sélectionnez **Démarrer** le débogage pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="cecf3-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="cecf3-141">Cliquez sur les boutons OK et Annuler et observez les différences.</span><span class="sxs-lookup"><span data-stu-id="cecf3-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="cecf3-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cecf3-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="cecf3-143">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="cecf3-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="cecf3-144">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="cecf3-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="cecf3-145">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cecf3-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="cecf3-146">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="cecf3-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="cecf3-147">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="cecf3-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
