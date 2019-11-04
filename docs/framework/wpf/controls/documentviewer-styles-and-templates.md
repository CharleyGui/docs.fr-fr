---
title: Styles et modèles DocumentViewer
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
ms.openlocfilehash: 7a812ff913703e3aa8408da8a11d28ee5adfa7fd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460345"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="c2634-102">Styles et modèles DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="c2634-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="c2634-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="c2634-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="c2634-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="c2634-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c2634-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c2634-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="c2634-106">Parties DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="c2634-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="c2634-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="c2634-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="c2634-108">Élément</span><span class="sxs-lookup"><span data-stu-id="c2634-108">Part</span></span>|<span data-ttu-id="c2634-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="c2634-109">Type</span></span>|<span data-ttu-id="c2634-110">Description</span><span class="sxs-lookup"><span data-stu-id="c2634-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c2634-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="c2634-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="c2634-112">Contenu et zone de défilement.</span><span class="sxs-lookup"><span data-stu-id="c2634-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="c2634-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="c2634-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="c2634-114">Par défaut, la zone de recherche est située en bas.</span><span class="sxs-lookup"><span data-stu-id="c2634-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="c2634-115">États de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="c2634-115">DocumentViewer States</span></span>  
 <span data-ttu-id="c2634-116">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="c2634-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="c2634-117">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="c2634-117">VisualState Name</span></span>|<span data-ttu-id="c2634-118">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c2634-118">VisualStateGroup Name</span></span>|<span data-ttu-id="c2634-119">Description</span><span class="sxs-lookup"><span data-stu-id="c2634-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c2634-120">Valide</span><span class="sxs-lookup"><span data-stu-id="c2634-120">Valid</span></span>|<span data-ttu-id="c2634-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2634-121">ValidationStates</span></span>|<span data-ttu-id="c2634-122">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="c2634-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c2634-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c2634-123">InvalidFocused</span></span>|<span data-ttu-id="c2634-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2634-124">ValidationStates</span></span>|<span data-ttu-id="c2634-125">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="c2634-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c2634-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c2634-126">InvalidUnfocused</span></span>|<span data-ttu-id="c2634-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2634-127">ValidationStates</span></span>|<span data-ttu-id="c2634-128">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="c2634-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="c2634-129">DocumentViewer ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="c2634-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="c2634-130">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="c2634-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="c2634-131">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="c2634-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c2634-132">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="c2634-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2634-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2634-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c2634-134">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="c2634-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c2634-135">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="c2634-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c2634-136">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="c2634-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c2634-137">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c2634-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
