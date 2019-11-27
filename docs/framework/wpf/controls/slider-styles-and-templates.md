---
title: Styles et modèles Slider
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
ms.openlocfilehash: f533142d5ba202bd4aaf628487eaaa2a18a535d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283387"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="4fbf1-102">Styles et modèles Slider</span><span class="sxs-lookup"><span data-stu-id="4fbf1-102">Slider Styles and Templates</span></span>
<span data-ttu-id="4fbf1-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="4fbf1-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4fbf1-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="4fbf1-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="4fbf1-106">Composants Slider</span><span class="sxs-lookup"><span data-stu-id="4fbf1-106">Slider Parts</span></span>  
 <span data-ttu-id="4fbf1-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="4fbf1-108">Élément</span><span class="sxs-lookup"><span data-stu-id="4fbf1-108">Part</span></span>|<span data-ttu-id="4fbf1-109">Type</span><span class="sxs-lookup"><span data-stu-id="4fbf1-109">Type</span></span>|<span data-ttu-id="4fbf1-110">Description</span><span class="sxs-lookup"><span data-stu-id="4fbf1-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4fbf1-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="4fbf1-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="4fbf1-112">Conteneur de l’élément qui indique la position du <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="4fbf1-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="4fbf1-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="4fbf1-114">Élément qui affiche une plage de sélection le long du <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="4fbf1-115">La plage de sélection est visible uniquement si la propriété <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="4fbf1-116">États du curseur</span><span class="sxs-lookup"><span data-stu-id="4fbf1-116">Slider States</span></span>  
 <span data-ttu-id="4fbf1-117">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="4fbf1-118">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="4fbf1-118">VisualState Name</span></span>|<span data-ttu-id="4fbf1-119">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="4fbf1-119">VisualStateGroup Name</span></span>|<span data-ttu-id="4fbf1-120">Description</span><span class="sxs-lookup"><span data-stu-id="4fbf1-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="4fbf1-121">Normal</span><span class="sxs-lookup"><span data-stu-id="4fbf1-121">Normal</span></span>|<span data-ttu-id="4fbf1-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4fbf1-122">CommonStates</span></span>|<span data-ttu-id="4fbf1-123">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-123">The default state.</span></span>|  
|<span data-ttu-id="4fbf1-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="4fbf1-124">MouseOver</span></span>|<span data-ttu-id="4fbf1-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4fbf1-125">CommonStates</span></span>|<span data-ttu-id="4fbf1-126">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="4fbf1-127">Désactivé</span><span class="sxs-lookup"><span data-stu-id="4fbf1-127">Disabled</span></span>|<span data-ttu-id="4fbf1-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4fbf1-128">CommonStates</span></span>|<span data-ttu-id="4fbf1-129">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-129">The control is disabled.</span></span>|  
|<span data-ttu-id="4fbf1-130">Avec focus</span><span class="sxs-lookup"><span data-stu-id="4fbf1-130">Focused</span></span>|<span data-ttu-id="4fbf1-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="4fbf1-131">FocusStates</span></span>|<span data-ttu-id="4fbf1-132">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-132">The control has focus.</span></span>|  
|<span data-ttu-id="4fbf1-133">Sans focus</span><span class="sxs-lookup"><span data-stu-id="4fbf1-133">Unfocused</span></span>|<span data-ttu-id="4fbf1-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="4fbf1-134">FocusStates</span></span>|<span data-ttu-id="4fbf1-135">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="4fbf1-136">Valide</span><span class="sxs-lookup"><span data-stu-id="4fbf1-136">Valid</span></span>|<span data-ttu-id="4fbf1-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4fbf1-137">ValidationStates</span></span>|<span data-ttu-id="4fbf1-138">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4fbf1-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4fbf1-139">InvalidFocused</span></span>|<span data-ttu-id="4fbf1-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4fbf1-140">ValidationStates</span></span>|<span data-ttu-id="4fbf1-141">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="4fbf1-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4fbf1-142">InvalidUnfocused</span></span>|<span data-ttu-id="4fbf1-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4fbf1-143">ValidationStates</span></span>|<span data-ttu-id="4fbf1-144">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="4fbf1-145">Exemple de ControlTemplate Slider</span><span class="sxs-lookup"><span data-stu-id="4fbf1-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="4fbf1-146">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="4fbf1-147">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="4fbf1-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4fbf1-148">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="4fbf1-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fbf1-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fbf1-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="4fbf1-150">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="4fbf1-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="4fbf1-151">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="4fbf1-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="4fbf1-152">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="4fbf1-152">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="4fbf1-153">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="4fbf1-153">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
