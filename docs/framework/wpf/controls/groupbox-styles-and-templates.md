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
ms.openlocfilehash: e5befffc86f26176da4accfc01239a08d4978713
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283764"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="41b14-102">Styles et modèles GroupBox</span><span class="sxs-lookup"><span data-stu-id="41b14-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="41b14-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="41b14-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="41b14-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="41b14-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="41b14-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="41b14-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="41b14-106">Composants de GroupBox</span><span class="sxs-lookup"><span data-stu-id="41b14-106">GroupBox Parts</span></span>  
 <span data-ttu-id="41b14-107">Le contrôle <xref:System.Windows.Controls.GroupBox> n’a pas de parties nommées.</span><span class="sxs-lookup"><span data-stu-id="41b14-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="41b14-108">États de GroupBox</span><span class="sxs-lookup"><span data-stu-id="41b14-108">GroupBox States</span></span>  
 <span data-ttu-id="41b14-109">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="41b14-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="41b14-110">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="41b14-110">VisualState Name</span></span>|<span data-ttu-id="41b14-111">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="41b14-111">VisualStateGroup Name</span></span>|<span data-ttu-id="41b14-112">Description</span><span class="sxs-lookup"><span data-stu-id="41b14-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="41b14-113">Valide</span><span class="sxs-lookup"><span data-stu-id="41b14-113">Valid</span></span>|<span data-ttu-id="41b14-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="41b14-114">ValidationStates</span></span>|<span data-ttu-id="41b14-115">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="41b14-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="41b14-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="41b14-116">InvalidFocused</span></span>|<span data-ttu-id="41b14-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="41b14-117">ValidationStates</span></span>|<span data-ttu-id="41b14-118">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="41b14-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="41b14-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="41b14-119">InvalidUnfocused</span></span>|<span data-ttu-id="41b14-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="41b14-120">ValidationStates</span></span>|<span data-ttu-id="41b14-121">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="41b14-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="41b14-122">GroupBox ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="41b14-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="41b14-123">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="41b14-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="41b14-124">Le <xref:System.Windows.Controls.ControlTemplate> utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="41b14-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="41b14-125">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="41b14-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b14-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41b14-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="41b14-127">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="41b14-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="41b14-128">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="41b14-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="41b14-129">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="41b14-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="41b14-130">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="41b14-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
