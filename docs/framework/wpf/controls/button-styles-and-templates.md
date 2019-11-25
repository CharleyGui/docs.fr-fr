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
ms.openlocfilehash: ef9f85848ebdda9dc4ae15d0f54847eacd46e24d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283580"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="04afc-102">Styles et modèles Button</span><span class="sxs-lookup"><span data-stu-id="04afc-102">Button Styles and Templates</span></span>
<span data-ttu-id="04afc-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="04afc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="04afc-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="04afc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="04afc-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="04afc-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="04afc-106">Composants de bouton</span><span class="sxs-lookup"><span data-stu-id="04afc-106">Button Parts</span></span>  
 <span data-ttu-id="04afc-107">Le contrôle <xref:System.Windows.Controls.Button> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="04afc-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="04afc-108">États du bouton</span><span class="sxs-lookup"><span data-stu-id="04afc-108">Button States</span></span>  
 <span data-ttu-id="04afc-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="04afc-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="04afc-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="04afc-110">VisualState Name</span></span>|<span data-ttu-id="04afc-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="04afc-111">VisualStateGroup Name</span></span>|<span data-ttu-id="04afc-112">Description</span><span class="sxs-lookup"><span data-stu-id="04afc-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="04afc-113">Normale</span><span class="sxs-lookup"><span data-stu-id="04afc-113">Normal</span></span>|<span data-ttu-id="04afc-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="04afc-114">CommonStates</span></span>|<span data-ttu-id="04afc-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="04afc-115">The default state.</span></span>|  
|<span data-ttu-id="04afc-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="04afc-116">MouseOver</span></span>|<span data-ttu-id="04afc-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="04afc-117">CommonStates</span></span>|<span data-ttu-id="04afc-118">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="04afc-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="04afc-119">Appuyé</span><span class="sxs-lookup"><span data-stu-id="04afc-119">Pressed</span></span>|<span data-ttu-id="04afc-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="04afc-120">CommonStates</span></span>|<span data-ttu-id="04afc-121">Le contrôle est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="04afc-121">The control is pressed.</span></span>|  
|<span data-ttu-id="04afc-122">Désactivé</span><span class="sxs-lookup"><span data-stu-id="04afc-122">Disabled</span></span>|<span data-ttu-id="04afc-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="04afc-123">CommonStates</span></span>|<span data-ttu-id="04afc-124">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="04afc-124">The control is disabled.</span></span>|  
|<span data-ttu-id="04afc-125">Avec focus</span><span class="sxs-lookup"><span data-stu-id="04afc-125">Focused</span></span>|<span data-ttu-id="04afc-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="04afc-126">FocusStates</span></span>|<span data-ttu-id="04afc-127">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="04afc-127">The control has focus.</span></span>|  
|<span data-ttu-id="04afc-128">Sans focus</span><span class="sxs-lookup"><span data-stu-id="04afc-128">Unfocused</span></span>|<span data-ttu-id="04afc-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="04afc-129">FocusStates</span></span>|<span data-ttu-id="04afc-130">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="04afc-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="04afc-131">Valide</span><span class="sxs-lookup"><span data-stu-id="04afc-131">Valid</span></span>|<span data-ttu-id="04afc-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="04afc-132">ValidationStates</span></span>|<span data-ttu-id="04afc-133">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="04afc-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="04afc-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="04afc-134">InvalidFocused</span></span>|<span data-ttu-id="04afc-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="04afc-135">ValidationStates</span></span>|<span data-ttu-id="04afc-136">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` et le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="04afc-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="04afc-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="04afc-137">InvalidUnfocused</span></span>|<span data-ttu-id="04afc-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="04afc-138">ValidationStates</span></span>|<span data-ttu-id="04afc-139">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="04afc-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="04afc-140">Button ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="04afc-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="04afc-141">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="04afc-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="04afc-142">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="04afc-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="04afc-143">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="04afc-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04afc-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04afc-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="04afc-145">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="04afc-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="04afc-146">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="04afc-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="04afc-147">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="04afc-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="04afc-148">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="04afc-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
