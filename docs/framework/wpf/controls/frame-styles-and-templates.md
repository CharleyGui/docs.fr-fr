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
ms.openlocfilehash: de853198c97c99319bea4a816c9a6eca5dc5d917
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283733"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="3a91f-102">Styles et modèles Frame</span><span class="sxs-lookup"><span data-stu-id="3a91f-102">Frame Styles and Templates</span></span>
<span data-ttu-id="3a91f-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="3a91f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="3a91f-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="3a91f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3a91f-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="3a91f-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="3a91f-106">Parties de frame</span><span class="sxs-lookup"><span data-stu-id="3a91f-106">Frame Parts</span></span>  
 <span data-ttu-id="3a91f-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="3a91f-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="3a91f-108">Élément</span><span class="sxs-lookup"><span data-stu-id="3a91f-108">Part</span></span>|<span data-ttu-id="3a91f-109">Type</span><span class="sxs-lookup"><span data-stu-id="3a91f-109">Type</span></span>|<span data-ttu-id="3a91f-110">Description</span><span class="sxs-lookup"><span data-stu-id="3a91f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3a91f-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="3a91f-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="3a91f-112">Zone de contenu.</span><span class="sxs-lookup"><span data-stu-id="3a91f-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="3a91f-113">États des frames</span><span class="sxs-lookup"><span data-stu-id="3a91f-113">Frame States</span></span>  
 <span data-ttu-id="3a91f-114">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="3a91f-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="3a91f-115">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="3a91f-115">VisualState Name</span></span>|<span data-ttu-id="3a91f-116">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3a91f-116">VisualStateGroup Name</span></span>|<span data-ttu-id="3a91f-117">Description</span><span class="sxs-lookup"><span data-stu-id="3a91f-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3a91f-118">Valide</span><span class="sxs-lookup"><span data-stu-id="3a91f-118">Valid</span></span>|<span data-ttu-id="3a91f-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3a91f-119">ValidationStates</span></span>|<span data-ttu-id="3a91f-120">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="3a91f-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3a91f-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3a91f-121">InvalidFocused</span></span>|<span data-ttu-id="3a91f-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3a91f-122">ValidationStates</span></span>|<span data-ttu-id="3a91f-123">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="3a91f-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3a91f-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3a91f-124">InvalidUnfocused</span></span>|<span data-ttu-id="3a91f-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3a91f-125">ValidationStates</span></span>|<span data-ttu-id="3a91f-126">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="3a91f-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="3a91f-127">Frame ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="3a91f-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="3a91f-128">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="3a91f-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="3a91f-129">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="3a91f-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3a91f-130">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="3a91f-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a91f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a91f-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3a91f-132">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="3a91f-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3a91f-133">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="3a91f-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3a91f-134">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="3a91f-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3a91f-135">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="3a91f-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
