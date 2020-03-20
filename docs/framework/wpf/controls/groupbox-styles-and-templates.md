---
title: Styles et modèles GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187479"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="d5faf-102">Styles et modèles GroupBox</span><span class="sxs-lookup"><span data-stu-id="d5faf-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="d5faf-103">Ce sujet décrit les styles et <xref:System.Windows.Controls.GroupBox> les modèles pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d5faf-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="d5faf-104">Vous pouvez modifier <xref:System.Windows.Controls.ControlTemplate> la valeur par défaut pour donner au contrôle une apparence unique.</span><span class="sxs-lookup"><span data-stu-id="d5faf-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d5faf-105">Pour plus d’informations, voir [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="d5faf-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a><span data-ttu-id="d5faf-106">Pièces GroupBox</span><span class="sxs-lookup"><span data-stu-id="d5faf-106">GroupBox Parts</span></span>  
 <span data-ttu-id="d5faf-107">Le <xref:System.Windows.Controls.GroupBox> contrôle n’a pas de pièces nommées.</span><span class="sxs-lookup"><span data-stu-id="d5faf-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a><span data-ttu-id="d5faf-108">États GroupBox</span><span class="sxs-lookup"><span data-stu-id="d5faf-108">GroupBox States</span></span>  
 <span data-ttu-id="d5faf-109">Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.GroupBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="d5faf-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="d5faf-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="d5faf-110">VisualState Name</span></span>|<span data-ttu-id="d5faf-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d5faf-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d5faf-112">Description</span><span class="sxs-lookup"><span data-stu-id="d5faf-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d5faf-113">Valide</span><span class="sxs-lookup"><span data-stu-id="d5faf-113">Valid</span></span>|<span data-ttu-id="d5faf-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d5faf-114">ValidationStates</span></span>|<span data-ttu-id="d5faf-115">Le contrôle <xref:System.Windows.Controls.Validation> utilise la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> classe `false`et la propriété ci-jointe est .</span><span class="sxs-lookup"><span data-stu-id="d5faf-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d5faf-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d5faf-116">InvalidFocused</span></span>|<span data-ttu-id="d5faf-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d5faf-117">ValidationStates</span></span>|<span data-ttu-id="d5faf-118">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété `true` ci-jointe est a le contrôle a mise au point.</span><span class="sxs-lookup"><span data-stu-id="d5faf-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d5faf-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d5faf-119">InvalidUnfocused</span></span>|<span data-ttu-id="d5faf-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d5faf-120">ValidationStates</span></span>|<span data-ttu-id="d5faf-121">La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété `true` ci-jointe est a le contrôle n’a pas de mise au point.</span><span class="sxs-lookup"><span data-stu-id="d5faf-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="d5faf-122">GroupBox ControlTemplate Exemple</span><span class="sxs-lookup"><span data-stu-id="d5faf-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="d5faf-123">L’exemple suivant montre <xref:System.Windows.Controls.ControlTemplate> comment <xref:System.Windows.Controls.GroupBox> définir un pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d5faf-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="d5faf-124">L’utilisation <xref:System.Windows.Controls.ControlTemplate> d’une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="d5faf-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d5faf-125">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="d5faf-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5faf-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5faf-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d5faf-127">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="d5faf-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d5faf-128">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="d5faf-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d5faf-129">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="d5faf-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="d5faf-130">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="d5faf-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
