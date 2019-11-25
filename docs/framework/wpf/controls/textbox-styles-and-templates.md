---
title: Styles et modèles TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 41e390c261836909240cc146a48729d48c4a410e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283700"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="6ad11-102">Styles et modèles TextBox</span><span class="sxs-lookup"><span data-stu-id="6ad11-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="6ad11-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6ad11-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="6ad11-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="6ad11-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6ad11-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="6ad11-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="6ad11-106">Parties de zone de texte</span><span class="sxs-lookup"><span data-stu-id="6ad11-106">TextBox Parts</span></span>  
 <span data-ttu-id="6ad11-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6ad11-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="6ad11-108">Élément</span><span class="sxs-lookup"><span data-stu-id="6ad11-108">Part</span></span>|<span data-ttu-id="6ad11-109">Type</span><span class="sxs-lookup"><span data-stu-id="6ad11-109">Type</span></span>|<span data-ttu-id="6ad11-110">Description</span><span class="sxs-lookup"><span data-stu-id="6ad11-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6ad11-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="6ad11-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="6ad11-112">Élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="6ad11-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="6ad11-113">Le texte de la <xref:System.Windows.Controls.TextBox> s’affiche dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="6ad11-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="6ad11-114">États de la zone de texte</span><span class="sxs-lookup"><span data-stu-id="6ad11-114">TextBox States</span></span>  
 <span data-ttu-id="6ad11-115">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6ad11-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="6ad11-116">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="6ad11-116">VisualState Name</span></span>|<span data-ttu-id="6ad11-117">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6ad11-117">VisualStateGroup Name</span></span>|<span data-ttu-id="6ad11-118">Description</span><span class="sxs-lookup"><span data-stu-id="6ad11-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="6ad11-119">Normale</span><span class="sxs-lookup"><span data-stu-id="6ad11-119">Normal</span></span>|<span data-ttu-id="6ad11-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-120">CommonStates</span></span>|<span data-ttu-id="6ad11-121">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="6ad11-121">The default state.</span></span>|  
|<span data-ttu-id="6ad11-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="6ad11-122">MouseOver</span></span>|<span data-ttu-id="6ad11-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-123">CommonStates</span></span>|<span data-ttu-id="6ad11-124">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="6ad11-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="6ad11-125">Désactivé</span><span class="sxs-lookup"><span data-stu-id="6ad11-125">Disabled</span></span>|<span data-ttu-id="6ad11-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-126">CommonStates</span></span>|<span data-ttu-id="6ad11-127">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="6ad11-127">The control is disabled.</span></span>|  
|<span data-ttu-id="6ad11-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6ad11-128">ReadOnly</span></span>|<span data-ttu-id="6ad11-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-129">CommonStates</span></span>|<span data-ttu-id="6ad11-130">L’utilisateur ne peut pas modifier le texte dans la <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6ad11-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="6ad11-131">Avec focus</span><span class="sxs-lookup"><span data-stu-id="6ad11-131">Focused</span></span>|<span data-ttu-id="6ad11-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-132">FocusStates</span></span>|<span data-ttu-id="6ad11-133">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="6ad11-133">The control has focus.</span></span>|  
|<span data-ttu-id="6ad11-134">Sans focus</span><span class="sxs-lookup"><span data-stu-id="6ad11-134">Unfocused</span></span>|<span data-ttu-id="6ad11-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-135">FocusStates</span></span>|<span data-ttu-id="6ad11-136">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="6ad11-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="6ad11-137">Valide</span><span class="sxs-lookup"><span data-stu-id="6ad11-137">Valid</span></span>|<span data-ttu-id="6ad11-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-138">ValidationStates</span></span>|<span data-ttu-id="6ad11-139">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="6ad11-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6ad11-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6ad11-140">InvalidFocused</span></span>|<span data-ttu-id="6ad11-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-141">ValidationStates</span></span>|<span data-ttu-id="6ad11-142">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="6ad11-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6ad11-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6ad11-143">InvalidUnfocused</span></span>|<span data-ttu-id="6ad11-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad11-144">ValidationStates</span></span>|<span data-ttu-id="6ad11-145">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="6ad11-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="6ad11-146">TextBox, exemple de ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6ad11-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="6ad11-147">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6ad11-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="6ad11-148">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="6ad11-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6ad11-149">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="6ad11-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad11-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ad11-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6ad11-151">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="6ad11-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6ad11-152">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="6ad11-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6ad11-153">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="6ad11-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6ad11-154">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="6ad11-154">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
