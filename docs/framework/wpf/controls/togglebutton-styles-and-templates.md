---
title: Styles et modèles ToggleButton
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: a4c449a561017659db7f54fd3cdb8964742650de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283675"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="735b7-102">Styles et modèles ToggleButton</span><span class="sxs-lookup"><span data-stu-id="735b7-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="735b7-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="735b7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="735b7-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="735b7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="735b7-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="735b7-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="735b7-106">Éléments ToggleButton</span><span class="sxs-lookup"><span data-stu-id="735b7-106">ToggleButton Parts</span></span>

<span data-ttu-id="735b7-107">Le contrôle <xref:System.Windows.Controls.Primitives.ToggleButton> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="735b7-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="735b7-108">États ToggleButton</span><span class="sxs-lookup"><span data-stu-id="735b7-108">ToggleButton States</span></span>

<span data-ttu-id="735b7-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="735b7-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="735b7-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="735b7-110">VisualState Name</span></span>|<span data-ttu-id="735b7-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="735b7-111">VisualStateGroup Name</span></span>|<span data-ttu-id="735b7-112">Description</span><span class="sxs-lookup"><span data-stu-id="735b7-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="735b7-113">Normal</span><span class="sxs-lookup"><span data-stu-id="735b7-113">Normal</span></span>|<span data-ttu-id="735b7-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="735b7-114">CommonStates</span></span>|<span data-ttu-id="735b7-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="735b7-115">The default state.</span></span>|
|<span data-ttu-id="735b7-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="735b7-116">MouseOver</span></span>|<span data-ttu-id="735b7-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="735b7-117">CommonStates</span></span>|<span data-ttu-id="735b7-118">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="735b7-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="735b7-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="735b7-119">Pressed</span></span>|<span data-ttu-id="735b7-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="735b7-120">CommonStates</span></span>|<span data-ttu-id="735b7-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="735b7-121">The control is pressed.</span></span>|
|<span data-ttu-id="735b7-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="735b7-122">Disabled</span></span>|<span data-ttu-id="735b7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="735b7-123">CommonStates</span></span>|<span data-ttu-id="735b7-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="735b7-124">The control is disabled.</span></span>|
|<span data-ttu-id="735b7-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="735b7-125">Focused</span></span>|<span data-ttu-id="735b7-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="735b7-126">FocusStates</span></span>|<span data-ttu-id="735b7-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="735b7-127">The control has focus.</span></span>|
|<span data-ttu-id="735b7-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="735b7-128">Unfocused</span></span>|<span data-ttu-id="735b7-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="735b7-129">FocusStates</span></span>|<span data-ttu-id="735b7-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="735b7-130">The control does not have focus.</span></span>|
|<span data-ttu-id="735b7-131">Activé</span><span class="sxs-lookup"><span data-stu-id="735b7-131">Checked</span></span>|<span data-ttu-id="735b7-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="735b7-132">CheckStates</span></span>|<span data-ttu-id="735b7-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="735b7-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="735b7-134">Désactivée</span><span class="sxs-lookup"><span data-stu-id="735b7-134">Unchecked</span></span>|<span data-ttu-id="735b7-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="735b7-135">CheckStates</span></span>|<span data-ttu-id="735b7-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `false`.</span><span class="sxs-lookup"><span data-stu-id="735b7-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="735b7-137">Déterminée</span><span class="sxs-lookup"><span data-stu-id="735b7-137">Indeterminate</span></span>|<span data-ttu-id="735b7-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="735b7-138">CheckStates</span></span>|<span data-ttu-id="735b7-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> est `true`et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `null`.</span><span class="sxs-lookup"><span data-stu-id="735b7-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="735b7-140">Valide</span><span class="sxs-lookup"><span data-stu-id="735b7-140">Valid</span></span>|<span data-ttu-id="735b7-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="735b7-141">ValidationStates</span></span>|<span data-ttu-id="735b7-142">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="735b7-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="735b7-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="735b7-143">InvalidFocused</span></span>|<span data-ttu-id="735b7-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="735b7-144">ValidationStates</span></span>|<span data-ttu-id="735b7-145">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="735b7-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="735b7-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="735b7-146">InvalidUnfocused</span></span>|<span data-ttu-id="735b7-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="735b7-147">ValidationStates</span></span>|<span data-ttu-id="735b7-148">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="735b7-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="735b7-149">Si l’état visuel indéterminé n’existe pas dans votre modèle de contrôle, l’état visuel non vérifié sera utilisé comme état visuel par défaut.</span><span class="sxs-lookup"><span data-stu-id="735b7-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="735b7-150">Exemple de ControlTemplate ToggleButton</span><span class="sxs-lookup"><span data-stu-id="735b7-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="735b7-151">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="735b7-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="735b7-152">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="735b7-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="735b7-153">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="735b7-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="735b7-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="735b7-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="735b7-155">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="735b7-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="735b7-156">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="735b7-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="735b7-157">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="735b7-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="735b7-158">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="735b7-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
