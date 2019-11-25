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
ms.openlocfilehash: 7093a78555aefd73f9bb05c0a7b5fab6b66176fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283414"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="7cf55-102">Styles et modèles ScrollBar</span><span class="sxs-lookup"><span data-stu-id="7cf55-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="7cf55-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="7cf55-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="7cf55-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="7cf55-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7cf55-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="7cf55-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="7cf55-106">Éléments ScrollBar</span><span class="sxs-lookup"><span data-stu-id="7cf55-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="7cf55-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="7cf55-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="7cf55-108">Élément</span><span class="sxs-lookup"><span data-stu-id="7cf55-108">Part</span></span>|<span data-ttu-id="7cf55-109">Type</span><span class="sxs-lookup"><span data-stu-id="7cf55-109">Type</span></span>|<span data-ttu-id="7cf55-110">Description</span><span class="sxs-lookup"><span data-stu-id="7cf55-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7cf55-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="7cf55-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="7cf55-112">Conteneur de l’élément qui indique la position du <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="7cf55-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="7cf55-113">États de la barre de défilement</span><span class="sxs-lookup"><span data-stu-id="7cf55-113">ScrollBar States</span></span>  
 <span data-ttu-id="7cf55-114">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="7cf55-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="7cf55-115">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="7cf55-115">VisualState Name</span></span>|<span data-ttu-id="7cf55-116">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7cf55-116">VisualStateGroup Name</span></span>|<span data-ttu-id="7cf55-117">Description</span><span class="sxs-lookup"><span data-stu-id="7cf55-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="7cf55-118">Normale</span><span class="sxs-lookup"><span data-stu-id="7cf55-118">Normal</span></span>|<span data-ttu-id="7cf55-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7cf55-119">CommonStates</span></span>|<span data-ttu-id="7cf55-120">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="7cf55-120">The default state.</span></span>|  
|<span data-ttu-id="7cf55-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="7cf55-121">MouseOver</span></span>|<span data-ttu-id="7cf55-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7cf55-122">CommonStates</span></span>|<span data-ttu-id="7cf55-123">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7cf55-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="7cf55-124">Désactivé</span><span class="sxs-lookup"><span data-stu-id="7cf55-124">Disabled</span></span>|<span data-ttu-id="7cf55-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7cf55-125">CommonStates</span></span>|<span data-ttu-id="7cf55-126">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7cf55-126">The control is disabled.</span></span>|  
|<span data-ttu-id="7cf55-127">Valide</span><span class="sxs-lookup"><span data-stu-id="7cf55-127">Valid</span></span>|<span data-ttu-id="7cf55-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cf55-128">ValidationStates</span></span>|<span data-ttu-id="7cf55-129">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="7cf55-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7cf55-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7cf55-130">InvalidFocused</span></span>|<span data-ttu-id="7cf55-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cf55-131">ValidationStates</span></span>|<span data-ttu-id="7cf55-132">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` et le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="7cf55-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="7cf55-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7cf55-133">InvalidUnfocused</span></span>|<span data-ttu-id="7cf55-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cf55-134">ValidationStates</span></span>|<span data-ttu-id="7cf55-135">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="7cf55-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="7cf55-136">ScrollBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="7cf55-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="7cf55-137">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="7cf55-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="7cf55-138">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="7cf55-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7cf55-139">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="7cf55-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf55-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cf55-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7cf55-141">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="7cf55-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7cf55-142">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="7cf55-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7cf55-143">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="7cf55-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7cf55-144">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="7cf55-144">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
