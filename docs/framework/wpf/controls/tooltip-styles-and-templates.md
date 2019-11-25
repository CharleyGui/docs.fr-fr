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
ms.openlocfilehash: c7a14034d665c124d01e8a4b43c5d42968241925
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283646"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="15b93-102">Styles et modèles ToolTip</span><span class="sxs-lookup"><span data-stu-id="15b93-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="15b93-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="15b93-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="15b93-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="15b93-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="15b93-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="15b93-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="15b93-106">Parties d’info-bulle</span><span class="sxs-lookup"><span data-stu-id="15b93-106">ToolTip Parts</span></span>  
 <span data-ttu-id="15b93-107">Le contrôle <xref:System.Windows.Controls.ToolTip> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="15b93-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="15b93-108">États de l’info-bulle</span><span class="sxs-lookup"><span data-stu-id="15b93-108">ToolTip States</span></span>  
 <span data-ttu-id="15b93-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="15b93-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="15b93-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="15b93-110">VisualState Name</span></span>|<span data-ttu-id="15b93-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="15b93-111">VisualStateGroup Name</span></span>|<span data-ttu-id="15b93-112">Description</span><span class="sxs-lookup"><span data-stu-id="15b93-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="15b93-113">Closed</span><span class="sxs-lookup"><span data-stu-id="15b93-113">Closed</span></span>|<span data-ttu-id="15b93-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="15b93-114">OpenStates</span></span>|<span data-ttu-id="15b93-115">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="15b93-115">The default state.</span></span>|  
|<span data-ttu-id="15b93-116">Ouvrir</span><span class="sxs-lookup"><span data-stu-id="15b93-116">Open</span></span>|<span data-ttu-id="15b93-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="15b93-117">OpenStates</span></span>|<span data-ttu-id="15b93-118">Le <xref:System.Windows.Controls.ToolTip> est visible.</span><span class="sxs-lookup"><span data-stu-id="15b93-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="15b93-119">Valide</span><span class="sxs-lookup"><span data-stu-id="15b93-119">Valid</span></span>|<span data-ttu-id="15b93-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15b93-120">ValidationStates</span></span>|<span data-ttu-id="15b93-121">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="15b93-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="15b93-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="15b93-122">InvalidFocused</span></span>|<span data-ttu-id="15b93-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15b93-123">ValidationStates</span></span>|<span data-ttu-id="15b93-124">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="15b93-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="15b93-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="15b93-125">InvalidUnfocused</span></span>|<span data-ttu-id="15b93-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15b93-126">ValidationStates</span></span>|<span data-ttu-id="15b93-127">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="15b93-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="15b93-128">Exemple de ControlTemplate d’info-bulle</span><span class="sxs-lookup"><span data-stu-id="15b93-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="15b93-129">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="15b93-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="15b93-130">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="15b93-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="15b93-131">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="15b93-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b93-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15b93-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="15b93-133">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="15b93-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="15b93-134">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="15b93-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="15b93-135">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="15b93-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="15b93-136">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="15b93-136">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
