---
title: Styles et modèles PasswordBox
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 227ccbda8d570868258508935a5d95f0f40663ab
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458839"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="ae8ee-102">Styles et modèles PasswordBox</span><span class="sxs-lookup"><span data-stu-id="ae8ee-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="ae8ee-103">Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="ae8ee-104">Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ae8ee-105">Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ae8ee-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="ae8ee-106">Parties de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="ae8ee-106">PasswordBox Parts</span></span>

<span data-ttu-id="ae8ee-107">Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="ae8ee-108">Élément</span><span class="sxs-lookup"><span data-stu-id="ae8ee-108">Part</span></span>|<span data-ttu-id="ae8ee-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="ae8ee-109">Type</span></span>|<span data-ttu-id="ae8ee-110">Description</span><span class="sxs-lookup"><span data-stu-id="ae8ee-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="ae8ee-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="ae8ee-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="ae8ee-112">Élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="ae8ee-113">Le texte de la <xref:System.Windows.Controls.PasswordBox> s’affiche dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="ae8ee-114">États de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="ae8ee-114">PasswordBox States</span></span>

<span data-ttu-id="ae8ee-115">Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="ae8ee-116">Nom VisualState</span><span class="sxs-lookup"><span data-stu-id="ae8ee-116">VisualState Name</span></span>|<span data-ttu-id="ae8ee-117">Nom VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ae8ee-117">VisualStateGroup Name</span></span>|<span data-ttu-id="ae8ee-118">Description</span><span class="sxs-lookup"><span data-stu-id="ae8ee-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="ae8ee-119">Normale</span><span class="sxs-lookup"><span data-stu-id="ae8ee-119">Normal</span></span>|<span data-ttu-id="ae8ee-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ae8ee-120">CommonStates</span></span>|<span data-ttu-id="ae8ee-121">État par défaut.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-121">The default state.</span></span>|
|<span data-ttu-id="ae8ee-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="ae8ee-122">MouseOver</span></span>|<span data-ttu-id="ae8ee-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ae8ee-123">CommonStates</span></span>|<span data-ttu-id="ae8ee-124">Le pointeur de souris est positionné sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="ae8ee-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="ae8ee-125">Disabled</span></span>|<span data-ttu-id="ae8ee-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ae8ee-126">CommonStates</span></span>|<span data-ttu-id="ae8ee-127">Le contrôle est désactivé.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-127">The control is disabled.</span></span>|
|<span data-ttu-id="ae8ee-128">Avec focus</span><span class="sxs-lookup"><span data-stu-id="ae8ee-128">Focused</span></span>|<span data-ttu-id="ae8ee-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ae8ee-129">FocusStates</span></span>|<span data-ttu-id="ae8ee-130">Le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-130">The control has focus.</span></span>|
|<span data-ttu-id="ae8ee-131">Sans focus</span><span class="sxs-lookup"><span data-stu-id="ae8ee-131">Unfocused</span></span>|<span data-ttu-id="ae8ee-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ae8ee-132">FocusStates</span></span>|<span data-ttu-id="ae8ee-133">Le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-133">The control does not have focus.</span></span>|
|<span data-ttu-id="ae8ee-134">Valide</span><span class="sxs-lookup"><span data-stu-id="ae8ee-134">Valid</span></span>|<span data-ttu-id="ae8ee-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ae8ee-135">ValidationStates</span></span>|<span data-ttu-id="ae8ee-136">Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="ae8ee-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ae8ee-137">InvalidFocused</span></span>|<span data-ttu-id="ae8ee-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ae8ee-138">ValidationStates</span></span>|<span data-ttu-id="ae8ee-139">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="ae8ee-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ae8ee-140">InvalidUnfocused</span></span>|<span data-ttu-id="ae8ee-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ae8ee-141">ValidationStates</span></span>|<span data-ttu-id="ae8ee-142">La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="ae8ee-143">Exemple de ControlTemplate de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="ae8ee-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="ae8ee-144">L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="ae8ee-145">L’exemple précédent utilise une ou plusieurs des ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="ae8ee-146">Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).</span><span class="sxs-lookup"><span data-stu-id="ae8ee-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae8ee-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae8ee-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ae8ee-148">Styles et modèles Control</span><span class="sxs-lookup"><span data-stu-id="ae8ee-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ae8ee-149">Personnalisation des contrôles</span><span class="sxs-lookup"><span data-stu-id="ae8ee-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ae8ee-150">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="ae8ee-150">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ae8ee-151">Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ae8ee-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
