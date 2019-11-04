---
title: Styles et modèles Thumb
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: c2114a02016db96d898a394b6892b6d3042d81ff
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458237"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="c293d-102">Styles et modèles Thumb</span><span class="sxs-lookup"><span data-stu-id="c293d-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="c293d-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="c293d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="c293d-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="c293d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c293d-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c293d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="c293d-106">Éléments Thumb</span><span class="sxs-lookup"><span data-stu-id="c293d-106">Thumb Parts</span></span>

<span data-ttu-id="c293d-107">Le contrôle <xref:System.Windows.Controls.Primitives.Thumb> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="c293d-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="c293d-108">États de Thumb</span><span class="sxs-lookup"><span data-stu-id="c293d-108">Thumb States</span></span>

<span data-ttu-id="c293d-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="c293d-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="c293d-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="c293d-110">VisualState Name</span></span>|<span data-ttu-id="c293d-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c293d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c293d-112">Description</span><span class="sxs-lookup"><span data-stu-id="c293d-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="c293d-113">Normale</span><span class="sxs-lookup"><span data-stu-id="c293d-113">Normal</span></span>|<span data-ttu-id="c293d-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c293d-114">CommonStates</span></span>|<span data-ttu-id="c293d-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="c293d-115">The default state.</span></span>|
|<span data-ttu-id="c293d-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="c293d-116">MouseOver</span></span>|<span data-ttu-id="c293d-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c293d-117">CommonStates</span></span>|<span data-ttu-id="c293d-118">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c293d-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="c293d-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="c293d-119">Pressed</span></span>|<span data-ttu-id="c293d-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c293d-120">CommonStates</span></span>|<span data-ttu-id="c293d-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="c293d-121">The control is pressed.</span></span>|
|<span data-ttu-id="c293d-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="c293d-122">Disabled</span></span>|<span data-ttu-id="c293d-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c293d-123">CommonStates</span></span>|<span data-ttu-id="c293d-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="c293d-124">The control is disabled.</span></span>|
|<span data-ttu-id="c293d-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="c293d-125">Focused</span></span>|<span data-ttu-id="c293d-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c293d-126">FocusStates</span></span>|<span data-ttu-id="c293d-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="c293d-127">The control has focus.</span></span>|
|<span data-ttu-id="c293d-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="c293d-128">Unfocused</span></span>|<span data-ttu-id="c293d-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c293d-129">FocusStates</span></span>|<span data-ttu-id="c293d-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="c293d-130">The control does not have focus.</span></span>|
|<span data-ttu-id="c293d-131">Valide</span><span class="sxs-lookup"><span data-stu-id="c293d-131">Valid</span></span>|<span data-ttu-id="c293d-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c293d-132">ValidationStates</span></span>|<span data-ttu-id="c293d-133">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="c293d-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="c293d-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c293d-134">InvalidFocused</span></span>|<span data-ttu-id="c293d-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c293d-135">ValidationStates</span></span>|<span data-ttu-id="c293d-136">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="c293d-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="c293d-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c293d-137">InvalidUnfocused</span></span>|<span data-ttu-id="c293d-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c293d-138">ValidationStates</span></span>|<span data-ttu-id="c293d-139">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="c293d-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="c293d-140">Thumb ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="c293d-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="c293d-141">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="c293d-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="c293d-142">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="c293d-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="c293d-143">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="c293d-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="c293d-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c293d-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c293d-145">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="c293d-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c293d-146">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="c293d-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c293d-147">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="c293d-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c293d-148">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c293d-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
