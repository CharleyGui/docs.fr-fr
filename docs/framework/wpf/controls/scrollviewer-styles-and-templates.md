---
title: Styles et modèles ScrollViewer
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 70a2002ab114f2bbd6a4e550ae9006e214ee27a5
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458419"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="2d3ac-102">Styles et modèles ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="2d3ac-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="2d3ac-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="2d3ac-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2d3ac-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ac-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="2d3ac-106">Parties ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="2d3ac-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="2d3ac-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="2d3ac-108">Élément</span><span class="sxs-lookup"><span data-stu-id="2d3ac-108">Part</span></span>|<span data-ttu-id="2d3ac-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="2d3ac-109">Type</span></span>|<span data-ttu-id="2d3ac-110">Description</span><span class="sxs-lookup"><span data-stu-id="2d3ac-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d3ac-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="2d3ac-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="2d3ac-112">Espace réservé pour le contenu du <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="2d3ac-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="2d3ac-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="2d3ac-114"><xref:System.Windows.Controls.Primitives.ScrollBar> utilisé pour faire défiler le contenu horizontalement.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="2d3ac-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="2d3ac-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="2d3ac-116"><xref:System.Windows.Controls.Primitives.ScrollBar> utilisé pour faire défiler le contenu verticalement.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="2d3ac-117">États ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="2d3ac-117">ScrollViewer States</span></span>  
 <span data-ttu-id="2d3ac-118">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="2d3ac-119">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="2d3ac-119">VisualState Name</span></span>|<span data-ttu-id="2d3ac-120">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2d3ac-120">VisualStateGroup Name</span></span>|<span data-ttu-id="2d3ac-121">Description</span><span class="sxs-lookup"><span data-stu-id="2d3ac-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d3ac-122">Valide</span><span class="sxs-lookup"><span data-stu-id="2d3ac-122">Valid</span></span>|<span data-ttu-id="2d3ac-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3ac-123">ValidationStates</span></span>|<span data-ttu-id="2d3ac-124">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2d3ac-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2d3ac-125">InvalidFocused</span></span>|<span data-ttu-id="2d3ac-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3ac-126">ValidationStates</span></span>|<span data-ttu-id="2d3ac-127">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2d3ac-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2d3ac-128">InvalidUnfocused</span></span>|<span data-ttu-id="2d3ac-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3ac-129">ValidationStates</span></span>|<span data-ttu-id="2d3ac-130">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="2d3ac-131">ScrollViewer ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="2d3ac-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="2d3ac-132">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="2d3ac-133">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2d3ac-134">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="2d3ac-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3ac-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d3ac-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2d3ac-136">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="2d3ac-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2d3ac-137">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="2d3ac-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2d3ac-138">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="2d3ac-138">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2d3ac-139">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="2d3ac-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
