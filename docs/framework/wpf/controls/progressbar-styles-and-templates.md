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
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459874"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="fbfdd-102">Styles et modèles ProgressBar</span><span class="sxs-lookup"><span data-stu-id="fbfdd-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="fbfdd-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="fbfdd-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fbfdd-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="fbfdd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="fbfdd-106">Composants ProgressBar</span><span class="sxs-lookup"><span data-stu-id="fbfdd-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="fbfdd-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="fbfdd-108">Élément</span><span class="sxs-lookup"><span data-stu-id="fbfdd-108">Part</span></span>|<span data-ttu-id="fbfdd-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="fbfdd-109">Type</span></span>|<span data-ttu-id="fbfdd-110">Description</span><span class="sxs-lookup"><span data-stu-id="fbfdd-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fbfdd-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="fbfdd-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="fbfdd-112">Objet qui indique la progression.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="fbfdd-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="fbfdd-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="fbfdd-114">Objet qui définit le chemin d’accès de l’indicateur de progression.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="fbfdd-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="fbfdd-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="fbfdd-116">Objet qui embellit la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="fbfdd-117">États de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="fbfdd-117">ProgressBar States</span></span>  
 <span data-ttu-id="fbfdd-118">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="fbfdd-119">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="fbfdd-119">VisualState Name</span></span>|<span data-ttu-id="fbfdd-120">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="fbfdd-120">VisualStateGroup Name</span></span>|<span data-ttu-id="fbfdd-121">Description</span><span class="sxs-lookup"><span data-stu-id="fbfdd-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="fbfdd-122">Déterminée</span><span class="sxs-lookup"><span data-stu-id="fbfdd-122">Determinate</span></span>|<span data-ttu-id="fbfdd-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fbfdd-123">CommonStates</span></span>|<span data-ttu-id="fbfdd-124"><xref:System.Windows.Controls.ProgressBar> signale la progression en fonction de la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="fbfdd-125">Déterminée</span><span class="sxs-lookup"><span data-stu-id="fbfdd-125">Indeterminate</span></span>|<span data-ttu-id="fbfdd-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fbfdd-126">CommonStates</span></span>|<span data-ttu-id="fbfdd-127"><xref:System.Windows.Controls.ProgressBar> signale la progression générique avec un modèle répétitif.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="fbfdd-128">Valide</span><span class="sxs-lookup"><span data-stu-id="fbfdd-128">Valid</span></span>|<span data-ttu-id="fbfdd-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fbfdd-129">ValidationStates</span></span>|<span data-ttu-id="fbfdd-130">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fbfdd-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fbfdd-131">InvalidFocused</span></span>|<span data-ttu-id="fbfdd-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fbfdd-132">ValidationStates</span></span>|<span data-ttu-id="fbfdd-133">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fbfdd-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fbfdd-134">InvalidUnfocused</span></span>|<span data-ttu-id="fbfdd-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fbfdd-135">ValidationStates</span></span>|<span data-ttu-id="fbfdd-136">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="fbfdd-137">ProgressBar ControlTemplate, exemple</span><span class="sxs-lookup"><span data-stu-id="fbfdd-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="fbfdd-138">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="fbfdd-139">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="fbfdd-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fbfdd-140">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="fbfdd-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbfdd-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbfdd-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="fbfdd-142">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="fbfdd-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="fbfdd-143">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="fbfdd-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="fbfdd-144">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="fbfdd-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="fbfdd-145">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="fbfdd-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
