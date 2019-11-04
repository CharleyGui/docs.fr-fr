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
ms.openlocfilehash: 334cb4a44788980262110eadac3305283bb61a92
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458394"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="a0f18-102">Styles et modèles Slider</span><span class="sxs-lookup"><span data-stu-id="a0f18-102">Slider Styles and Templates</span></span>
<span data-ttu-id="a0f18-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="a0f18-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="a0f18-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="a0f18-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a0f18-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a0f18-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="a0f18-106">Composants Slider</span><span class="sxs-lookup"><span data-stu-id="a0f18-106">Slider Parts</span></span>  
 <span data-ttu-id="a0f18-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="a0f18-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="a0f18-108">Élément</span><span class="sxs-lookup"><span data-stu-id="a0f18-108">Part</span></span>|<span data-ttu-id="a0f18-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="a0f18-109">Type</span></span>|<span data-ttu-id="a0f18-110">Description</span><span class="sxs-lookup"><span data-stu-id="a0f18-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a0f18-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="a0f18-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="a0f18-112">Conteneur de l’élément qui indique la position du <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="a0f18-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="a0f18-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="a0f18-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="a0f18-114">Élément qui affiche une plage de sélection le long du <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="a0f18-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="a0f18-115">La plage de sélection est visible uniquement si la propriété <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="a0f18-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="a0f18-116">États du curseur</span><span class="sxs-lookup"><span data-stu-id="a0f18-116">Slider States</span></span>  
 <span data-ttu-id="a0f18-117">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="a0f18-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="a0f18-118">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="a0f18-118">VisualState Name</span></span>|<span data-ttu-id="a0f18-119">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a0f18-119">VisualStateGroup Name</span></span>|<span data-ttu-id="a0f18-120">Description</span><span class="sxs-lookup"><span data-stu-id="a0f18-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="a0f18-121">Normale</span><span class="sxs-lookup"><span data-stu-id="a0f18-121">Normal</span></span>|<span data-ttu-id="a0f18-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a0f18-122">CommonStates</span></span>|<span data-ttu-id="a0f18-123">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="a0f18-123">The default state.</span></span>|  
|<span data-ttu-id="a0f18-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="a0f18-124">MouseOver</span></span>|<span data-ttu-id="a0f18-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a0f18-125">CommonStates</span></span>|<span data-ttu-id="a0f18-126">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a0f18-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="a0f18-127">Disabled</span><span class="sxs-lookup"><span data-stu-id="a0f18-127">Disabled</span></span>|<span data-ttu-id="a0f18-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a0f18-128">CommonStates</span></span>|<span data-ttu-id="a0f18-129">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="a0f18-129">The control is disabled.</span></span>|  
|<span data-ttu-id="a0f18-130">Avec focus</span><span class="sxs-lookup"><span data-stu-id="a0f18-130">Focused</span></span>|<span data-ttu-id="a0f18-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="a0f18-131">FocusStates</span></span>|<span data-ttu-id="a0f18-132">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="a0f18-132">The control has focus.</span></span>|  
|<span data-ttu-id="a0f18-133">Sans focus</span><span class="sxs-lookup"><span data-stu-id="a0f18-133">Unfocused</span></span>|<span data-ttu-id="a0f18-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="a0f18-134">FocusStates</span></span>|<span data-ttu-id="a0f18-135">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="a0f18-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="a0f18-136">Valide</span><span class="sxs-lookup"><span data-stu-id="a0f18-136">Valid</span></span>|<span data-ttu-id="a0f18-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a0f18-137">ValidationStates</span></span>|<span data-ttu-id="a0f18-138">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="a0f18-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a0f18-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a0f18-139">InvalidFocused</span></span>|<span data-ttu-id="a0f18-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a0f18-140">ValidationStates</span></span>|<span data-ttu-id="a0f18-141">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="a0f18-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a0f18-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a0f18-142">InvalidUnfocused</span></span>|<span data-ttu-id="a0f18-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a0f18-143">ValidationStates</span></span>|<span data-ttu-id="a0f18-144">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="a0f18-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="a0f18-145">Exemple de ControlTemplate Slider</span><span class="sxs-lookup"><span data-stu-id="a0f18-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="a0f18-146">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="a0f18-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="a0f18-147">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="a0f18-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a0f18-148">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="a0f18-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f18-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0f18-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="a0f18-150">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="a0f18-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="a0f18-151">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="a0f18-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="a0f18-152">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="a0f18-152">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="a0f18-153">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a0f18-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
