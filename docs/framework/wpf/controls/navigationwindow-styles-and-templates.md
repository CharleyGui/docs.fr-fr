---
title: Styles et modèles NavigationWindow
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: 5cc504956ce036505ac9261ea1438c7881fa2790
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283489"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="c3ee6-102">Styles et modèles NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="c3ee6-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="c3ee6-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="c3ee6-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c3ee6-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="c3ee6-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="c3ee6-106">Éléments NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="c3ee6-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="c3ee6-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="c3ee6-108">Élément</span><span class="sxs-lookup"><span data-stu-id="c3ee6-108">Part</span></span>|<span data-ttu-id="c3ee6-109">Type</span><span class="sxs-lookup"><span data-stu-id="c3ee6-109">Type</span></span>|<span data-ttu-id="c3ee6-110">Description</span><span class="sxs-lookup"><span data-stu-id="c3ee6-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c3ee6-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="c3ee6-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="c3ee6-112">Zone du contenu.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="c3ee6-113">États de NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="c3ee6-113">NavigationWindow States</span></span>  
 <span data-ttu-id="c3ee6-114">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="c3ee6-115">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="c3ee6-115">VisualState Name</span></span>|<span data-ttu-id="c3ee6-116">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c3ee6-116">VisualStateGroup Name</span></span>|<span data-ttu-id="c3ee6-117">Description</span><span class="sxs-lookup"><span data-stu-id="c3ee6-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c3ee6-118">Valide</span><span class="sxs-lookup"><span data-stu-id="c3ee6-118">Valid</span></span>|<span data-ttu-id="c3ee6-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c3ee6-119">ValidationStates</span></span>|<span data-ttu-id="c3ee6-120">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c3ee6-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c3ee6-121">InvalidFocused</span></span>|<span data-ttu-id="c3ee6-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c3ee6-122">ValidationStates</span></span>|<span data-ttu-id="c3ee6-123">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c3ee6-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c3ee6-124">InvalidUnfocused</span></span>|<span data-ttu-id="c3ee6-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c3ee6-125">ValidationStates</span></span>|<span data-ttu-id="c3ee6-126">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="c3ee6-127">NavigationWindow ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="c3ee6-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="c3ee6-128">Bien que cet exemple contienne tous les éléments définis dans la <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Navigation.NavigationWindow> par défaut, les valeurs spécifiques doivent être considérées comme des exemples.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="c3ee6-129">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="c3ee6-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c3ee6-130">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="c3ee6-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ee6-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3ee6-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c3ee6-132">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="c3ee6-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c3ee6-133">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="c3ee6-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c3ee6-134">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="c3ee6-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c3ee6-135">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="c3ee6-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
