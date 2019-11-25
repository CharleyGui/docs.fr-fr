---
title: Styles et modèles Label
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: 35fcd9c15bf44d15a08c16d58847698c5ec6e574
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283507"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="be4ce-102">Styles et modèles Label</span><span class="sxs-lookup"><span data-stu-id="be4ce-102">Label Styles and Templates</span></span>
<span data-ttu-id="be4ce-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="be4ce-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="be4ce-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="be4ce-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="be4ce-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="be4ce-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="be4ce-106">Parties de l’étiquette</span><span class="sxs-lookup"><span data-stu-id="be4ce-106">Label Parts</span></span>  
 <span data-ttu-id="be4ce-107">Le contrôle <xref:System.Windows.Controls.Label> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="be4ce-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="be4ce-108">États des étiquettes</span><span class="sxs-lookup"><span data-stu-id="be4ce-108">Label States</span></span>  
 <span data-ttu-id="be4ce-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="be4ce-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="be4ce-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="be4ce-110">VisualState Name</span></span>|<span data-ttu-id="be4ce-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="be4ce-111">VisualStateGroup Name</span></span>|<span data-ttu-id="be4ce-112">Description</span><span class="sxs-lookup"><span data-stu-id="be4ce-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="be4ce-113">Valide</span><span class="sxs-lookup"><span data-stu-id="be4ce-113">Valid</span></span>|<span data-ttu-id="be4ce-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="be4ce-114">ValidationStates</span></span>|<span data-ttu-id="be4ce-115">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="be4ce-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="be4ce-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="be4ce-116">InvalidFocused</span></span>|<span data-ttu-id="be4ce-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="be4ce-117">ValidationStates</span></span>|<span data-ttu-id="be4ce-118">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="be4ce-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="be4ce-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="be4ce-119">InvalidUnfocused</span></span>|<span data-ttu-id="be4ce-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="be4ce-120">ValidationStates</span></span>|<span data-ttu-id="be4ce-121">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="be4ce-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="be4ce-122">Exemple de ControlTemplate d’étiquette</span><span class="sxs-lookup"><span data-stu-id="be4ce-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="be4ce-123">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="be4ce-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="be4ce-124">Le <xref:System.Windows.Controls.ControlTemplate> utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="be4ce-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="be4ce-125">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="be4ce-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be4ce-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be4ce-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="be4ce-127">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="be4ce-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="be4ce-128">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="be4ce-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="be4ce-129">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="be4ce-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="be4ce-130">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="be4ce-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
