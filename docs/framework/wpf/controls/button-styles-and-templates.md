---
title: Styles et modèles Button
description: En savoir plus sur les styles et les modèles pour le contrôle bouton Windows Presentation Foundation. Modifiez le ControlTemplate pour attribuer une apparence unique au contrôle.
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 11509adeef397f26eb040e6e98d0edb333b2515f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166269"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="ce3c3-104">Styles et modèles Button</span><span class="sxs-lookup"><span data-stu-id="ce3c3-104">Button Styles and Templates</span></span>
<span data-ttu-id="ce3c3-105">Cette rubrique décrit les styles et les modèles pour le <xref:System.Windows.Controls.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="ce3c3-106">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour que le contrôle donne une apparence unique.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ce3c3-107">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="ce3c3-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="ce3c3-108">Composants de bouton</span><span class="sxs-lookup"><span data-stu-id="ce3c3-108">Button Parts</span></span>  
 <span data-ttu-id="ce3c3-109">Le <xref:System.Windows.Controls.Button> contrôle n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-109">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="ce3c3-110">États du bouton</span><span class="sxs-lookup"><span data-stu-id="ce3c3-110">Button States</span></span>  
 <span data-ttu-id="ce3c3-111">Le tableau suivant répertorie les États visuels du <xref:System.Windows.Controls.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-111">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="ce3c3-112">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="ce3c3-112">VisualState Name</span></span>|<span data-ttu-id="ce3c3-113">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ce3c3-113">VisualStateGroup Name</span></span>|<span data-ttu-id="ce3c3-114">Description</span><span class="sxs-lookup"><span data-stu-id="ce3c3-114">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ce3c3-115">Normal</span><span class="sxs-lookup"><span data-stu-id="ce3c3-115">Normal</span></span>|<span data-ttu-id="ce3c3-116">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-116">CommonStates</span></span>|<span data-ttu-id="ce3c3-117">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-117">The default state.</span></span>|  
|<span data-ttu-id="ce3c3-118">MouseOver</span><span class="sxs-lookup"><span data-stu-id="ce3c3-118">MouseOver</span></span>|<span data-ttu-id="ce3c3-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-119">CommonStates</span></span>|<span data-ttu-id="ce3c3-120">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-120">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="ce3c3-121">Appuyé</span><span class="sxs-lookup"><span data-stu-id="ce3c3-121">Pressed</span></span>|<span data-ttu-id="ce3c3-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-122">CommonStates</span></span>|<span data-ttu-id="ce3c3-123">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-123">The control is pressed.</span></span>|  
|<span data-ttu-id="ce3c3-124">Désactivé</span><span class="sxs-lookup"><span data-stu-id="ce3c3-124">Disabled</span></span>|<span data-ttu-id="ce3c3-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-125">CommonStates</span></span>|<span data-ttu-id="ce3c3-126">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-126">The control is disabled.</span></span>|  
|<span data-ttu-id="ce3c3-127">Avec focus</span><span class="sxs-lookup"><span data-stu-id="ce3c3-127">Focused</span></span>|<span data-ttu-id="ce3c3-128">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-128">FocusStates</span></span>|<span data-ttu-id="ce3c3-129">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-129">The control has focus.</span></span>|  
|<span data-ttu-id="ce3c3-130">Sans focus</span><span class="sxs-lookup"><span data-stu-id="ce3c3-130">Unfocused</span></span>|<span data-ttu-id="ce3c3-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-131">FocusStates</span></span>|<span data-ttu-id="ce3c3-132">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-132">The control does not have focus.</span></span>|  
|<span data-ttu-id="ce3c3-133">Valide</span><span class="sxs-lookup"><span data-stu-id="ce3c3-133">Valid</span></span>|<span data-ttu-id="ce3c3-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-134">ValidationStates</span></span>|<span data-ttu-id="ce3c3-135">Le contrôle utilise la <xref:System.Windows.Controls.Validation> classe et la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false` .</span><span class="sxs-lookup"><span data-stu-id="ce3c3-135">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ce3c3-136">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ce3c3-136">InvalidFocused</span></span>|<span data-ttu-id="ce3c3-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-137">ValidationStates</span></span>|<span data-ttu-id="ce3c3-138">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-138">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="ce3c3-139">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ce3c3-139">InvalidUnfocused</span></span>|<span data-ttu-id="ce3c3-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce3c3-140">ValidationStates</span></span>|<span data-ttu-id="ce3c3-141">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="ce3c3-142">Button ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="ce3c3-142">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="ce3c3-143">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-143">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="ce3c3-144">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="ce3c3-144">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ce3c3-145">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="ce3c3-145">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3c3-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce3c3-146">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ce3c3-147">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="ce3c3-147">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ce3c3-148">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="ce3c3-148">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ce3c3-149">Application d'un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="ce3c3-149">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ce3c3-150">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="ce3c3-150">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
