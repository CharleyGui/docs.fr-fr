---
title: 'Procédure pas à pas : créer un bouton avec XAML'
description: Utilisez cette procédure pas à pas pour apprendre à créer un bouton animé à utiliser dans une application Windows Presentation Foundation à l’aide de XAML.
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 136d1ad5d6fefd70f0d977e5287ae75f06c52d36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164845"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="d4316-103">Procédure pas à pas : créer un bouton avec XAML</span><span class="sxs-lookup"><span data-stu-id="d4316-103">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="d4316-104">L’objectif de cette procédure pas à pas est d’apprendre à créer un bouton animé à utiliser dans une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d4316-104">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="d4316-105">Cette procédure pas à pas utilise des styles et un modèle pour créer une ressource de bouton personnalisée qui permet la réutilisation du code et la séparation de la logique de bouton à partir de la déclaration de bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-105">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="d4316-106">Cette procédure pas à pas est écrite entièrement dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d4316-106">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4316-107">Cette procédure pas à pas vous guide tout au long des étapes de création de l’application en tapant ou en copiant-collant [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4316-107">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="d4316-108">Si vous préférez apprendre à utiliser un concepteur pour créer la même application, consultez [créer un bouton à l’aide de Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="d4316-108">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="d4316-109">L’illustration suivante montre les boutons terminés.</span><span class="sxs-lookup"><span data-stu-id="d4316-109">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="d4316-110">![Boutons personnalisés créés en utilisant XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="d4316-110">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="d4316-111">Créer des boutons de base</span><span class="sxs-lookup"><span data-stu-id="d4316-111">Create Basic Buttons</span></span>

<span data-ttu-id="d4316-112">Commençons par créer un nouveau projet et à ajouter quelques boutons à la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d4316-112">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="d4316-113">Pour créer un projet WPF et ajouter des boutons à la fenêtre</span><span class="sxs-lookup"><span data-stu-id="d4316-113">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="d4316-114">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4316-114">Start Visual Studio.</span></span>

2. <span data-ttu-id="d4316-115">**Créez un projet WPF :** Dans le menu **fichier** , pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="d4316-115">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="d4316-116">Recherchez le modèle d' **application Windows (WPF)** et nommez le projet « AnimatedButton ».</span><span class="sxs-lookup"><span data-stu-id="d4316-116">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="d4316-117">Cette opération crée la structure de l’application.</span><span class="sxs-lookup"><span data-stu-id="d4316-117">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="d4316-118">**Ajouter des boutons par défaut de base :** Tous les fichiers dont vous avez besoin pour cette procédure pas à pas sont fournis par le modèle.</span><span class="sxs-lookup"><span data-stu-id="d4316-118">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="d4316-119">Ouvrez le fichier Window1. XAML en double-cliquant dessus dans Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="d4316-119">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="d4316-120">Par défaut, il existe un <xref:System.Windows.Controls.Grid> élément dans Window1. Xaml.</span><span class="sxs-lookup"><span data-stu-id="d4316-120">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="d4316-121">Supprimez l' <xref:System.Windows.Controls.Grid> élément et ajoutez quelques boutons à la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page en tapant ou en recopiant et collant le code en surbrillance suivant dans Window1. xaml :</span><span class="sxs-lookup"><span data-stu-id="d4316-121">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     <span data-ttu-id="d4316-122">Appuyez sur F5 pour exécuter l’application. vous devez voir un ensemble de boutons ressemblant à l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="d4316-122">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="d4316-123">![Trois boutons de base](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="d4316-123">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="d4316-124">Maintenant que vous avez créé les boutons de base, vous avez fini de travailler dans le fichier Window1. Xaml.</span><span class="sxs-lookup"><span data-stu-id="d4316-124">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="d4316-125">Le reste de la procédure pas à pas se concentre sur le fichier app. xaml, sur la définition des styles et un modèle pour les boutons.</span><span class="sxs-lookup"><span data-stu-id="d4316-125">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="d4316-126">Définir les propriétés de base</span><span class="sxs-lookup"><span data-stu-id="d4316-126">Set Basic Properties</span></span>

<span data-ttu-id="d4316-127">Ensuite, nous allons définir des propriétés sur ces boutons pour contrôler l’apparence et la disposition du bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-127">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="d4316-128">Au lieu de définir des propriétés sur les boutons individuellement, vous allez utiliser des ressources pour définir les propriétés de bouton de l’application entière.</span><span class="sxs-lookup"><span data-stu-id="d4316-128">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="d4316-129">Les ressources d’application sont conceptuellement similaires aux feuilles de style en cascade externes (CSS) pour les pages Web ; Toutefois, les ressources sont bien plus puissantes que feuilles de style en cascade (CSS), comme vous le verrez à la fin de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="d4316-129">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="d4316-130">Pour en savoir plus sur les ressources, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="d4316-130">To learn more about resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="d4316-131">Pour utiliser des styles pour définir des propriétés de base sur les boutons</span><span class="sxs-lookup"><span data-stu-id="d4316-131">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="d4316-132">**Définissez un bloc application. Resources :** Ouvrez App. xaml et ajoutez le balisage en surbrillance suivant s’il n’y figure pas déjà :</span><span class="sxs-lookup"><span data-stu-id="d4316-132">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

    ```xaml
    <Application x:Class="AnimatedButton.App"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      StartupUri="Window1.xaml"
      >
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>
    </Application>
    ```

     <span data-ttu-id="d4316-133">L’étendue des ressources est déterminée par l’emplacement de définition de la ressource.</span><span class="sxs-lookup"><span data-stu-id="d4316-133">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="d4316-134">La définition de ressources dans `Application.Resources` le fichier app. Xaml permet d’utiliser la ressource depuis n’importe où dans l’application.</span><span class="sxs-lookup"><span data-stu-id="d4316-134">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="d4316-135">Pour en savoir plus sur la définition de l’étendue de vos ressources, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="d4316-135">To learn more about defining the scope of your resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

2. <span data-ttu-id="d4316-136">**Créez un style et définissez les valeurs de propriété de base avec lui :** Ajoutez le balisage suivant au `Application.Resources` bloc.</span><span class="sxs-lookup"><span data-stu-id="d4316-136">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="d4316-137">Ce balisage crée un <xref:System.Windows.Style> qui s’applique à tous les boutons de l’application, en affectant à la propriété <xref:System.Windows.FrameworkElement.Width%2A> des boutons la valeur 90 et la <xref:System.Windows.FrameworkElement.Margin%2A> valeur 10 :</span><span class="sxs-lookup"><span data-stu-id="d4316-137">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="d4316-138">La <xref:System.Windows.Style.TargetType%2A> propriété spécifie que le style s’applique à tous les objets de type <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="d4316-138">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="d4316-139">Chaque <xref:System.Windows.Setter> définit une valeur de propriété différente pour le <xref:System.Windows.Style> .</span><span class="sxs-lookup"><span data-stu-id="d4316-139">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="d4316-140">Par conséquent, à ce stade, chaque bouton de l’application a une largeur de 90 et une marge de 10.</span><span class="sxs-lookup"><span data-stu-id="d4316-140">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="d4316-141">Si vous appuyez sur F5 pour exécuter l’application, la fenêtre suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d4316-141">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="d4316-142">![Boutons avec une largeur de 90 et une marge de 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="d4316-142">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="d4316-143">Vous pouvez faire bien d’autres choses avec les styles, y compris diverses façons d’affiner les objets ciblés, en spécifiant des valeurs de propriété complexes et même en utilisant des styles comme entrée pour d’autres styles.</span><span class="sxs-lookup"><span data-stu-id="d4316-143">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="d4316-144">Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d4316-144">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="d4316-145">**Définissez une valeur de propriété de style sur une ressource :** Les ressources permettent de réutiliser facilement les objets et valeurs couramment définis.</span><span class="sxs-lookup"><span data-stu-id="d4316-145">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="d4316-146">Il est particulièrement utile de définir des valeurs complexes à l’aide de ressources pour faciliter la modularité de votre code.</span><span class="sxs-lookup"><span data-stu-id="d4316-146">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="d4316-147">Ajoutez le balisage en surbrillance suivant à App. Xaml.</span><span class="sxs-lookup"><span data-stu-id="d4316-147">Add the following highlighted markup to app.xaml.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="d4316-148">Directement sous le `Application.Resources` bloc, vous avez créé une ressource appelée « GrayBlueGradientBrush ».</span><span class="sxs-lookup"><span data-stu-id="d4316-148">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="d4316-149">Cette ressource définit un dégradé horizontal.</span><span class="sxs-lookup"><span data-stu-id="d4316-149">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="d4316-150">Cette ressource peut être utilisée en tant que valeur de propriété à n’importe quel endroit de l’application, y compris à l’intérieur de la méthode setter de style de bouton pour la <xref:System.Windows.Controls.Control.Background%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="d4316-150">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="d4316-151">À présent, tous les boutons ont une <xref:System.Windows.Controls.Control.Background%2A> valeur de propriété de ce dégradé.</span><span class="sxs-lookup"><span data-stu-id="d4316-151">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="d4316-152">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d4316-152">Press F5 to run the application.</span></span> <span data-ttu-id="d4316-153">Elle doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="d4316-153">It should look like the following.</span></span>

     <span data-ttu-id="d4316-154">![Boutons avec un arrière-plan dégradé](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="d4316-154">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="d4316-155">Créer un modèle qui définit l’apparence du bouton</span><span class="sxs-lookup"><span data-stu-id="d4316-155">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="d4316-156">Dans cette section, vous allez créer un modèle qui personnalise l’apparence (présentation) du bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-156">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="d4316-157">La présentation du bouton est composée de plusieurs objets, y compris des rectangles et d’autres composants, pour donner un aspect unique au bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-157">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="d4316-158">Jusqu’à présent, le contrôle de l’apparence des boutons dans l’application a été limité à la modification des propriétés du bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-158">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="d4316-159">Que se passe-t-il si vous souhaitez apporter des modifications plus radicales à l’apparence du bouton ?</span><span class="sxs-lookup"><span data-stu-id="d4316-159">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="d4316-160">Les modèles permettent un contrôle puissant de la présentation d’un objet.</span><span class="sxs-lookup"><span data-stu-id="d4316-160">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="d4316-161">Étant donné que les modèles peuvent être utilisés dans les styles, vous pouvez appliquer un modèle à tous les objets auxquels le style s’applique (dans cette procédure pas à pas, le bouton).</span><span class="sxs-lookup"><span data-stu-id="d4316-161">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="d4316-162">Pour utiliser le modèle afin de définir l’apparence du bouton</span><span class="sxs-lookup"><span data-stu-id="d4316-162">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="d4316-163">**Configurez le modèle :** Comme les contrôles comme <xref:System.Windows.Controls.Button> ont une <xref:System.Windows.Controls.Control.Template%2A> propriété, vous pouvez définir la valeur de propriété de modèle comme les autres valeurs de propriété que nous avons définies dans un <xref:System.Windows.Style> à l’aide d’un <xref:System.Windows.Setter> .</span><span class="sxs-lookup"><span data-stu-id="d4316-163">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="d4316-164">Ajoutez le balisage en surbrillance suivant à votre style de bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-164">Add the following highlighted markup to your button style.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"
        StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>
      </Style>
    </Application.Resources>
    ```

2. <span data-ttu-id="d4316-165">**Présentation du bouton modifier :** À ce stade, vous devez définir le modèle.</span><span class="sxs-lookup"><span data-stu-id="d4316-165">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="d4316-166">Ajoutez le balisage en surbrillance suivant.</span><span class="sxs-lookup"><span data-stu-id="d4316-166">Add the following highlighted markup.</span></span> <span data-ttu-id="d4316-167">Ce balisage spécifie deux <xref:System.Windows.Shapes.Rectangle> éléments avec des bords arrondis, suivis d’un <xref:System.Windows.Controls.DockPanel> .</span><span class="sxs-lookup"><span data-stu-id="d4316-167">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="d4316-168">Le <xref:System.Windows.Controls.DockPanel> est utilisé pour héberger le <xref:System.Windows.Controls.ContentPresenter> du bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-168">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="d4316-169">Un <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-169">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="d4316-170">Dans cette procédure pas à pas, le contenu est de texte (« Button 1 », « Button 2 », « Button 3 »).</span><span class="sxs-lookup"><span data-stu-id="d4316-170">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="d4316-171">Tous les composants de modèle (les rectangles et <xref:System.Windows.Controls.DockPanel> ) sont disposés à l’intérieur d’un <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="d4316-171">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="d4316-172">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d4316-172">Press F5 to run the application.</span></span> <span data-ttu-id="d4316-173">Elle doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="d4316-173">It should look like the following.</span></span>

     ![Fenêtre avec 3 boutons](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="d4316-175">**Ajoutez un GlassEffect au modèle :** Ensuite, vous allez ajouter la vitre.</span><span class="sxs-lookup"><span data-stu-id="d4316-175">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="d4316-176">Tout d’abord, vous créez des ressources qui créent un effet de dégradé de verre.</span><span class="sxs-lookup"><span data-stu-id="d4316-176">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="d4316-177">Ajoutez ces ressources de dégradés n’importe où dans le `Application.Resources` bloc :</span><span class="sxs-lookup"><span data-stu-id="d4316-177">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     <span data-ttu-id="d4316-178">Ces ressources sont utilisées comme <xref:System.Windows.Shapes.Shape.Fill%2A> pour un rectangle que nous insérons dans le <xref:System.Windows.Controls.Grid> du modèle de bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-178">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="d4316-179">Ajoutez le balisage en surbrillance suivant au modèle.</span><span class="sxs-lookup"><span data-stu-id="d4316-179">Add the following highlighted markup to the template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"
          ClipToBounds="True">

        <!-- Outer Rectangle with rounded corners. -->
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

        <!-- Inner Rectangle with rounded corners. -->
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />

        <!-- Glass Rectangle -->
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch"
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
          Fill="{StaticResource MyGlassBrushResource}"
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
          </Rectangle.Stroke>
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>

        <!-- Present Text of the button. -->
        <DockPanel Name="myContentPresenterDockPanel">
          <ContentPresenter x:Name="myContentPresenter" Margin="20"
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
        </DockPanel>
      </Grid>
    </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="d4316-180">Notez que le <xref:System.Windows.UIElement.Opacity%2A> du rectangle avec la `x:Name` propriété de « glassCube » a la valeur 0. par conséquent, lorsque vous exécutez l’exemple, le rectangle de transparence ne s’affiche pas en haut.</span><span class="sxs-lookup"><span data-stu-id="d4316-180">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="d4316-181">Cela est dû au fait que nous ajouterons ultérieurement des déclencheurs au modèle lorsque l’utilisateur interagit avec le bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-181">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="d4316-182">Toutefois, vous pouvez voir à quoi ressemble le bouton maintenant en remplaçant la <xref:System.Windows.UIElement.Opacity%2A> valeur par 1 et en exécutant l’application.</span><span class="sxs-lookup"><span data-stu-id="d4316-182">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="d4316-183">Voir la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="d4316-183">See the following figure.</span></span> <span data-ttu-id="d4316-184">Avant de passer à l’étape suivante, repassez la <xref:System.Windows.UIElement.Opacity%2A> valeur 0.</span><span class="sxs-lookup"><span data-stu-id="d4316-184">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="d4316-185">![Boutons personnalisés créés en utilisant XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="d4316-185">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="d4316-186">Créer une interactivité de bouton</span><span class="sxs-lookup"><span data-stu-id="d4316-186">Create Button Interactivity</span></span>

<span data-ttu-id="d4316-187">Dans cette section, vous allez créer des déclencheurs de propriété et des déclencheurs d’événements pour modifier les valeurs de propriété et exécuter des animations en réponse aux actions de l’utilisateur, telles que le déplacement du pointeur de la souris sur le bouton et le clic.</span><span class="sxs-lookup"><span data-stu-id="d4316-187">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="d4316-188">Un moyen simple d’ajouter de l’interactivité (souris, survol, clic, etc.) consiste à définir des déclencheurs dans votre modèle ou style.</span><span class="sxs-lookup"><span data-stu-id="d4316-188">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="d4316-189">Pour créer un <xref:System.Windows.Trigger> , vous définissez une propriété « condition » telle que : la <xref:System.Windows.UIElement.IsMouseOver%2A> valeur de la propriété du bouton est égale à `true` .</span><span class="sxs-lookup"><span data-stu-id="d4316-189">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="d4316-190">Vous définissez ensuite les méthodes setter (actions) qui ont lieu lorsque la condition de déclencheur a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="d4316-190">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="d4316-191">Pour créer une interactivité de bouton</span><span class="sxs-lookup"><span data-stu-id="d4316-191">To create button interactivity</span></span>

1. <span data-ttu-id="d4316-192">**Ajouter des déclencheurs de modèle :** Ajoutez le balisage en surbrillance à votre modèle.</span><span class="sxs-lookup"><span data-stu-id="d4316-192">**Add template triggers:** Add the highlighted markup to your template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}"
          Height="{TemplateBinding Height}" ClipToBounds="True">

          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch" Stroke="Transparent"
            StrokeThickness="20"
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"
          />

          <!-- Glass Rectangle -->
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch"
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
            Fill="{StaticResource MyGlassBrushResource}"
            RenderTransformOrigin="0.5,0.5">
            <Rectangle.Stroke>
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                <LinearGradientBrush.GradientStops>
                  <GradientStop Offset="0.0" Color="LightBlue" />
                  <GradientStop Offset="1.0" Color="Gray" />
                </LinearGradientBrush.GradientStops>
              </LinearGradientBrush>
            </Rectangle.Stroke>

            <!-- These transforms have no effect as they
                 are declared here.
                 The reason the transforms are included is to be targets
                 for animation (see later). -->
            <Rectangle.RenderTransform>
              <TransformGroup>
                <ScaleTransform />
                <RotateTransform />
              </TransformGroup>
            </Rectangle.RenderTransform>

              <!-- A BevelBitmapEffect is applied to give the button a
                   "Beveled" look. -->
            <Rectangle.BitmapEffect>
              <BevelBitmapEffect />
            </Rectangle.BitmapEffect>
          </Rectangle>

          <!-- Present Text of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20"
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>

        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>
      </ControlTemplate>
    </Setter.Value>
    ```

2. <span data-ttu-id="d4316-193">**Ajouter des déclencheurs de propriété :** Ajoutez le balisage en surbrillance au `ControlTemplate.Triggers` bloc :</span><span class="sxs-lookup"><span data-stu-id="d4316-193">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="d4316-194">Appuyez sur F5 pour exécuter l’application et voir l’effet lorsque vous exécutez le pointeur de la souris sur les boutons.</span><span class="sxs-lookup"><span data-stu-id="d4316-194">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="d4316-195">**Ajouter un déclencheur de Focus :** Ensuite, nous allons ajouter des accesseurs set similaires pour gérer le cas où le bouton a le focus (par exemple, une fois que l’utilisateur clique dessus).</span><span class="sxs-lookup"><span data-stu-id="d4316-195">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->
      <Trigger Property="IsMouseOver" Value="True">

        <!-- Below are three property settings that occur when the
             condition is met (user mouses over button).  -->
        <!-- Change the color of the outer rectangle when user          mouses over it. -->
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />

        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />

        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">
          <Setter.Value>
            <BlurBitmapEffect Radius="1" />
          </Setter.Value>
        </Setter>
      </Trigger>
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>

    </ControlTemplate.Triggers>
    ```

     <span data-ttu-id="d4316-196">Appuyez sur F5 pour exécuter l’application et cliquez sur l’un des boutons.</span><span class="sxs-lookup"><span data-stu-id="d4316-196">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="d4316-197">Notez que le bouton reste en surbrillance après avoir cliqué dessus, car il a toujours le focus.</span><span class="sxs-lookup"><span data-stu-id="d4316-197">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="d4316-198">Si vous cliquez sur un autre bouton, le nouveau bouton gagne le focus tandis que le dernier le perd.</span><span class="sxs-lookup"><span data-stu-id="d4316-198">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="d4316-199">**Ajouter des animations pour** <xref:System.Windows.UIElement.MouseEnter> **et** <xref:System.Windows.UIElement.MouseLeave> **:** Ensuite, nous ajoutons des animations aux déclencheurs.  </span><span class="sxs-lookup"><span data-stu-id="d4316-199">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="d4316-200">Ajoutez la balise suivante n’importe où dans le `ControlTemplate.Triggers` bloc.</span><span class="sxs-lookup"><span data-stu-id="d4316-200">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->
    <EventTrigger RoutedEvent="Mouse.MouseEnter">
      <EventTrigger.Actions>
        <BeginStoryboard Name="mouseEnterBeginStoryboard">
          <Storyboard>
          <!-- This animation makes the glass rectangle shrink in the X direction. -->
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"
              By="-0.1" Duration="0:0:0.5" />
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->
            <DoubleAnimation
            Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"
              By="-0.1" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    <EventTrigger RoutedEvent="Mouse.MouseLeave">
      <EventTrigger.Actions>
        <!-- Stopping the storyboard sets all animated properties back to default. -->
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="d4316-201">Le rectangle de transparence se réduit lorsque le pointeur de la souris se déplace sur le bouton et retourne à la taille normale lorsque le pointeur quitte.</span><span class="sxs-lookup"><span data-stu-id="d4316-201">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="d4316-202">Deux animations sont déclenchées lorsque le pointeur passe sur le bouton (l' <xref:System.Windows.UIElement.MouseEnter> événement est déclenché).</span><span class="sxs-lookup"><span data-stu-id="d4316-202">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="d4316-203">Ces animations réduisent le rectangle de transparence le long des axes X et Y.</span><span class="sxs-lookup"><span data-stu-id="d4316-203">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="d4316-204">Notez les propriétés sur les <xref:System.Windows.Media.Animation.DoubleAnimation> éléments, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .</span><span class="sxs-lookup"><span data-stu-id="d4316-204">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="d4316-205"><xref:System.Windows.Media.Animation.Timeline.Duration%2A>Spécifie que l’animation se produit pendant une demi-seconde et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> spécifie que la transparence est réduite de 10%.</span><span class="sxs-lookup"><span data-stu-id="d4316-205">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="d4316-206">Le deuxième déclencheur d’événements ( <xref:System.Windows.UIElement.MouseLeave> ) arrête simplement le premier.</span><span class="sxs-lookup"><span data-stu-id="d4316-206">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="d4316-207">Lorsque vous arrêtez un <xref:System.Windows.Media.Animation.Storyboard> , toutes les propriétés animées retournent à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="d4316-207">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="d4316-208">Par conséquent, lorsque l’utilisateur déplace le pointeur en dehors du bouton, le bouton revient à la façon dont il se trouvait avant le pointeur de la souris sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-208">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="d4316-209">Pour plus d’informations sur les animations, consultez [vue d’ensemble](../graphics-multimedia/animation-overview.md)de l’animation.</span><span class="sxs-lookup"><span data-stu-id="d4316-209">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="d4316-210">**Ajouter une animation pour lorsque l’utilisateur clique sur le bouton :** La dernière étape consiste à ajouter un déclencheur pour lorsque l’utilisateur clique sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="d4316-210">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="d4316-211">Ajoutez la balise suivante n’importe où dans le `ControlTemplate.Triggers` bloc :</span><span class="sxs-lookup"><span data-stu-id="d4316-211">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->
    <EventTrigger RoutedEvent="Button.Click">
      <EventTrigger.Actions>
        <BeginStoryboard>
          <Storyboard>
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"
              By="360" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="d4316-212">Appuyez sur F5 pour exécuter l’application, puis cliquez sur l’un des boutons.</span><span class="sxs-lookup"><span data-stu-id="d4316-212">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="d4316-213">Lorsque vous cliquez sur un bouton, le rectangle de transparence tourne.</span><span class="sxs-lookup"><span data-stu-id="d4316-213">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="d4316-214">Résumé</span><span class="sxs-lookup"><span data-stu-id="d4316-214">Summary</span></span>
 <span data-ttu-id="d4316-215">Dans cette procédure pas à pas, vous avez effectué les exercices suivants :</span><span class="sxs-lookup"><span data-stu-id="d4316-215">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="d4316-216">Ciblé a <xref:System.Windows.Style> vers un type d’objet ( <xref:System.Windows.Controls.Button> ).</span><span class="sxs-lookup"><span data-stu-id="d4316-216">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="d4316-217">Contrôle des propriétés de base des boutons de l’application entière à l’aide de <xref:System.Windows.Style> .</span><span class="sxs-lookup"><span data-stu-id="d4316-217">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="d4316-218">Ressources créées, comme des dégradés, à utiliser pour les valeurs de propriété des <xref:System.Windows.Style> accesseurs set.</span><span class="sxs-lookup"><span data-stu-id="d4316-218">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="d4316-219">Personnaliser l’apparence des boutons dans toute l’application en appliquant un modèle aux boutons.</span><span class="sxs-lookup"><span data-stu-id="d4316-219">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="d4316-220">Comportement personnalisé pour les boutons en réponse aux actions de l’utilisateur (telles que <xref:System.Windows.UIElement.MouseEnter> , <xref:System.Windows.UIElement.MouseLeave> et <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ) qui incluent des effets d’animation.</span><span class="sxs-lookup"><span data-stu-id="d4316-220">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4316-221">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4316-221">See also</span></span>

- [<span data-ttu-id="d4316-222">Créer un bouton à l'aide de Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="d4316-222">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="d4316-223">Application d'un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="d4316-223">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="d4316-224">Vue d'ensemble de l'animation</span><span class="sxs-lookup"><span data-stu-id="d4316-224">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="d4316-225">Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="d4316-225">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="d4316-226">Vue d'ensemble des effets bitmap</span><span class="sxs-lookup"><span data-stu-id="d4316-226">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
