---
title: Styles et modèles StatusBar
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: b1dd575d58571b845fc849ca432ad440d1ce3ec4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458262"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="a88ff-102">Styles et modèles StatusBar</span><span class="sxs-lookup"><span data-stu-id="a88ff-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="a88ff-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="a88ff-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="a88ff-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="a88ff-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a88ff-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a88ff-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="a88ff-106">Parties de StatusBar</span><span class="sxs-lookup"><span data-stu-id="a88ff-106">StatusBar Parts</span></span>  
 <span data-ttu-id="a88ff-107">Le contrôle <xref:System.Windows.Controls.Primitives.StatusBar> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="a88ff-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="a88ff-108">États du StatusBar</span><span class="sxs-lookup"><span data-stu-id="a88ff-108">StatusBar States</span></span>  
 <span data-ttu-id="a88ff-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="a88ff-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="a88ff-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="a88ff-110">VisualState Name</span></span>|<span data-ttu-id="a88ff-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a88ff-111">VisualStateGroup Name</span></span>|<span data-ttu-id="a88ff-112">Description</span><span class="sxs-lookup"><span data-stu-id="a88ff-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a88ff-113">Valide</span><span class="sxs-lookup"><span data-stu-id="a88ff-113">Valid</span></span>|<span data-ttu-id="a88ff-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a88ff-114">ValidationStates</span></span>|<span data-ttu-id="a88ff-115">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="a88ff-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a88ff-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a88ff-116">InvalidFocused</span></span>|<span data-ttu-id="a88ff-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a88ff-117">ValidationStates</span></span>|<span data-ttu-id="a88ff-118">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="a88ff-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a88ff-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a88ff-119">InvalidUnfocused</span></span>|<span data-ttu-id="a88ff-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a88ff-120">ValidationStates</span></span>|<span data-ttu-id="a88ff-121">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="a88ff-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="a88ff-122">Composants de StatusBarItem</span><span class="sxs-lookup"><span data-stu-id="a88ff-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="a88ff-123">Le contrôle <xref:System.Windows.Controls.Primitives.StatusBarItem> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="a88ff-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="a88ff-124">États du StatusBar</span><span class="sxs-lookup"><span data-stu-id="a88ff-124">StatusBar States</span></span>  
 <span data-ttu-id="a88ff-125">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.StatusBarItem>.</span><span class="sxs-lookup"><span data-stu-id="a88ff-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="a88ff-126">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="a88ff-126">VisualState Name</span></span>|<span data-ttu-id="a88ff-127">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a88ff-127">VisualStateGroup Name</span></span>|<span data-ttu-id="a88ff-128">Description</span><span class="sxs-lookup"><span data-stu-id="a88ff-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a88ff-129">Valide</span><span class="sxs-lookup"><span data-stu-id="a88ff-129">Valid</span></span>|<span data-ttu-id="a88ff-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a88ff-130">ValidationStates</span></span>|<span data-ttu-id="a88ff-131">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="a88ff-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a88ff-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a88ff-132">InvalidFocused</span></span>|<span data-ttu-id="a88ff-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a88ff-133">ValidationStates</span></span>|<span data-ttu-id="a88ff-134">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="a88ff-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a88ff-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a88ff-135">InvalidUnfocused</span></span>|<span data-ttu-id="a88ff-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a88ff-136">ValidationStates</span></span>|<span data-ttu-id="a88ff-137">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="a88ff-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="a88ff-138">Exemple de ControlTemplate StatusBar</span><span class="sxs-lookup"><span data-stu-id="a88ff-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="a88ff-139">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="a88ff-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="a88ff-140">Le <xref:System.Windows.Controls.ControlTemplate> utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="a88ff-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a88ff-141">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="a88ff-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88ff-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a88ff-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="a88ff-143">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="a88ff-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="a88ff-144">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="a88ff-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="a88ff-145">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="a88ff-145">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="a88ff-146">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a88ff-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
