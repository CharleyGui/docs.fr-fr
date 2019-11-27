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
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="79407-102">Styles et modèles ProgressBar</span><span class="sxs-lookup"><span data-stu-id="79407-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="79407-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="79407-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="79407-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="79407-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="79407-105">Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="79407-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="79407-106">Composants ProgressBar</span><span class="sxs-lookup"><span data-stu-id="79407-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="79407-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="79407-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="79407-108">Élément</span><span class="sxs-lookup"><span data-stu-id="79407-108">Part</span></span>|<span data-ttu-id="79407-109">Type</span><span class="sxs-lookup"><span data-stu-id="79407-109">Type</span></span>|<span data-ttu-id="79407-110">Description</span><span class="sxs-lookup"><span data-stu-id="79407-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="79407-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="79407-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="79407-112">Objet qui indique la progression.</span><span class="sxs-lookup"><span data-stu-id="79407-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="79407-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="79407-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="79407-114">Objet qui définit le chemin d’accès de l’indicateur de progression.</span><span class="sxs-lookup"><span data-stu-id="79407-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="79407-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="79407-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="79407-116">Objet qui embellit la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="79407-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="79407-117">États de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="79407-117">ProgressBar States</span></span>  
 <span data-ttu-id="79407-118">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="79407-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="79407-119">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="79407-119">VisualState Name</span></span>|<span data-ttu-id="79407-120">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="79407-120">VisualStateGroup Name</span></span>|<span data-ttu-id="79407-121">Description</span><span class="sxs-lookup"><span data-stu-id="79407-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="79407-122">Déterminée</span><span class="sxs-lookup"><span data-stu-id="79407-122">Determinate</span></span>|<span data-ttu-id="79407-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="79407-123">CommonStates</span></span>|<span data-ttu-id="79407-124"><xref:System.Windows.Controls.ProgressBar> signale la progression en fonction de la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="79407-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="79407-125">Déterminée</span><span class="sxs-lookup"><span data-stu-id="79407-125">Indeterminate</span></span>|<span data-ttu-id="79407-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="79407-126">CommonStates</span></span>|<span data-ttu-id="79407-127"><xref:System.Windows.Controls.ProgressBar> signale la progression générique avec un modèle répétitif.</span><span class="sxs-lookup"><span data-stu-id="79407-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="79407-128">Valide</span><span class="sxs-lookup"><span data-stu-id="79407-128">Valid</span></span>|<span data-ttu-id="79407-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="79407-129">ValidationStates</span></span>|<span data-ttu-id="79407-130">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="79407-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="79407-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="79407-131">InvalidFocused</span></span>|<span data-ttu-id="79407-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="79407-132">ValidationStates</span></span>|<span data-ttu-id="79407-133">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="79407-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="79407-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="79407-134">InvalidUnfocused</span></span>|<span data-ttu-id="79407-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="79407-135">ValidationStates</span></span>|<span data-ttu-id="79407-136">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="79407-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="79407-137">ProgressBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="79407-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="79407-138">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="79407-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="79407-139">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="79407-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="79407-140">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="79407-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79407-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79407-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="79407-142">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="79407-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="79407-143">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="79407-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="79407-144">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="79407-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="79407-145">Créer un modèle pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="79407-145">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
