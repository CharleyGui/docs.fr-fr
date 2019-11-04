---
title: Styles et modèles ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: f30a0abb3e4252737e513b531b8d5f49a0d47f0b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458446"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="e1d73-102">Styles et modèles ScrollBar</span><span class="sxs-lookup"><span data-stu-id="e1d73-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="e1d73-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="e1d73-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="e1d73-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="e1d73-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e1d73-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e1d73-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="e1d73-106">Éléments ScrollBar</span><span class="sxs-lookup"><span data-stu-id="e1d73-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="e1d73-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="e1d73-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="e1d73-108">Élément</span><span class="sxs-lookup"><span data-stu-id="e1d73-108">Part</span></span>|<span data-ttu-id="e1d73-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="e1d73-109">Type</span></span>|<span data-ttu-id="e1d73-110">Description</span><span class="sxs-lookup"><span data-stu-id="e1d73-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e1d73-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="e1d73-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="e1d73-112">Conteneur de l’élément qui indique la position du <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="e1d73-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="e1d73-113">États de la barre de défilement</span><span class="sxs-lookup"><span data-stu-id="e1d73-113">ScrollBar States</span></span>  
 <span data-ttu-id="e1d73-114">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="e1d73-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="e1d73-115">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="e1d73-115">VisualState Name</span></span>|<span data-ttu-id="e1d73-116">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e1d73-116">VisualStateGroup Name</span></span>|<span data-ttu-id="e1d73-117">Description</span><span class="sxs-lookup"><span data-stu-id="e1d73-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="e1d73-118">Normale</span><span class="sxs-lookup"><span data-stu-id="e1d73-118">Normal</span></span>|<span data-ttu-id="e1d73-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e1d73-119">CommonStates</span></span>|<span data-ttu-id="e1d73-120">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="e1d73-120">The default state.</span></span>|  
|<span data-ttu-id="e1d73-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e1d73-121">MouseOver</span></span>|<span data-ttu-id="e1d73-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e1d73-122">CommonStates</span></span>|<span data-ttu-id="e1d73-123">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e1d73-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="e1d73-124">Disabled</span><span class="sxs-lookup"><span data-stu-id="e1d73-124">Disabled</span></span>|<span data-ttu-id="e1d73-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e1d73-125">CommonStates</span></span>|<span data-ttu-id="e1d73-126">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="e1d73-126">The control is disabled.</span></span>|  
|<span data-ttu-id="e1d73-127">Valide</span><span class="sxs-lookup"><span data-stu-id="e1d73-127">Valid</span></span>|<span data-ttu-id="e1d73-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1d73-128">ValidationStates</span></span>|<span data-ttu-id="e1d73-129">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="e1d73-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e1d73-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e1d73-130">InvalidFocused</span></span>|<span data-ttu-id="e1d73-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1d73-131">ValidationStates</span></span>|<span data-ttu-id="e1d73-132">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` et le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="e1d73-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="e1d73-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e1d73-133">InvalidUnfocused</span></span>|<span data-ttu-id="e1d73-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1d73-134">ValidationStates</span></span>|<span data-ttu-id="e1d73-135">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="e1d73-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="e1d73-136">ScrollBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="e1d73-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="e1d73-137">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="e1d73-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="e1d73-138">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="e1d73-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e1d73-139">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="e1d73-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d73-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1d73-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e1d73-141">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="e1d73-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e1d73-142">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="e1d73-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e1d73-143">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="e1d73-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e1d73-144">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e1d73-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
