---
title: Styles et modèles ContextMenu
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: fa192e20ea84e96c9f85ff84e16c63b7f56c8a98
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283537"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="7655a-102">Styles et modèles ContextMenu</span><span class="sxs-lookup"><span data-stu-id="7655a-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="7655a-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="7655a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="7655a-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="7655a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7655a-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="7655a-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="7655a-106">Composants ContextMenu</span><span class="sxs-lookup"><span data-stu-id="7655a-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="7655a-107">Le contrôle <xref:System.Windows.Controls.ContextMenu> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="7655a-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="7655a-108">Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.ContextMenu>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="7655a-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="7655a-109">(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément du <xref:System.Windows.Controls.ContextMenu>; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).</span><span class="sxs-lookup"><span data-stu-id="7655a-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="7655a-110">Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer au <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="7655a-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="7655a-111">États de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="7655a-111">ContextMenu States</span></span>  
 <span data-ttu-id="7655a-112">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="7655a-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="7655a-113">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="7655a-113">VisualState Name</span></span>|<span data-ttu-id="7655a-114">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7655a-114">VisualStateGroup Name</span></span>|<span data-ttu-id="7655a-115">Description</span><span class="sxs-lookup"><span data-stu-id="7655a-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7655a-116">Valide</span><span class="sxs-lookup"><span data-stu-id="7655a-116">Valid</span></span>|<span data-ttu-id="7655a-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7655a-117">ValidationStates</span></span>|<span data-ttu-id="7655a-118">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="7655a-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7655a-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7655a-119">InvalidFocused</span></span>|<span data-ttu-id="7655a-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7655a-120">ValidationStates</span></span>|<span data-ttu-id="7655a-121">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="7655a-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7655a-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7655a-122">InvalidUnfocused</span></span>|<span data-ttu-id="7655a-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7655a-123">ValidationStates</span></span>|<span data-ttu-id="7655a-124">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="7655a-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="7655a-125">ContextMenu ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="7655a-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="7655a-126">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="7655a-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="7655a-127">Le <xref:System.Windows.Controls.ControlTemplate> utilise les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="7655a-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7655a-128">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="7655a-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7655a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7655a-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7655a-130">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="7655a-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7655a-131">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="7655a-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7655a-132">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="7655a-132">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7655a-133">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="7655a-133">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
