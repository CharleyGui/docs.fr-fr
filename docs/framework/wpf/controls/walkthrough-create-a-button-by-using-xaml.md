---
title: 'Procédure pas à pas : créer un bouton avec XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: a8cc227703e81e5de9dea7e44e10dfecca2cd05c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646465"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="3e555-102">Procédure pas à pas : créer un bouton avec XAML</span><span class="sxs-lookup"><span data-stu-id="3e555-102">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="3e555-103">L’objectif de cette procédure pas à pas est d’apprendre à créer un bouton d’animation pour une utilisation dans une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="3e555-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="3e555-104">Cette procédure pas à pas utilise des styles et un modèle pour créer une ressource bouton personnalisée qui permet la réutilisation du code et la séparation de la logique du bouton de la déclaration de bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="3e555-105">Cette procédure pas à pas [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]est entièrement écrite en .</span><span class="sxs-lookup"><span data-stu-id="3e555-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e555-106">Cette procédure pas à pas vous guide à travers les étapes pour [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] créer l’application en tapant ou en copiant et en collé dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e555-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="3e555-107">Si vous préférez apprendre à utiliser un concepteur pour créer la même application, voir [Créer un bouton en utilisant Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="3e555-107">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="3e555-108">Le chiffre suivant montre les boutons finis.</span><span class="sxs-lookup"><span data-stu-id="3e555-108">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="3e555-109">![Boutons personnalisés créés en utilisant XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="3e555-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="3e555-110">Créez des boutons de base</span><span class="sxs-lookup"><span data-stu-id="3e555-110">Create Basic Buttons</span></span>

<span data-ttu-id="3e555-111">Commençons par créer un nouveau projet et ajouter quelques boutons à la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3e555-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="3e555-112">Créer un nouveau projet WPF et ajouter des boutons à la fenêtre</span><span class="sxs-lookup"><span data-stu-id="3e555-112">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="3e555-113">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e555-113">Start Visual Studio.</span></span>

2. <span data-ttu-id="3e555-114">**Créer un nouveau projet WPF :** Sur le menu **du fichier,** pointez vers **New**, puis cliquez sur **Le projet**.</span><span class="sxs-lookup"><span data-stu-id="3e555-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="3e555-115">Trouvez le modèle **d’application Windows (WPF)** et nommez le projet "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="3e555-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="3e555-116">Cela créera le squelette de l’application.</span><span class="sxs-lookup"><span data-stu-id="3e555-116">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="3e555-117">**Ajoutez des boutons par défaut de base :** Tous les fichiers dont vous avez besoin pour cette procédure pas à pas sont fournis par le modèle.</span><span class="sxs-lookup"><span data-stu-id="3e555-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="3e555-118">Ouvrez le fichier Window1.xaml en le cliquant doublement dans Solution Explorer.</span><span class="sxs-lookup"><span data-stu-id="3e555-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="3e555-119">Par défaut, il <xref:System.Windows.Controls.Grid> y a un élément dans Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="3e555-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="3e555-120">Retirez <xref:System.Windows.Controls.Grid> l’élément et ajoutez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] quelques boutons à la page en tapant ou en copie et en coller le code surligné ci-dessus à Window1.xaml :</span><span class="sxs-lookup"><span data-stu-id="3e555-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

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

     <span data-ttu-id="3e555-121">Appuyez sur F5 pour exécuter l’application; vous devriez voir un ensemble de boutons qui ressemble à la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="3e555-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="3e555-122">![Trois boutons de base](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="3e555-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="3e555-123">Maintenant que vous avez créé les boutons de base, vous avez fini de travailler dans le fichier Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="3e555-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="3e555-124">Le reste de la procédure pas à pas se concentre sur le fichier app.xaml, la définition des styles et un modèle pour les boutons.</span><span class="sxs-lookup"><span data-stu-id="3e555-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="3e555-125">Définir les propriétés de base</span><span class="sxs-lookup"><span data-stu-id="3e555-125">Set Basic Properties</span></span>

<span data-ttu-id="3e555-126">Ensuite, nous allons définir quelques propriétés sur ces boutons pour contrôler l’apparence du bouton et la mise en page.</span><span class="sxs-lookup"><span data-stu-id="3e555-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="3e555-127">Plutôt que de définir les propriétés sur les boutons individuellement, vous utiliserez les ressources pour définir les propriétés bouton pour l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="3e555-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="3e555-128">Les ressources d’application sont conceptuellement semblables aux feuilles externes de style en cascade (CSS) pour les pages Web ; cependant, les ressources sont beaucoup plus puissantes que les feuilles de style en cascade (CSS), comme vous le verrez à la fin de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="3e555-128">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="3e555-129">Pour en savoir plus sur les ressources, consultez [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="3e555-129">To learn more about resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="3e555-130">Utiliser des styles pour définir les propriétés de base sur les boutons</span><span class="sxs-lookup"><span data-stu-id="3e555-130">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="3e555-131">**Décrivez un bloc Application.Resources :** Ouvrez app.xaml et ajoutez la balisage surlignée suivante si elle n’est pas déjà là:</span><span class="sxs-lookup"><span data-stu-id="3e555-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

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

     <span data-ttu-id="3e555-132">La portée des ressources est déterminée par l’endroit où vous définissez la ressource.</span><span class="sxs-lookup"><span data-stu-id="3e555-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="3e555-133">La définition `Application.Resources` des ressources dans le fichier app.xaml permet d’utiliser la ressource de n’importe où dans l’application.</span><span class="sxs-lookup"><span data-stu-id="3e555-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="3e555-134">Pour en savoir plus sur la définition de la portée de vos ressources, consultez [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="3e555-134">To learn more about defining the scope of your resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

2. <span data-ttu-id="3e555-135">**Créez un style et définissez les valeurs de base des propriétés avec lui :** Ajouter la marque suivante `Application.Resources` au bloc.</span><span class="sxs-lookup"><span data-stu-id="3e555-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="3e555-136">Cette balisage <xref:System.Windows.Style> crée un qui s’applique à <xref:System.Windows.FrameworkElement.Width%2A> tous les boutons de l’application, en définissant les boutons à 90 et le <xref:System.Windows.FrameworkElement.Margin%2A> à 10:</span><span class="sxs-lookup"><span data-stu-id="3e555-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="3e555-137">La <xref:System.Windows.Style.TargetType%2A> propriété précise que le style s’applique à tous les objets de type <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="3e555-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="3e555-138">Chacun <xref:System.Windows.Setter> établit une valeur <xref:System.Windows.Style>de propriété différente pour le .</span><span class="sxs-lookup"><span data-stu-id="3e555-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="3e555-139">Par conséquent, à ce stade, chaque bouton de l’application a une largeur de 90 et une marge de 10.</span><span class="sxs-lookup"><span data-stu-id="3e555-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="3e555-140">Si vous appuyez sur F5 pour exécuter l’application, vous voyez la fenêtre suivante.</span><span class="sxs-lookup"><span data-stu-id="3e555-140">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="3e555-141">![Boutons avec une largeur de 90 et une marge de 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="3e555-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="3e555-142">Il ya beaucoup plus que vous pouvez faire avec les styles, y compris une variété de façons d’affiner ce que les objets sont ciblés, spécifiant des valeurs de propriété complexes, et même en utilisant des styles comme entrée pour d’autres styles.</span><span class="sxs-lookup"><span data-stu-id="3e555-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="3e555-143">Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e555-143">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="3e555-144">**Définissez une valeur de propriété de style à une ressource :** Les ressources permettent un moyen simple de réutiliser des objets et des valeurs communément définis.</span><span class="sxs-lookup"><span data-stu-id="3e555-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="3e555-145">Il est particulièrement utile de définir des valeurs complexes en utilisant des ressources pour rendre votre code plus modulaire.</span><span class="sxs-lookup"><span data-stu-id="3e555-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="3e555-146">Ajoutez la balisage surlignée suivante à app.xaml.</span><span class="sxs-lookup"><span data-stu-id="3e555-146">Add the following highlighted markup to app.xaml.</span></span>

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

     <span data-ttu-id="3e555-147">Directement sous `Application.Resources` le bloc, vous avez créé une ressource appelée "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="3e555-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="3e555-148">Cette ressource définit un gradient horizontal.</span><span class="sxs-lookup"><span data-stu-id="3e555-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="3e555-149">Cette ressource peut être utilisée comme valeur de propriété de n’importe <xref:System.Windows.Controls.Control.Background%2A> où dans l’application, y compris à l’intérieur du setter de style bouton pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="3e555-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="3e555-150">Maintenant, tous les boutons <xref:System.Windows.Controls.Control.Background%2A> ont une valeur de propriété de ce gradient.</span><span class="sxs-lookup"><span data-stu-id="3e555-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="3e555-151">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="3e555-151">Press F5 to run the application.</span></span> <span data-ttu-id="3e555-152">Il devrait ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="3e555-152">It should look like the following.</span></span>

     <span data-ttu-id="3e555-153">![Boutons avec un arrière-plan dégradé](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="3e555-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="3e555-154">Créer un modèle qui définit l’apparence du bouton</span><span class="sxs-lookup"><span data-stu-id="3e555-154">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="3e555-155">Dans cette section, vous créez un modèle qui personnalise l’apparence (présentation) du bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="3e555-156">La présentation du bouton est composée de plusieurs objets, y compris des rectangles et d’autres composants pour donner au bouton un look unique.</span><span class="sxs-lookup"><span data-stu-id="3e555-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="3e555-157">Jusqu’à présent, le contrôle de l’apparence des boutons dans l’application a été limité à changer les propriétés du bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="3e555-158">Que faire si vous voulez apporter des changements plus radicaux à l’apparence du bouton?</span><span class="sxs-lookup"><span data-stu-id="3e555-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="3e555-159">Les modèles permettent un contrôle puissant sur la présentation d’un objet.</span><span class="sxs-lookup"><span data-stu-id="3e555-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="3e555-160">Étant donné que les modèles peuvent être utilisés dans les styles, vous pouvez appliquer un modèle à tous les objets auxquels le style s’applique (dans cette procédure pas à pas, le bouton).</span><span class="sxs-lookup"><span data-stu-id="3e555-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="3e555-161">Pour utiliser le modèle pour définir l’apparence du bouton</span><span class="sxs-lookup"><span data-stu-id="3e555-161">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="3e555-162">**Configurez le modèle :** Parce que <xref:System.Windows.Controls.Button> les <xref:System.Windows.Controls.Control.Template%2A> contrôles comme ont une propriété, vous pouvez définir la <xref:System.Windows.Style> valeur <xref:System.Windows.Setter>de propriété modèle tout comme les autres valeurs de propriété que nous avons mis dans un utilisation d’un .</span><span class="sxs-lookup"><span data-stu-id="3e555-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="3e555-163">Ajoutez la marque surlignée suivante à votre style de bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-163">Add the following highlighted markup to your button style.</span></span>

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

2. <span data-ttu-id="3e555-164">**Présentation du bouton Alter :** À ce stade, vous devez définir le modèle.</span><span class="sxs-lookup"><span data-stu-id="3e555-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="3e555-165">Ajoutez la balisage surlignée ci-après.</span><span class="sxs-lookup"><span data-stu-id="3e555-165">Add the following highlighted markup.</span></span> <span data-ttu-id="3e555-166">Cette balisage spécifie deux <xref:System.Windows.Shapes.Rectangle> éléments <xref:System.Windows.Controls.DockPanel>avec des bords arrondis, suivi d’un .</span><span class="sxs-lookup"><span data-stu-id="3e555-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="3e555-167">Le <xref:System.Windows.Controls.DockPanel> est utilisé <xref:System.Windows.Controls.ContentPresenter> pour héberger le bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="3e555-168">Un <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="3e555-169">Dans cette procédure pas à pas, le contenu est texte ("Button 1", "Button 2", "Button 3").</span><span class="sxs-lookup"><span data-stu-id="3e555-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="3e555-170">Tous les composants du modèle (les <xref:System.Windows.Controls.DockPanel>rectangles et les <xref:System.Windows.Controls.Grid>) sont disposés à l’intérieur d’un .</span><span class="sxs-lookup"><span data-stu-id="3e555-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

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

     <span data-ttu-id="3e555-171">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="3e555-171">Press F5 to run the application.</span></span> <span data-ttu-id="3e555-172">Il devrait ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="3e555-172">It should look like the following.</span></span>

     ![Fenêtre avec 3 boutons](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="3e555-174">**Ajoutez un effet de verre au modèle :** Ensuite, vous ajouterez le verre.</span><span class="sxs-lookup"><span data-stu-id="3e555-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="3e555-175">Tout d’abord, vous créez des ressources qui créent un effet de gradient de verre.</span><span class="sxs-lookup"><span data-stu-id="3e555-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="3e555-176">Ajoutez ces ressources de `Application.Resources` gradient n’importe où dans le bloc :</span><span class="sxs-lookup"><span data-stu-id="3e555-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

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

     <span data-ttu-id="3e555-177">Ces ressources sont <xref:System.Windows.Shapes.Shape.Fill%2A> utilisées comme pour un <xref:System.Windows.Controls.Grid> rectangle que nous insérons dans le modèle de bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="3e555-178">Ajoutez la marque surlignée suivante au modèle.</span><span class="sxs-lookup"><span data-stu-id="3e555-178">Add the following highlighted markup to the template.</span></span>

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

     <span data-ttu-id="3e555-179">Notez <xref:System.Windows.UIElement.Opacity%2A> que le rectangle `x:Name` avec la propriété de "glassCube" est de 0, donc quand vous exécutez l’échantillon, vous ne voyez pas le rectangle de verre superposé sur le dessus.</span><span class="sxs-lookup"><span data-stu-id="3e555-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="3e555-180">C’est parce que nous allons plus tard ajouter des déclencheurs au modèle pour quand l’utilisateur interagit avec le bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="3e555-181">Cependant, vous pouvez voir à quoi ressemble <xref:System.Windows.UIElement.Opacity%2A> le bouton maintenant en changeant la valeur à 1 et en exécutant l’application.</span><span class="sxs-lookup"><span data-stu-id="3e555-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="3e555-182">Voir la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="3e555-182">See the following figure.</span></span> <span data-ttu-id="3e555-183">Avant de passer à l’étape suivante, changez le <xref:System.Windows.UIElement.Opacity%2A> dos à 0.</span><span class="sxs-lookup"><span data-stu-id="3e555-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="3e555-184">![Boutons personnalisés créés en utilisant XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="3e555-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="3e555-185">Créer l’interactivité bouton</span><span class="sxs-lookup"><span data-stu-id="3e555-185">Create Button Interactivity</span></span>

<span data-ttu-id="3e555-186">Dans cette section, vous créerez des déclencheurs de propriété et des déclencheurs d’événements pour changer les valeurs de propriété et exécuter des animations en réponse aux actions de l’utilisateur telles que le déplacement du pointeur de souris sur le bouton et le clic.</span><span class="sxs-lookup"><span data-stu-id="3e555-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="3e555-187">Un moyen facile d’ajouter l’interactivité (souris-over, souris-laisser, cliquez, et ainsi de suite) est de définir les déclencheurs dans votre modèle ou style.</span><span class="sxs-lookup"><span data-stu-id="3e555-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="3e555-188">Pour créer <xref:System.Windows.Trigger>un , vous définissez une propriété <xref:System.Windows.UIElement.IsMouseOver%2A> "condition" `true`telle que: La valeur de la propriété bouton est égale à .</span><span class="sxs-lookup"><span data-stu-id="3e555-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="3e555-189">Vous définissez ensuite les setters (actions) qui ont lieu lorsque l’état de déclenchement est vrai.</span><span class="sxs-lookup"><span data-stu-id="3e555-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="3e555-190">Créer l’interactivité des boutons</span><span class="sxs-lookup"><span data-stu-id="3e555-190">To create button interactivity</span></span>

1. <span data-ttu-id="3e555-191">**Ajouter des déclencheurs de modèle :** Ajoutez la marque mise en évidence à votre modèle.</span><span class="sxs-lookup"><span data-stu-id="3e555-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>

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

2. <span data-ttu-id="3e555-192">**Ajouter les déclencheurs de propriété :** Ajoutez la marque mise `ControlTemplate.Triggers` en évidence au bloc :</span><span class="sxs-lookup"><span data-stu-id="3e555-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="3e555-193">Appuyez sur F5 pour exécuter l’application et voir l’effet que vous exécutez le pointeur de la souris sur les boutons.</span><span class="sxs-lookup"><span data-stu-id="3e555-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="3e555-194">**Ajouter un déclencheur de mise au point :** Ensuite, nous ajouterons des setters similaires pour gérer le boîtier lorsque le bouton est focalisateur (par exemple, après que l’utilisateur l’a cliqué).</span><span class="sxs-lookup"><span data-stu-id="3e555-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

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

     <span data-ttu-id="3e555-195">Appuyez sur F5 pour exécuter l’application et cliquez sur l’un des boutons.</span><span class="sxs-lookup"><span data-stu-id="3e555-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="3e555-196">Notez que le bouton reste surligné après avoir cliqué parce qu’il a toujours mise au point.</span><span class="sxs-lookup"><span data-stu-id="3e555-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="3e555-197">Si vous cliquez sur un autre bouton, le nouveau bouton se concentre tandis que le dernier le perd.</span><span class="sxs-lookup"><span data-stu-id="3e555-197">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="3e555-198">**Ajoutez des animations pour** <xref:System.Windows.UIElement.MouseEnter> **et** <xref:System.Windows.UIElement.MouseLeave> **:** Ensuite, nous ajoutons quelques animations aux déclencheurs.  </span><span class="sxs-lookup"><span data-stu-id="3e555-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="3e555-199">Ajouter la balisage suivante `ControlTemplate.Triggers` n’importe où à l’intérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="3e555-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

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

     <span data-ttu-id="3e555-200">Le rectangle de verre se rétrécit lorsque le pointeur de la souris se déplace sur le bouton et revient à la taille normale lorsque le pointeur quitte.</span><span class="sxs-lookup"><span data-stu-id="3e555-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="3e555-201">Il ya deux animations qui sont déclenchées<xref:System.Windows.UIElement.MouseEnter> lorsque le pointeur va sur le bouton (l’événement est soulevé).</span><span class="sxs-lookup"><span data-stu-id="3e555-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="3e555-202">Ces animations rétrécissent le rectangle de verre le long de l’axe X et Y.</span><span class="sxs-lookup"><span data-stu-id="3e555-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="3e555-203">Remarquez les <xref:System.Windows.Media.Animation.DoubleAnimation> propriétés <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>sur les éléments — et .</span><span class="sxs-lookup"><span data-stu-id="3e555-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="3e555-204">Le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> spécifie que l’animation <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> se produit plus d’une demi-seconde, et précise que le verre rétrécit de 10%.</span><span class="sxs-lookup"><span data-stu-id="3e555-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="3e555-205">Le deuxième déclencheur<xref:System.Windows.UIElement.MouseLeave>de l’événement ( ) arrête simplement le premier.</span><span class="sxs-lookup"><span data-stu-id="3e555-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="3e555-206">Lorsque vous <xref:System.Windows.Media.Animation.Storyboard>arrêtez un , toutes les propriétés animées reviennent à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="3e555-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="3e555-207">Par conséquent, lorsque l’utilisateur déplace le pointeur sur le bouton, le bouton remonte à la façon dont il était avant que le pointeur de la souris déplacé sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="3e555-208">Pour plus d’informations sur les animations, voir [Aperçu animation](../graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e555-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="3e555-209">**Ajoutez une animation pour quand le bouton est cliqué :** La dernière étape consiste à ajouter un déclencheur pour quand l’utilisateur clique sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="3e555-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="3e555-210">Ajoutez la balisage suivante `ControlTemplate.Triggers` n’importe où à l’intérieur du bloc :</span><span class="sxs-lookup"><span data-stu-id="3e555-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

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

     <span data-ttu-id="3e555-211">Appuyez sur F5 pour exécuter l’application, et cliquez sur l’un des boutons.</span><span class="sxs-lookup"><span data-stu-id="3e555-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="3e555-212">Lorsque vous cliquez sur un bouton, le rectangle de verre tourne autour.</span><span class="sxs-lookup"><span data-stu-id="3e555-212">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="3e555-213">Résumé</span><span class="sxs-lookup"><span data-stu-id="3e555-213">Summary</span></span>
 <span data-ttu-id="3e555-214">Dans cette procédure pas à pas, vous avez effectué les exercices suivants :</span><span class="sxs-lookup"><span data-stu-id="3e555-214">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="3e555-215">Ciblé <xref:System.Windows.Style> un à un<xref:System.Windows.Controls.Button>type d’objet ( ).</span><span class="sxs-lookup"><span data-stu-id="3e555-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="3e555-216">Propriétés de base contrôlées des boutons <xref:System.Windows.Style>dans l’ensemble de l’application en utilisant le .</span><span class="sxs-lookup"><span data-stu-id="3e555-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="3e555-217">Création de ressources comme des gradients <xref:System.Windows.Style> à utiliser pour la valeur des propriétés des setters.</span><span class="sxs-lookup"><span data-stu-id="3e555-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="3e555-218">Personnalisé l’apparence des boutons dans l’ensemble de l’application en appliquant un modèle sur les boutons.</span><span class="sxs-lookup"><span data-stu-id="3e555-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="3e555-219">Comportement personnalisé pour les boutons en réponse aux <xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.UIElement.MouseLeave>actions <xref:System.Windows.Controls.Primitives.ButtonBase.Click>de l’utilisateur (tels que , , et ) qui comprenait des effets d’animation.</span><span class="sxs-lookup"><span data-stu-id="3e555-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e555-220">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e555-220">See also</span></span>

- [<span data-ttu-id="3e555-221">Créer un bouton à l'aide de Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="3e555-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="3e555-222">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="3e555-222">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3e555-223">Vue d'ensemble de l'animation</span><span class="sxs-lookup"><span data-stu-id="3e555-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="3e555-224">Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="3e555-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="3e555-225">Vue d'ensemble des effets bitmap</span><span class="sxs-lookup"><span data-stu-id="3e555-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
