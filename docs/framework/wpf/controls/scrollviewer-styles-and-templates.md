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
ms.openlocfilehash: b54dcacf55a750d7c1253db20147d18de47d027e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283394"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="85b36-102">Styles et modèles ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="85b36-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="85b36-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="85b36-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="85b36-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="85b36-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="85b36-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="85b36-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="85b36-106">Parties ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="85b36-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="85b36-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="85b36-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="85b36-108">Élément</span><span class="sxs-lookup"><span data-stu-id="85b36-108">Part</span></span>|<span data-ttu-id="85b36-109">Type</span><span class="sxs-lookup"><span data-stu-id="85b36-109">Type</span></span>|<span data-ttu-id="85b36-110">Description</span><span class="sxs-lookup"><span data-stu-id="85b36-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="85b36-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="85b36-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="85b36-112">Espace réservé pour le contenu du <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="85b36-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="85b36-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="85b36-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="85b36-114"><xref:System.Windows.Controls.Primitives.ScrollBar> utilisé pour faire défiler le contenu horizontalement.</span><span class="sxs-lookup"><span data-stu-id="85b36-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="85b36-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="85b36-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="85b36-116"><xref:System.Windows.Controls.Primitives.ScrollBar> utilisé pour faire défiler le contenu verticalement.</span><span class="sxs-lookup"><span data-stu-id="85b36-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="85b36-117">États ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="85b36-117">ScrollViewer States</span></span>  
 <span data-ttu-id="85b36-118">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="85b36-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="85b36-119">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="85b36-119">VisualState Name</span></span>|<span data-ttu-id="85b36-120">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="85b36-120">VisualStateGroup Name</span></span>|<span data-ttu-id="85b36-121">Description</span><span class="sxs-lookup"><span data-stu-id="85b36-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="85b36-122">Valide</span><span class="sxs-lookup"><span data-stu-id="85b36-122">Valid</span></span>|<span data-ttu-id="85b36-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="85b36-123">ValidationStates</span></span>|<span data-ttu-id="85b36-124">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="85b36-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="85b36-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="85b36-125">InvalidFocused</span></span>|<span data-ttu-id="85b36-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="85b36-126">ValidationStates</span></span>|<span data-ttu-id="85b36-127">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="85b36-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="85b36-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="85b36-128">InvalidUnfocused</span></span>|<span data-ttu-id="85b36-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="85b36-129">ValidationStates</span></span>|<span data-ttu-id="85b36-130">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="85b36-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="85b36-131">ScrollViewer ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="85b36-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="85b36-132">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="85b36-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="85b36-133">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="85b36-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="85b36-134">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="85b36-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b36-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85b36-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="85b36-136">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="85b36-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="85b36-137">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="85b36-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="85b36-138">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="85b36-138">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="85b36-139">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="85b36-139">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
