---
title: Créer un modèle dans WPF-.NET Desktop
description: Découvrez comment créer et référencer un modèle de contrôle dans Windows Presentation Foundation et .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071247"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="9833f-103">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="9833f-103">Create a template for a control</span></span>

<span data-ttu-id="9833f-104">Avec Windows Presentation Foundation (WPF), vous pouvez personnaliser la structure visuelle et le comportement d’un contrôle existant avec votre propre modèle réutilisable.</span><span class="sxs-lookup"><span data-stu-id="9833f-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="9833f-105">Les modèles peuvent être appliqués globalement à votre application, à vos fenêtres et à vos pages, ou directement à des contrôles.</span><span class="sxs-lookup"><span data-stu-id="9833f-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="9833f-106">La plupart des scénarios qui requièrent la création d’un nouveau contrôle peuvent être couverts en créant à la place un nouveau modèle pour un contrôle existant.</span><span class="sxs-lookup"><span data-stu-id="9833f-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="9833f-107">Dans cet article, vous allez découvrir comment créer un <xref:System.Windows.Controls.ControlTemplate> nouveau pour <xref:System.Windows.Controls.Button> le contrôle.</span><span class="sxs-lookup"><span data-stu-id="9833f-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="9833f-108">Quand créer un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9833f-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="9833f-109">Les contrôles ont de nombreuses propriétés, <xref:System.Windows.Controls.Border.Background%2A>telles <xref:System.Windows.Controls.Control.Foreground%2A>que, <xref:System.Windows.Controls.Control.FontFamily%2A>et.</span><span class="sxs-lookup"><span data-stu-id="9833f-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="9833f-110">Ces propriétés contrôlent les différents aspects de l’apparence du contrôle, mais les modifications que vous pouvez apporter en définissant ces propriétés sont limitées.</span><span class="sxs-lookup"><span data-stu-id="9833f-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="9833f-111">Par exemple, vous pouvez affecter la <xref:System.Windows.Controls.Control.Foreground%2A> valeur Blue à la <xref:System.Windows.Controls.Control.FontStyle%2A> propriété et la valeur <xref:System.Windows.Controls.CheckBox>italique à un.</span><span class="sxs-lookup"><span data-stu-id="9833f-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="9833f-112">Si vous souhaitez personnaliser l’apparence du contrôle au-delà de ce que peut faire les autres propriétés du contrôle, vous créez <xref:System.Windows.Controls.ControlTemplate>un.</span><span class="sxs-lookup"><span data-stu-id="9833f-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="9833f-113">Dans la plupart des interfaces utilisateur, un bouton a la même apparence générale : un rectangle avec du texte.</span><span class="sxs-lookup"><span data-stu-id="9833f-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="9833f-114">Si vous souhaitez créer un bouton arrondi, vous pouvez créer un nouveau contrôle qui hérite du bouton ou recrée les fonctionnalités du bouton.</span><span class="sxs-lookup"><span data-stu-id="9833f-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="9833f-115">En outre, le nouveau contrôle utilisateur fournirait le visuel circulaire.</span><span class="sxs-lookup"><span data-stu-id="9833f-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="9833f-116">Vous pouvez éviter de créer de nouveaux contrôles en personnalisant la disposition visuelle d’un contrôle existant.</span><span class="sxs-lookup"><span data-stu-id="9833f-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="9833f-117">Avec un bouton arrondi, vous créez un <xref:System.Windows.Controls.ControlTemplate> avec la disposition visuelle souhaitée.</span><span class="sxs-lookup"><span data-stu-id="9833f-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="9833f-118">En revanche, si vous avez besoin d’un contrôle avec de nouvelles fonctionnalités, des propriétés différentes et de nouveaux paramètres, vous devez créer <xref:System.Windows.Controls.UserControl>un nouveau.</span><span class="sxs-lookup"><span data-stu-id="9833f-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9833f-119">Prérequis</span><span class="sxs-lookup"><span data-stu-id="9833f-119">Prerequisites</span></span>

<span data-ttu-id="9833f-120">Créez une application WPF et dans *MainWindow. Xaml* (ou une autre fenêtre de votre choix) définissez les propriétés suivantes sur l’élément>de la \*\* \<fenêtre\*\* :</span><span class="sxs-lookup"><span data-stu-id="9833f-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

<span data-ttu-id="9833f-121">Définissez le contenu de la \*\* \<fenêtre>\*\* élément sur le code XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="9833f-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="9833f-122">À la fin, le fichier *MainWindow. Xaml* doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="9833f-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="9833f-123">Si vous exécutez l’application, elle ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="9833f-123">If you run the application, it looks like the following:</span></span>

![Fenêtre WPF avec deux boutons sans style](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="9833f-125">Créer un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9833f-125">Create a ControlTemplate</span></span>

<span data-ttu-id="9833f-126">La méthode la plus courante pour déclarer <xref:System.Windows.Controls.ControlTemplate> un est en tant que ressource `Resources` dans la section d’un fichier XAML.</span><span class="sxs-lookup"><span data-stu-id="9833f-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="9833f-127">Étant donné que les modèles sont des ressources, ils obéissent aux mêmes règles de portée qui s’appliquent à toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="9833f-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="9833f-128">En d’autres termes, lorsque vous déclarez un modèle, vous affectez l’emplacement où le modèle peut être appliqué.</span><span class="sxs-lookup"><span data-stu-id="9833f-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="9833f-129">Par exemple, si vous déclarez le modèle dans l’élément racine de votre fichier XAML de définition d’application, le modèle peut être utilisé n’importe où dans votre application.</span><span class="sxs-lookup"><span data-stu-id="9833f-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="9833f-130">Si vous définissez le modèle dans une fenêtre, seuls les contrôles de cette fenêtre peuvent utiliser le modèle.</span><span class="sxs-lookup"><span data-stu-id="9833f-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="9833f-131">Pour commencer, ajoutez un `Window.Resources` élément à votre fichier *MainWindow. Xaml* :</span><span class="sxs-lookup"><span data-stu-id="9833f-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="9833f-132">Créez un \*\* \<>de ControlTemplate\*\* avec les propriétés suivantes définies :</span><span class="sxs-lookup"><span data-stu-id="9833f-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="9833f-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="9833f-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="9833f-134">Ce modèle de contrôle sera simple :</span><span class="sxs-lookup"><span data-stu-id="9833f-134">This control template will be simple:</span></span>

- <span data-ttu-id="9833f-135">élément racine pour le contrôle, un<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="9833f-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="9833f-136"><xref:System.Windows.Shapes.Ellipse> pour dessiner l’apparence arrondie du bouton</span><span class="sxs-lookup"><span data-stu-id="9833f-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="9833f-137"><xref:System.Windows.Controls.ContentPresenter> pour afficher le contenu du bouton spécifié par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="9833f-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="9833f-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="9833f-138">TemplateBinding</span></span>

<span data-ttu-id="9833f-139">Quand vous créez un nouveau <xref:System.Windows.Controls.ControlTemplate>, vous pouvez toujours utiliser les propriétés publiques pour modifier l’apparence du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9833f-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="9833f-140">L’extension de balisage [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) lie une propriété d’un élément qui se trouve <xref:System.Windows.Controls.ControlTemplate> dans à une propriété publique définie par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="9833f-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="9833f-141">Quand vous utilisez un [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), vous activez les propriétés du contrôle pour agir en tant que paramètres du modèle.</span><span class="sxs-lookup"><span data-stu-id="9833f-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="9833f-142">Autrement dit, quand une propriété sur un contrôle est définie, cette valeur est passée à l’élément qui a le [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="9833f-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="9833f-143">Ellipse</span><span class="sxs-lookup"><span data-stu-id="9833f-143">Ellipse</span></span>

<span data-ttu-id="9833f-144">Notez que les **:::no-loc text="Fill":::** propriétés **:::no-loc text="Stroke":::** et de l' \*\* \<élément ellipse>\*\* sont liées aux propriétés et <xref:System.Windows.Controls.Control.Background> du <xref:System.Windows.Controls.Control.Foreground> contrôle.</span><span class="sxs-lookup"><span data-stu-id="9833f-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="9833f-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="9833f-145">ContentPresenter</span></span>

<span data-ttu-id="9833f-146">Un élément de [ \<>ContentPresenter](xref:System.Windows.Controls.ContentPresenter) est également ajouté au modèle.</span><span class="sxs-lookup"><span data-stu-id="9833f-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="9833f-147">Étant donné que ce modèle est conçu pour un bouton, prenez en considération le fait que le <xref:System.Windows.Controls.ContentControl>bouton hérite de.</span><span class="sxs-lookup"><span data-stu-id="9833f-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="9833f-148">Le bouton présente le contenu de l’élément.</span><span class="sxs-lookup"><span data-stu-id="9833f-148">The button presents the content of the element.</span></span> <span data-ttu-id="9833f-149">Vous pouvez définir tout ce qui se trouve à l’intérieur du bouton, comme du texte brut ou même un autre contrôle.</span><span class="sxs-lookup"><span data-stu-id="9833f-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="9833f-150">Les deux types de boutons valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="9833f-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="9833f-151">Dans les deux exemples précédents, le texte et la case à cocher sont définis en tant que propriété [Button. Content](xref:System.Windows.Controls.ContentControl.Content) .</span><span class="sxs-lookup"><span data-stu-id="9833f-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="9833f-152">Tout ce qui est défini en tant que contenu peut être présenté par le biais d’un \*\* \<>ContentPresenter \*\*, ce que fait le modèle.</span><span class="sxs-lookup"><span data-stu-id="9833f-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="9833f-153">Si le <xref:System.Windows.Controls.ControlTemplate> est appliqué à un <xref:System.Windows.Controls.ContentControl> type, tel qu’un `Button`, une <xref:System.Windows.Controls.ContentPresenter> est recherchée dans l’arborescence d’éléments.</span><span class="sxs-lookup"><span data-stu-id="9833f-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="9833f-154">Si le `ContentPresenter` est trouvé, le modèle lie automatiquement la propriété du <xref:System.Windows.Controls.ContentControl.Content> contrôle à. `ContentPresenter`</span><span class="sxs-lookup"><span data-stu-id="9833f-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="9833f-155">Utiliser le modèle</span><span class="sxs-lookup"><span data-stu-id="9833f-155">Use the template</span></span>

<span data-ttu-id="9833f-156">Recherchez les boutons qui ont été déclarés au début de cet article.</span><span class="sxs-lookup"><span data-stu-id="9833f-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="9833f-157">Définissez la propriété du <xref:System.Windows.Controls.Control.Template> deuxième bouton sur la `roundbutton` ressource :</span><span class="sxs-lookup"><span data-stu-id="9833f-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="9833f-158">Si vous exécutez le projet et regardez le résultat, vous verrez que le bouton a un arrière-plan arrondi.</span><span class="sxs-lookup"><span data-stu-id="9833f-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Fenêtre WPF avec un bouton ovale de modèle](media/create-apply-template/styled-button.png)

<span data-ttu-id="9833f-160">Vous avez peut-être remarqué que le bouton n’est pas un cercle, mais qu’il est incliné.</span><span class="sxs-lookup"><span data-stu-id="9833f-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="9833f-161">En raison de la façon dont l' \*\* \<élément ellipse>\*\* fonctionne, il se développe toujours pour occuper l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="9833f-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="9833f-162">Définissez le cercle comme uniforme en remplaçant les propriétés **:::no-loc text="width":::** et **:::no-loc text="height":::** du bouton par la même valeur :</span><span class="sxs-lookup"><span data-stu-id="9833f-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Fenêtre WPF avec un seul modèle de bouton circulaire](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="9833f-164">Ajouter un déclencheur</span><span class="sxs-lookup"><span data-stu-id="9833f-164">Add a Trigger</span></span>

<span data-ttu-id="9833f-165">Même si un bouton avec un modèle appliqué semble différent, il se comporte comme n’importe quel autre bouton.</span><span class="sxs-lookup"><span data-stu-id="9833f-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="9833f-166">Si vous appuyez sur le bouton, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> l’événement se déclenche.</span><span class="sxs-lookup"><span data-stu-id="9833f-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="9833f-167">Toutefois, vous avez peut-être remarqué que lorsque vous déplacez votre souris sur le bouton, les éléments visuels du bouton ne changent pas.</span><span class="sxs-lookup"><span data-stu-id="9833f-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="9833f-168">Ces interactions visuelles sont toutes définies par le modèle.</span><span class="sxs-lookup"><span data-stu-id="9833f-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="9833f-169">Avec les systèmes d’événements et de propriétés dynamiques fournis par WPF, vous pouvez surveiller une propriété spécifique pour une valeur, puis restyleer le modèle lorsque cela est approprié.</span><span class="sxs-lookup"><span data-stu-id="9833f-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="9833f-170">Dans cet exemple, vous allez surveiller la propriété du <xref:System.Windows.UIElement.IsMouseOver> bouton.</span><span class="sxs-lookup"><span data-stu-id="9833f-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="9833f-171">Lorsque la souris se trouve sur le contrôle, le style de l' \*\* \<ellipse>\*\* avec une nouvelle couleur.</span><span class="sxs-lookup"><span data-stu-id="9833f-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="9833f-172">Ce type de déclencheur est appelé *PropertyTrigger*.</span><span class="sxs-lookup"><span data-stu-id="9833f-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="9833f-173">Pour que cela fonctionne, vous devez ajouter un nom à l' \*\* \<ellipse>\*\* que vous pouvez référencer.</span><span class="sxs-lookup"><span data-stu-id="9833f-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="9833f-174">Donnez-lui le nom de **backgroundElement**.</span><span class="sxs-lookup"><span data-stu-id="9833f-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="9833f-175">Ensuite, ajoutez un nouveau <xref:System.Windows.Trigger> à la collection [ControlTemplate. Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) .</span><span class="sxs-lookup"><span data-stu-id="9833f-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="9833f-176">Le déclencheur surveille l' `IsMouseOver` événement pour la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="9833f-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="9833f-177">Ensuite, ajoutez une \*\* \<>Setter\*\* au \*\* \<>de déclencheur\*\* qui remplace la propriété **Fill** de l' \*\* \<ellipse>\*\* par une nouvelle couleur.</span><span class="sxs-lookup"><span data-stu-id="9833f-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="9833f-178">Exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="9833f-178">Run the project.</span></span> <span data-ttu-id="9833f-179">Notez que lorsque vous placez le pointeur de la souris sur le bouton, la couleur de l' \*\* \<ellipse>\*\* change.</span><span class="sxs-lookup"><span data-stu-id="9833f-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![la souris se déplace sur le bouton WPF pour modifier la couleur de remplissage](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="9833f-181">Utiliser un VisualState</span><span class="sxs-lookup"><span data-stu-id="9833f-181">Use a VisualState</span></span>

<span data-ttu-id="9833f-182">Les États visuels sont définis et déclenchés par un contrôle.</span><span class="sxs-lookup"><span data-stu-id="9833f-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="9833f-183">Par exemple, lorsque la souris est déplacée au-dessus du contrôle `CommonStates.MouseOver` , l’État est déclenché.</span><span class="sxs-lookup"><span data-stu-id="9833f-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="9833f-184">Vous pouvez animer les modifications de propriété en fonction de l’état actuel du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9833f-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="9833f-185">Dans la section précédente, une \*\* \<>PropertyTrigger\*\* a été utilisée pour remplacer le premier plan du bouton `AliceBlue` par lorsque `IsMouseOver` la propriété `true`était.</span><span class="sxs-lookup"><span data-stu-id="9833f-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="9833f-186">Au lieu de cela, créez un état visuel qui anime la modification de cette couleur, en fournissant une transition lisse.</span><span class="sxs-lookup"><span data-stu-id="9833f-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="9833f-187">Pour plus d’informations sur *VisualStates*, consultez [styles et modèles dans WPF](../fundamentals/styles-templates-overview.md#visual-states).</span><span class="sxs-lookup"><span data-stu-id="9833f-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="9833f-188">Pour convertir le \*\* \<>PropertyTrigger\*\* en un état visuel animé, commencez par supprimer l' \*\* \<élément ControlTemplate. Triggers>\*\* de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="9833f-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="9833f-189">Ensuite, dans la \*\* \<grille>\*\* racine du modèle de contrôle, ajoutez l' \*\* \<élément VisualStateManager. VisualStateGroups>\*\* avec un \*\* \<>VisualStateGroup\*\* pour `CommonStates`.</span><span class="sxs-lookup"><span data-stu-id="9833f-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="9833f-190">Définissez deux États, `Normal` et `MouseOver`.</span><span class="sxs-lookup"><span data-stu-id="9833f-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="9833f-191">Les animations définies dans un \*\* \<>VisualState\*\* sont appliquées lorsque cet État est déclenché.</span><span class="sxs-lookup"><span data-stu-id="9833f-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="9833f-192">Créez des animations pour chaque État.</span><span class="sxs-lookup"><span data-stu-id="9833f-192">Create animations for each state.</span></span> <span data-ttu-id="9833f-193">Les animations sont placées à l’intérieur d’un élément de>d’une \*\* \<table de montage séquentiel\*\* .</span><span class="sxs-lookup"><span data-stu-id="9833f-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="9833f-194">Pour plus d’informations sur les storyboards, consultez [vue d’ensemble des storyboards](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9833f-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="9833f-195">Normal</span><span class="sxs-lookup"><span data-stu-id="9833f-195">Normal</span></span>

  <span data-ttu-id="9833f-196">Cet État anime le remplissage de l’ellipse, en le restaurant à la `Background` couleur du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9833f-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="9833f-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="9833f-197">MouseOver</span></span>

  <span data-ttu-id="9833f-198">Cet État anime la couleur de `Background` l’ellipse avec une nouvelle couleur `Yellow`:.</span><span class="sxs-lookup"><span data-stu-id="9833f-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="9833f-199">Le \*\* \<>de ControlTemplate\*\* doit maintenant ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="9833f-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="9833f-200">Exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="9833f-200">Run the project.</span></span> <span data-ttu-id="9833f-201">Notez que lorsque vous placez le pointeur de la souris sur le bouton, la couleur de l' \*\* \<ellipse>\*\* s’anime.</span><span class="sxs-lookup"><span data-stu-id="9833f-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![la souris se déplace sur le bouton WPF pour modifier la couleur de remplissage](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="9833f-203">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9833f-203">Next steps</span></span>

- [<span data-ttu-id="9833f-204">Créer un style pour un contrôle dans WPF</span><span class="sxs-lookup"><span data-stu-id="9833f-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="9833f-205">Styles et modèles dans WPF</span><span class="sxs-lookup"><span data-stu-id="9833f-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="9833f-206">Vue d’ensemble des ressources XAML</span><span class="sxs-lookup"><span data-stu-id="9833f-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
