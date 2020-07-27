---
title: Styles et modèles TextBox
description: En savoir plus sur les styles et les modèles pour le contrôle Windows Presentation Foundation TextBox. Modifiez le ControlTemplate pour attribuer une apparence unique au contrôle.
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164727"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="d63a6-104">Styles et modèles TextBox</span><span class="sxs-lookup"><span data-stu-id="d63a6-104">TextBox Styles and Templates</span></span>
<span data-ttu-id="d63a6-105">Cette rubrique décrit les styles et les modèles pour le <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="d63a6-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="d63a6-106">Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour que le contrôle donne une apparence unique.</span><span class="sxs-lookup"><span data-stu-id="d63a6-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d63a6-107">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="d63a6-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="d63a6-108">Parties de zone de texte</span><span class="sxs-lookup"><span data-stu-id="d63a6-108">TextBox Parts</span></span>  
 <span data-ttu-id="d63a6-109">Le tableau suivant répertorie les parties nommées du <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="d63a6-109">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="d63a6-110">Élément</span><span class="sxs-lookup"><span data-stu-id="d63a6-110">Part</span></span>|<span data-ttu-id="d63a6-111">Type</span><span class="sxs-lookup"><span data-stu-id="d63a6-111">Type</span></span>|<span data-ttu-id="d63a6-112">Description</span><span class="sxs-lookup"><span data-stu-id="d63a6-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d63a6-113">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="d63a6-113">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d63a6-114">Élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="d63a6-114">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="d63a6-115">Le texte du <xref:System.Windows.Controls.TextBox> est affiché dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="d63a6-115">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="d63a6-116">États de la zone de texte</span><span class="sxs-lookup"><span data-stu-id="d63a6-116">TextBox States</span></span>  
 <span data-ttu-id="d63a6-117">Le tableau suivant répertorie les États visuels du <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="d63a6-117">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="d63a6-118">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="d63a6-118">VisualState Name</span></span>|<span data-ttu-id="d63a6-119">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d63a6-119">VisualStateGroup Name</span></span>|<span data-ttu-id="d63a6-120">Description</span><span class="sxs-lookup"><span data-stu-id="d63a6-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="d63a6-121">Normal</span><span class="sxs-lookup"><span data-stu-id="d63a6-121">Normal</span></span>|<span data-ttu-id="d63a6-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-122">CommonStates</span></span>|<span data-ttu-id="d63a6-123">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="d63a6-123">The default state.</span></span>|  
|<span data-ttu-id="d63a6-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="d63a6-124">MouseOver</span></span>|<span data-ttu-id="d63a6-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-125">CommonStates</span></span>|<span data-ttu-id="d63a6-126">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d63a6-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="d63a6-127">Désactivé</span><span class="sxs-lookup"><span data-stu-id="d63a6-127">Disabled</span></span>|<span data-ttu-id="d63a6-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-128">CommonStates</span></span>|<span data-ttu-id="d63a6-129">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="d63a6-129">The control is disabled.</span></span>|  
|<span data-ttu-id="d63a6-130">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="d63a6-130">ReadOnly</span></span>|<span data-ttu-id="d63a6-131">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-131">CommonStates</span></span>|<span data-ttu-id="d63a6-132">L’utilisateur ne peut pas modifier le texte dans <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="d63a6-132">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="d63a6-133">Avec focus</span><span class="sxs-lookup"><span data-stu-id="d63a6-133">Focused</span></span>|<span data-ttu-id="d63a6-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-134">FocusStates</span></span>|<span data-ttu-id="d63a6-135">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="d63a6-135">The control has focus.</span></span>|  
|<span data-ttu-id="d63a6-136">Sans focus</span><span class="sxs-lookup"><span data-stu-id="d63a6-136">Unfocused</span></span>|<span data-ttu-id="d63a6-137">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-137">FocusStates</span></span>|<span data-ttu-id="d63a6-138">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="d63a6-138">The control does not have focus.</span></span>|  
|<span data-ttu-id="d63a6-139">Valide</span><span class="sxs-lookup"><span data-stu-id="d63a6-139">Valid</span></span>|<span data-ttu-id="d63a6-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-140">ValidationStates</span></span>|<span data-ttu-id="d63a6-141">Le contrôle utilise la <xref:System.Windows.Controls.Validation> classe et la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false` .</span><span class="sxs-lookup"><span data-stu-id="d63a6-141">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d63a6-142">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d63a6-142">InvalidFocused</span></span>|<span data-ttu-id="d63a6-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-143">ValidationStates</span></span>|<span data-ttu-id="d63a6-144">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe a `true` le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="d63a6-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d63a6-145">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d63a6-145">InvalidUnfocused</span></span>|<span data-ttu-id="d63a6-146">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d63a6-146">ValidationStates</span></span>|<span data-ttu-id="d63a6-147">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="d63a6-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="d63a6-148">TextBox, exemple de ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d63a6-148">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="d63a6-149">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="d63a6-149">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="d63a6-150">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="d63a6-150">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d63a6-151">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="d63a6-151">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d63a6-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d63a6-152">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d63a6-153">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="d63a6-153">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d63a6-154">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="d63a6-154">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d63a6-155">Application d'un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="d63a6-155">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="d63a6-156">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="d63a6-156">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
