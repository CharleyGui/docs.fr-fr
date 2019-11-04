---
title: Styles et modèles Window
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: 48fe5887ebad86efad1b1aae39ba03a26fda3bd8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460020"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="7c114-102">Styles et modèles Window</span><span class="sxs-lookup"><span data-stu-id="7c114-102">Window Styles and Templates</span></span>
<span data-ttu-id="7c114-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="7c114-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="7c114-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="7c114-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7c114-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="7c114-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="7c114-106">Parties de fenêtre</span><span class="sxs-lookup"><span data-stu-id="7c114-106">Window Parts</span></span>  
 <span data-ttu-id="7c114-107">Le contrôle <xref:System.Windows.Window> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="7c114-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="7c114-108">États de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="7c114-108">Window States</span></span>  
 <span data-ttu-id="7c114-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="7c114-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="7c114-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="7c114-110">VisualState Name</span></span>|<span data-ttu-id="7c114-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7c114-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7c114-112">Description</span><span class="sxs-lookup"><span data-stu-id="7c114-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7c114-113">Valide</span><span class="sxs-lookup"><span data-stu-id="7c114-113">Valid</span></span>|<span data-ttu-id="7c114-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7c114-114">ValidationStates</span></span>|<span data-ttu-id="7c114-115">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="7c114-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7c114-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7c114-116">InvalidFocused</span></span>|<span data-ttu-id="7c114-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7c114-117">ValidationStates</span></span>|<span data-ttu-id="7c114-118">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="7c114-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7c114-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7c114-119">InvalidUnfocused</span></span>|<span data-ttu-id="7c114-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7c114-120">ValidationStates</span></span>|<span data-ttu-id="7c114-121">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="7c114-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="7c114-122">Exemple de fenêtre ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7c114-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="7c114-123">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="7c114-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="7c114-124">Le <xref:System.Windows.Controls.ControlTemplate> utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="7c114-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7c114-125">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="7c114-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c114-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c114-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7c114-127">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="7c114-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7c114-128">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="7c114-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7c114-129">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="7c114-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7c114-130">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7c114-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
