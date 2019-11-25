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
ms.openlocfilehash: 0d0d88e3b527beacfa5f879027e696aa75b18147
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283679"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="0d0c3-102">Styles et modèles Thumb</span><span class="sxs-lookup"><span data-stu-id="0d0c3-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="0d0c3-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="0d0c3-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0d0c3-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="0d0c3-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="0d0c3-106">Éléments Thumb</span><span class="sxs-lookup"><span data-stu-id="0d0c3-106">Thumb Parts</span></span>

<span data-ttu-id="0d0c3-107">Le contrôle <xref:System.Windows.Controls.Primitives.Thumb> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="0d0c3-108">États de Thumb</span><span class="sxs-lookup"><span data-stu-id="0d0c3-108">Thumb States</span></span>

<span data-ttu-id="0d0c3-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="0d0c3-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="0d0c3-110">VisualState Name</span></span>|<span data-ttu-id="0d0c3-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="0d0c3-111">VisualStateGroup Name</span></span>|<span data-ttu-id="0d0c3-112">Description</span><span class="sxs-lookup"><span data-stu-id="0d0c3-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="0d0c3-113">Normale</span><span class="sxs-lookup"><span data-stu-id="0d0c3-113">Normal</span></span>|<span data-ttu-id="0d0c3-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-114">CommonStates</span></span>|<span data-ttu-id="0d0c3-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-115">The default state.</span></span>|
|<span data-ttu-id="0d0c3-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="0d0c3-116">MouseOver</span></span>|<span data-ttu-id="0d0c3-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-117">CommonStates</span></span>|<span data-ttu-id="0d0c3-118">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="0d0c3-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="0d0c3-119">Pressed</span></span>|<span data-ttu-id="0d0c3-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-120">CommonStates</span></span>|<span data-ttu-id="0d0c3-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-121">The control is pressed.</span></span>|
|<span data-ttu-id="0d0c3-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="0d0c3-122">Disabled</span></span>|<span data-ttu-id="0d0c3-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-123">CommonStates</span></span>|<span data-ttu-id="0d0c3-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-124">The control is disabled.</span></span>|
|<span data-ttu-id="0d0c3-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="0d0c3-125">Focused</span></span>|<span data-ttu-id="0d0c3-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-126">FocusStates</span></span>|<span data-ttu-id="0d0c3-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-127">The control has focus.</span></span>|
|<span data-ttu-id="0d0c3-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="0d0c3-128">Unfocused</span></span>|<span data-ttu-id="0d0c3-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-129">FocusStates</span></span>|<span data-ttu-id="0d0c3-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-130">The control does not have focus.</span></span>|
|<span data-ttu-id="0d0c3-131">Valide</span><span class="sxs-lookup"><span data-stu-id="0d0c3-131">Valid</span></span>|<span data-ttu-id="0d0c3-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-132">ValidationStates</span></span>|<span data-ttu-id="0d0c3-133">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="0d0c3-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0d0c3-134">InvalidFocused</span></span>|<span data-ttu-id="0d0c3-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-135">ValidationStates</span></span>|<span data-ttu-id="0d0c3-136">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="0d0c3-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0d0c3-137">InvalidUnfocused</span></span>|<span data-ttu-id="0d0c3-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0d0c3-138">ValidationStates</span></span>|<span data-ttu-id="0d0c3-139">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="0d0c3-140">Thumb ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="0d0c3-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="0d0c3-141">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="0d0c3-142">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="0d0c3-143">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="0d0c3-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d0c3-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d0c3-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="0d0c3-145">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="0d0c3-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="0d0c3-146">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="0d0c3-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="0d0c3-147">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="0d0c3-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="0d0c3-148">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="0d0c3-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
