---
title: Styles et modèles ProgressBar
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 6551701e86dd6abcd42f143f146c7bdadfeabbcf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283454"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="d003f-102">Styles et modèles ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d003f-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="d003f-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="d003f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="d003f-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="d003f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d003f-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="d003f-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="d003f-106">Composants ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d003f-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="d003f-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="d003f-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="d003f-108">Élément</span><span class="sxs-lookup"><span data-stu-id="d003f-108">Part</span></span>|<span data-ttu-id="d003f-109">Type</span><span class="sxs-lookup"><span data-stu-id="d003f-109">Type</span></span>|<span data-ttu-id="d003f-110">Description</span><span class="sxs-lookup"><span data-stu-id="d003f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d003f-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="d003f-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d003f-112">Objet qui indique la progression.</span><span class="sxs-lookup"><span data-stu-id="d003f-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="d003f-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="d003f-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d003f-114">Objet qui définit le chemin d’accès de l’indicateur de progression.</span><span class="sxs-lookup"><span data-stu-id="d003f-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="d003f-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="d003f-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d003f-116">Objet qui embellit la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="d003f-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="d003f-117">États de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d003f-117">ProgressBar States</span></span>  
 <span data-ttu-id="d003f-118">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="d003f-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="d003f-119">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="d003f-119">VisualState Name</span></span>|<span data-ttu-id="d003f-120">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d003f-120">VisualStateGroup Name</span></span>|<span data-ttu-id="d003f-121">Description</span><span class="sxs-lookup"><span data-stu-id="d003f-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="d003f-122">Déterminée</span><span class="sxs-lookup"><span data-stu-id="d003f-122">Determinate</span></span>|<span data-ttu-id="d003f-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d003f-123">CommonStates</span></span>|<span data-ttu-id="d003f-124"><xref:System.Windows.Controls.ProgressBar> signale la progression en fonction de la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="d003f-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="d003f-125">Déterminée</span><span class="sxs-lookup"><span data-stu-id="d003f-125">Indeterminate</span></span>|<span data-ttu-id="d003f-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d003f-126">CommonStates</span></span>|<span data-ttu-id="d003f-127"><xref:System.Windows.Controls.ProgressBar> signale la progression générique avec un modèle répétitif.</span><span class="sxs-lookup"><span data-stu-id="d003f-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="d003f-128">Valide</span><span class="sxs-lookup"><span data-stu-id="d003f-128">Valid</span></span>|<span data-ttu-id="d003f-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d003f-129">ValidationStates</span></span>|<span data-ttu-id="d003f-130">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="d003f-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d003f-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d003f-131">InvalidFocused</span></span>|<span data-ttu-id="d003f-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d003f-132">ValidationStates</span></span>|<span data-ttu-id="d003f-133">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="d003f-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d003f-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d003f-134">InvalidUnfocused</span></span>|<span data-ttu-id="d003f-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d003f-135">ValidationStates</span></span>|<span data-ttu-id="d003f-136">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="d003f-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="d003f-137">ProgressBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="d003f-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="d003f-138">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="d003f-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="d003f-139">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="d003f-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d003f-140">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="d003f-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d003f-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d003f-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d003f-142">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="d003f-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d003f-143">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="d003f-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d003f-144">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="d003f-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="d003f-145">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="d003f-145">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
