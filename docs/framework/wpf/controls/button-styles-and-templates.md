---
title: Styles et modèles Button
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 64764d43191d30c191c5d6519982b16cfc86d26e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460958"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="88385-102">Styles et modèles Button</span><span class="sxs-lookup"><span data-stu-id="88385-102">Button Styles and Templates</span></span>
<span data-ttu-id="88385-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="88385-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="88385-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="88385-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="88385-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="88385-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="88385-106">Composants de bouton</span><span class="sxs-lookup"><span data-stu-id="88385-106">Button Parts</span></span>  
 <span data-ttu-id="88385-107">Le contrôle <xref:System.Windows.Controls.Button> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="88385-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="88385-108">États du bouton</span><span class="sxs-lookup"><span data-stu-id="88385-108">Button States</span></span>  
 <span data-ttu-id="88385-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="88385-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="88385-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="88385-110">VisualState Name</span></span>|<span data-ttu-id="88385-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="88385-111">VisualStateGroup Name</span></span>|<span data-ttu-id="88385-112">Description</span><span class="sxs-lookup"><span data-stu-id="88385-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="88385-113">Normale</span><span class="sxs-lookup"><span data-stu-id="88385-113">Normal</span></span>|<span data-ttu-id="88385-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="88385-114">CommonStates</span></span>|<span data-ttu-id="88385-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="88385-115">The default state.</span></span>|  
|<span data-ttu-id="88385-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="88385-116">MouseOver</span></span>|<span data-ttu-id="88385-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="88385-117">CommonStates</span></span>|<span data-ttu-id="88385-118">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="88385-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="88385-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="88385-119">Pressed</span></span>|<span data-ttu-id="88385-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="88385-120">CommonStates</span></span>|<span data-ttu-id="88385-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="88385-121">The control is pressed.</span></span>|  
|<span data-ttu-id="88385-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="88385-122">Disabled</span></span>|<span data-ttu-id="88385-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="88385-123">CommonStates</span></span>|<span data-ttu-id="88385-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="88385-124">The control is disabled.</span></span>|  
|<span data-ttu-id="88385-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="88385-125">Focused</span></span>|<span data-ttu-id="88385-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="88385-126">FocusStates</span></span>|<span data-ttu-id="88385-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="88385-127">The control has focus.</span></span>|  
|<span data-ttu-id="88385-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="88385-128">Unfocused</span></span>|<span data-ttu-id="88385-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="88385-129">FocusStates</span></span>|<span data-ttu-id="88385-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="88385-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="88385-131">Valide</span><span class="sxs-lookup"><span data-stu-id="88385-131">Valid</span></span>|<span data-ttu-id="88385-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="88385-132">ValidationStates</span></span>|<span data-ttu-id="88385-133">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="88385-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="88385-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="88385-134">InvalidFocused</span></span>|<span data-ttu-id="88385-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="88385-135">ValidationStates</span></span>|<span data-ttu-id="88385-136">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` et le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="88385-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="88385-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="88385-137">InvalidUnfocused</span></span>|<span data-ttu-id="88385-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="88385-138">ValidationStates</span></span>|<span data-ttu-id="88385-139">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="88385-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="88385-140">Button ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="88385-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="88385-141">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="88385-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="88385-142">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="88385-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="88385-143">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="88385-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88385-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88385-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="88385-145">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="88385-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="88385-146">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="88385-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="88385-147">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="88385-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="88385-148">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="88385-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
