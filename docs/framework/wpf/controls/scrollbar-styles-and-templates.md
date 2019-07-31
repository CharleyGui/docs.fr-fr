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
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671980"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="37233-102">Styles et modèles ScrollBar</span><span class="sxs-lookup"><span data-stu-id="37233-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="37233-103">Cette rubrique décrit les styles et les modèles pour <xref:System.Windows.Controls.Primitives.ScrollBar> le contrôle.</span><span class="sxs-lookup"><span data-stu-id="37233-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="37233-104">Vous pouvez modifier la valeur <xref:System.Windows.Controls.ControlTemplate> par défaut pour que le contrôle donne une apparence unique.</span><span class="sxs-lookup"><span data-stu-id="37233-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="37233-105">Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="37233-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="37233-106">Éléments ScrollBar</span><span class="sxs-lookup"><span data-stu-id="37233-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="37233-107">Le tableau suivant répertorie les parties <xref:System.Windows.Controls.Primitives.ScrollBar> nommées du contrôle.</span><span class="sxs-lookup"><span data-stu-id="37233-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="37233-108">Élément</span><span class="sxs-lookup"><span data-stu-id="37233-108">Part</span></span>|<span data-ttu-id="37233-109">Type</span><span class="sxs-lookup"><span data-stu-id="37233-109">Type</span></span>|<span data-ttu-id="37233-110">Description</span><span class="sxs-lookup"><span data-stu-id="37233-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="37233-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="37233-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="37233-112">Conteneur de l’élément qui indique la position du <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="37233-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="37233-113">États de la barre de défilement</span><span class="sxs-lookup"><span data-stu-id="37233-113">ScrollBar States</span></span>  
 <span data-ttu-id="37233-114">Le tableau suivant répertorie les États <xref:System.Windows.Controls.Primitives.ScrollBar> visuels du contrôle.</span><span class="sxs-lookup"><span data-stu-id="37233-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="37233-115">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="37233-115">VisualState Name</span></span>|<span data-ttu-id="37233-116">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="37233-116">VisualStateGroup Name</span></span>|<span data-ttu-id="37233-117">Description</span><span class="sxs-lookup"><span data-stu-id="37233-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="37233-118">Normale</span><span class="sxs-lookup"><span data-stu-id="37233-118">Normal</span></span>|<span data-ttu-id="37233-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="37233-119">CommonStates</span></span>|<span data-ttu-id="37233-120">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="37233-120">The default state.</span></span>|  
|<span data-ttu-id="37233-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="37233-121">MouseOver</span></span>|<span data-ttu-id="37233-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="37233-122">CommonStates</span></span>|<span data-ttu-id="37233-123">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="37233-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="37233-124">Désactivé</span><span class="sxs-lookup"><span data-stu-id="37233-124">Disabled</span></span>|<span data-ttu-id="37233-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="37233-125">CommonStates</span></span>|<span data-ttu-id="37233-126">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="37233-126">The control is disabled.</span></span>|  
|<span data-ttu-id="37233-127">Valide</span><span class="sxs-lookup"><span data-stu-id="37233-127">Valid</span></span>|<span data-ttu-id="37233-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37233-128">ValidationStates</span></span>|<span data-ttu-id="37233-129">Le contrôle utilise la <xref:System.Windows.Controls.Validation> classe et la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `false`est.</span><span class="sxs-lookup"><span data-stu-id="37233-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="37233-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="37233-130">InvalidFocused</span></span>|<span data-ttu-id="37233-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37233-131">ValidationStates</span></span>|<span data-ttu-id="37233-132">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `true` est et le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="37233-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="37233-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="37233-133">InvalidUnfocused</span></span>|<span data-ttu-id="37233-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37233-134">ValidationStates</span></span>|<span data-ttu-id="37233-135">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `true` est et le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="37233-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="37233-136">ScrollBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="37233-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="37233-137">L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.Primitives.ScrollBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="37233-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="37233-138">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="37233-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="37233-139">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="37233-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37233-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37233-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="37233-141">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="37233-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="37233-142">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="37233-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="37233-143">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="37233-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="37233-144">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="37233-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
