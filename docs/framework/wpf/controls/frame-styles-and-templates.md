---
title: Styles et modèles Frame
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: 89f4fc21637d20ca226507463093bc6bae2241fc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460315"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="c643c-102">Styles et modèles Frame</span><span class="sxs-lookup"><span data-stu-id="c643c-102">Frame Styles and Templates</span></span>
<span data-ttu-id="c643c-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="c643c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="c643c-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="c643c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c643c-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c643c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="c643c-106">Parties de frame</span><span class="sxs-lookup"><span data-stu-id="c643c-106">Frame Parts</span></span>  
 <span data-ttu-id="c643c-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="c643c-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="c643c-108">Élément</span><span class="sxs-lookup"><span data-stu-id="c643c-108">Part</span></span>|<span data-ttu-id="c643c-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="c643c-109">Type</span></span>|<span data-ttu-id="c643c-110">Description</span><span class="sxs-lookup"><span data-stu-id="c643c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c643c-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="c643c-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="c643c-112">Zone de contenu.</span><span class="sxs-lookup"><span data-stu-id="c643c-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="c643c-113">États des frames</span><span class="sxs-lookup"><span data-stu-id="c643c-113">Frame States</span></span>  
 <span data-ttu-id="c643c-114">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="c643c-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="c643c-115">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="c643c-115">VisualState Name</span></span>|<span data-ttu-id="c643c-116">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c643c-116">VisualStateGroup Name</span></span>|<span data-ttu-id="c643c-117">Description</span><span class="sxs-lookup"><span data-stu-id="c643c-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c643c-118">Valide</span><span class="sxs-lookup"><span data-stu-id="c643c-118">Valid</span></span>|<span data-ttu-id="c643c-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c643c-119">ValidationStates</span></span>|<span data-ttu-id="c643c-120">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="c643c-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c643c-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c643c-121">InvalidFocused</span></span>|<span data-ttu-id="c643c-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c643c-122">ValidationStates</span></span>|<span data-ttu-id="c643c-123">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="c643c-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c643c-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c643c-124">InvalidUnfocused</span></span>|<span data-ttu-id="c643c-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c643c-125">ValidationStates</span></span>|<span data-ttu-id="c643c-126">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="c643c-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="c643c-127">Frame ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="c643c-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="c643c-128">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="c643c-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="c643c-129">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="c643c-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c643c-130">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="c643c-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c643c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c643c-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c643c-132">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="c643c-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c643c-133">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="c643c-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c643c-134">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="c643c-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c643c-135">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c643c-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
