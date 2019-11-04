---
title: Styles et modèles ToolTip
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: 626d0b4d49d653f820d1506f0aa09f06d26352c2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458637"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="60c01-102">Styles et modèles ToolTip</span><span class="sxs-lookup"><span data-stu-id="60c01-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="60c01-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="60c01-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="60c01-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="60c01-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="60c01-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="60c01-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="60c01-106">Parties d’info-bulle</span><span class="sxs-lookup"><span data-stu-id="60c01-106">ToolTip Parts</span></span>  
 <span data-ttu-id="60c01-107">Le contrôle <xref:System.Windows.Controls.ToolTip> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="60c01-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="60c01-108">États de l’info-bulle</span><span class="sxs-lookup"><span data-stu-id="60c01-108">ToolTip States</span></span>  
 <span data-ttu-id="60c01-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="60c01-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="60c01-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="60c01-110">VisualState Name</span></span>|<span data-ttu-id="60c01-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="60c01-111">VisualStateGroup Name</span></span>|<span data-ttu-id="60c01-112">Description</span><span class="sxs-lookup"><span data-stu-id="60c01-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="60c01-113">Closed</span><span class="sxs-lookup"><span data-stu-id="60c01-113">Closed</span></span>|<span data-ttu-id="60c01-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="60c01-114">OpenStates</span></span>|<span data-ttu-id="60c01-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="60c01-115">The default state.</span></span>|  
|<span data-ttu-id="60c01-116">Ouvrir</span><span class="sxs-lookup"><span data-stu-id="60c01-116">Open</span></span>|<span data-ttu-id="60c01-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="60c01-117">OpenStates</span></span>|<span data-ttu-id="60c01-118">Le <xref:System.Windows.Controls.ToolTip> est visible.</span><span class="sxs-lookup"><span data-stu-id="60c01-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="60c01-119">Valide</span><span class="sxs-lookup"><span data-stu-id="60c01-119">Valid</span></span>|<span data-ttu-id="60c01-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="60c01-120">ValidationStates</span></span>|<span data-ttu-id="60c01-121">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="60c01-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="60c01-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="60c01-122">InvalidFocused</span></span>|<span data-ttu-id="60c01-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="60c01-123">ValidationStates</span></span>|<span data-ttu-id="60c01-124">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="60c01-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="60c01-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="60c01-125">InvalidUnfocused</span></span>|<span data-ttu-id="60c01-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="60c01-126">ValidationStates</span></span>|<span data-ttu-id="60c01-127">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="60c01-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="60c01-128">Exemple de ControlTemplate d’info-bulle</span><span class="sxs-lookup"><span data-stu-id="60c01-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="60c01-129">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="60c01-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="60c01-130">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="60c01-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="60c01-131">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="60c01-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c01-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60c01-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="60c01-133">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="60c01-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="60c01-134">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="60c01-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="60c01-135">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="60c01-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="60c01-136">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="60c01-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
