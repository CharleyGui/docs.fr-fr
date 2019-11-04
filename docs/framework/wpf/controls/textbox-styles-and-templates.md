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
ms.openlocfilehash: 7c4680a3ea9352e94d628e786fc8e4fd71018d00
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458251"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="69a56-102">Styles et modèles TextBox</span><span class="sxs-lookup"><span data-stu-id="69a56-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="69a56-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="69a56-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="69a56-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="69a56-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="69a56-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="69a56-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="69a56-106">Parties de zone de texte</span><span class="sxs-lookup"><span data-stu-id="69a56-106">TextBox Parts</span></span>  
 <span data-ttu-id="69a56-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="69a56-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="69a56-108">Élément</span><span class="sxs-lookup"><span data-stu-id="69a56-108">Part</span></span>|<span data-ttu-id="69a56-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="69a56-109">Type</span></span>|<span data-ttu-id="69a56-110">Description</span><span class="sxs-lookup"><span data-stu-id="69a56-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="69a56-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="69a56-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="69a56-112">Élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="69a56-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="69a56-113">Le texte de la <xref:System.Windows.Controls.TextBox> s’affiche dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="69a56-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="69a56-114">États de la zone de texte</span><span class="sxs-lookup"><span data-stu-id="69a56-114">TextBox States</span></span>  
 <span data-ttu-id="69a56-115">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="69a56-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="69a56-116">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="69a56-116">VisualState Name</span></span>|<span data-ttu-id="69a56-117">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="69a56-117">VisualStateGroup Name</span></span>|<span data-ttu-id="69a56-118">Description</span><span class="sxs-lookup"><span data-stu-id="69a56-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="69a56-119">Normale</span><span class="sxs-lookup"><span data-stu-id="69a56-119">Normal</span></span>|<span data-ttu-id="69a56-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="69a56-120">CommonStates</span></span>|<span data-ttu-id="69a56-121">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="69a56-121">The default state.</span></span>|  
|<span data-ttu-id="69a56-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="69a56-122">MouseOver</span></span>|<span data-ttu-id="69a56-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="69a56-123">CommonStates</span></span>|<span data-ttu-id="69a56-124">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="69a56-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="69a56-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="69a56-125">Disabled</span></span>|<span data-ttu-id="69a56-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="69a56-126">CommonStates</span></span>|<span data-ttu-id="69a56-127">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="69a56-127">The control is disabled.</span></span>|  
|<span data-ttu-id="69a56-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="69a56-128">ReadOnly</span></span>|<span data-ttu-id="69a56-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="69a56-129">CommonStates</span></span>|<span data-ttu-id="69a56-130">L’utilisateur ne peut pas modifier le texte dans la <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="69a56-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="69a56-131">Avec focus</span><span class="sxs-lookup"><span data-stu-id="69a56-131">Focused</span></span>|<span data-ttu-id="69a56-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="69a56-132">FocusStates</span></span>|<span data-ttu-id="69a56-133">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="69a56-133">The control has focus.</span></span>|  
|<span data-ttu-id="69a56-134">Sans focus</span><span class="sxs-lookup"><span data-stu-id="69a56-134">Unfocused</span></span>|<span data-ttu-id="69a56-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="69a56-135">FocusStates</span></span>|<span data-ttu-id="69a56-136">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="69a56-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="69a56-137">Valide</span><span class="sxs-lookup"><span data-stu-id="69a56-137">Valid</span></span>|<span data-ttu-id="69a56-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="69a56-138">ValidationStates</span></span>|<span data-ttu-id="69a56-139">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="69a56-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="69a56-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="69a56-140">InvalidFocused</span></span>|<span data-ttu-id="69a56-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="69a56-141">ValidationStates</span></span>|<span data-ttu-id="69a56-142">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="69a56-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="69a56-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="69a56-143">InvalidUnfocused</span></span>|<span data-ttu-id="69a56-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="69a56-144">ValidationStates</span></span>|<span data-ttu-id="69a56-145">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="69a56-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="69a56-146">TextBox, exemple de ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="69a56-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="69a56-147">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="69a56-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="69a56-148">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="69a56-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="69a56-149">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="69a56-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a56-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69a56-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="69a56-151">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="69a56-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="69a56-152">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="69a56-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="69a56-153">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="69a56-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="69a56-154">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="69a56-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
