---
title: Styles et modèles ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: b782e62500edd14b40b1267c3b7f92758210a5c0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458211"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="ca617-102">Styles et modèles ToolBar</span><span class="sxs-lookup"><span data-stu-id="ca617-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="ca617-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="ca617-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="ca617-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="ca617-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ca617-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ca617-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="ca617-106">Composants de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="ca617-106">ToolBar Parts</span></span>  
 <span data-ttu-id="ca617-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="ca617-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="ca617-108">Élément</span><span class="sxs-lookup"><span data-stu-id="ca617-108">Part</span></span>|<span data-ttu-id="ca617-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="ca617-109">Type</span></span>|<span data-ttu-id="ca617-110">Description</span><span class="sxs-lookup"><span data-stu-id="ca617-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ca617-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="ca617-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="ca617-112">Objet qui contient les contrôles sur le <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="ca617-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="ca617-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="ca617-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="ca617-114">Objet qui contient les contrôles qui se trouvent dans la zone de débordement du <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="ca617-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="ca617-115">Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.ToolBar>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="ca617-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="ca617-116">(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément du <xref:System.Windows.Controls.ToolBar>; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).</span><span class="sxs-lookup"><span data-stu-id="ca617-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="ca617-117">Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer au <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="ca617-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="ca617-118">États de la barre d’outils</span><span class="sxs-lookup"><span data-stu-id="ca617-118">ToolBar States</span></span>  
 <span data-ttu-id="ca617-119">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="ca617-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="ca617-120">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="ca617-120">VisualState Name</span></span>|<span data-ttu-id="ca617-121">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ca617-121">VisualStateGroup Name</span></span>|<span data-ttu-id="ca617-122">Description</span><span class="sxs-lookup"><span data-stu-id="ca617-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ca617-123">Valide</span><span class="sxs-lookup"><span data-stu-id="ca617-123">Valid</span></span>|<span data-ttu-id="ca617-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca617-124">ValidationStates</span></span>|<span data-ttu-id="ca617-125">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="ca617-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ca617-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ca617-126">InvalidFocused</span></span>|<span data-ttu-id="ca617-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca617-127">ValidationStates</span></span>|<span data-ttu-id="ca617-128">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="ca617-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ca617-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ca617-129">InvalidUnfocused</span></span>|<span data-ttu-id="ca617-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca617-130">ValidationStates</span></span>|<span data-ttu-id="ca617-131">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="ca617-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="ca617-132">ToolBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="ca617-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="ca617-133">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="ca617-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="ca617-134">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="ca617-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ca617-135">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="ca617-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca617-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca617-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ca617-137">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="ca617-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ca617-138">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="ca617-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ca617-139">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="ca617-139">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ca617-140">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ca617-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
