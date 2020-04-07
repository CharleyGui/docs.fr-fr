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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805909"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="fb02c-102">Styles et modèles ToggleButton</span><span class="sxs-lookup"><span data-stu-id="fb02c-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="fb02c-103">Ce sujet décrit les styles et <xref:System.Windows.Controls.Primitives.ToggleButton> les modèles pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="fb02c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="fb02c-104">Vous pouvez modifier <xref:System.Windows.Controls.ControlTemplate> la valeur par défaut pour donner au contrôle une apparence unique.</span><span class="sxs-lookup"><span data-stu-id="fb02c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fb02c-105">Pour plus d’informations, voir [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="fb02c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="fb02c-106">Pièces ToggleButton</span><span class="sxs-lookup"><span data-stu-id="fb02c-106">ToggleButton Parts</span></span>

<span data-ttu-id="fb02c-107">Le <xref:System.Windows.Controls.Primitives.ToggleButton> contrôle n’a pas de pièces nommées.</span><span class="sxs-lookup"><span data-stu-id="fb02c-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="fb02c-108">ToggleButton États</span><span class="sxs-lookup"><span data-stu-id="fb02c-108">ToggleButton States</span></span>

<span data-ttu-id="fb02c-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.ToggleButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="fb02c-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="fb02c-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="fb02c-110">VisualState Name</span></span>|<span data-ttu-id="fb02c-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="fb02c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="fb02c-112">Description</span><span class="sxs-lookup"><span data-stu-id="fb02c-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="fb02c-113">Normal</span><span class="sxs-lookup"><span data-stu-id="fb02c-113">Normal</span></span>|<span data-ttu-id="fb02c-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-114">CommonStates</span></span>|<span data-ttu-id="fb02c-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="fb02c-115">The default state.</span></span>|
|<span data-ttu-id="fb02c-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="fb02c-116">MouseOver</span></span>|<span data-ttu-id="fb02c-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-117">CommonStates</span></span>|<span data-ttu-id="fb02c-118">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="fb02c-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="fb02c-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="fb02c-119">Pressed</span></span>|<span data-ttu-id="fb02c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-120">CommonStates</span></span>|<span data-ttu-id="fb02c-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="fb02c-121">The control is pressed.</span></span>|
|<span data-ttu-id="fb02c-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="fb02c-122">Disabled</span></span>|<span data-ttu-id="fb02c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-123">CommonStates</span></span>|<span data-ttu-id="fb02c-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="fb02c-124">The control is disabled.</span></span>|
|<span data-ttu-id="fb02c-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="fb02c-125">Focused</span></span>|<span data-ttu-id="fb02c-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-126">FocusStates</span></span>|<span data-ttu-id="fb02c-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="fb02c-127">The control has focus.</span></span>|
|<span data-ttu-id="fb02c-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="fb02c-128">Unfocused</span></span>|<span data-ttu-id="fb02c-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-129">FocusStates</span></span>|<span data-ttu-id="fb02c-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="fb02c-130">The control does not have focus.</span></span>|
|<span data-ttu-id="fb02c-131">Activé</span><span class="sxs-lookup"><span data-stu-id="fb02c-131">Checked</span></span>|<span data-ttu-id="fb02c-132">CheckStates (en)</span><span class="sxs-lookup"><span data-stu-id="fb02c-132">CheckStates</span></span>|<span data-ttu-id="fb02c-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="fb02c-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="fb02c-134">Désactivé</span><span class="sxs-lookup"><span data-stu-id="fb02c-134">Unchecked</span></span>|<span data-ttu-id="fb02c-135">CheckStates (en)</span><span class="sxs-lookup"><span data-stu-id="fb02c-135">CheckStates</span></span>|<span data-ttu-id="fb02c-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="fb02c-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="fb02c-137">Indéterminé</span><span class="sxs-lookup"><span data-stu-id="fb02c-137">Indeterminate</span></span>|<span data-ttu-id="fb02c-138">CheckStates (en)</span><span class="sxs-lookup"><span data-stu-id="fb02c-138">CheckStates</span></span>|<span data-ttu-id="fb02c-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> a la valeur `true` et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="fb02c-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="fb02c-140">Valide</span><span class="sxs-lookup"><span data-stu-id="fb02c-140">Valid</span></span>|<span data-ttu-id="fb02c-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-141">ValidationStates</span></span>|<span data-ttu-id="fb02c-142">Le contrôle <xref:System.Windows.Controls.Validation> utilise la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> classe `false`et la propriété ci-jointe est .</span><span class="sxs-lookup"><span data-stu-id="fb02c-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="fb02c-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fb02c-143">InvalidFocused</span></span>|<span data-ttu-id="fb02c-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-144">ValidationStates</span></span>|<span data-ttu-id="fb02c-145">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété `true` ci-jointe est et le contrôle a mise au point.</span><span class="sxs-lookup"><span data-stu-id="fb02c-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|
|<span data-ttu-id="fb02c-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fb02c-146">InvalidUnfocused</span></span>|<span data-ttu-id="fb02c-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb02c-147">ValidationStates</span></span>|<span data-ttu-id="fb02c-148">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété `true` ci-jointe est et le contrôle n’a pas de mise au point.</span><span class="sxs-lookup"><span data-stu-id="fb02c-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="fb02c-149">Si l’état visuel indéterminé n’existe pas dans votre modèle de contrôle, alors l’état visuel non contrôlé sera utilisé comme état visuel par défaut.</span><span class="sxs-lookup"><span data-stu-id="fb02c-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="fb02c-150">ToggleButton ControlTemplate Exemple</span><span class="sxs-lookup"><span data-stu-id="fb02c-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="fb02c-151">L’exemple suivant montre <xref:System.Windows.Controls.ControlTemplate> comment <xref:System.Windows.Controls.Primitives.ToggleButton> définir un pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="fb02c-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="fb02c-152">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="fb02c-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="fb02c-153">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="fb02c-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb02c-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb02c-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="fb02c-155">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="fb02c-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="fb02c-156">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="fb02c-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="fb02c-157">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="fb02c-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="fb02c-158">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="fb02c-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
