---
title: 'Comment : implémenter la validation de la liaison'
description: Découvrez comment utiliser la validation de liaison pour fournir des commentaires visuels à l’utilisateur lorsqu’une valeur non valide est entrée dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 0813be9f79a83a9dae26db1dadb58b5e973339fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617880"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="436e4-103">Comment : implémenter la validation de la liaison</span><span class="sxs-lookup"><span data-stu-id="436e4-103">How to: Implement Binding Validation</span></span>

<span data-ttu-id="436e4-104">Cet exemple montre comment utiliser un <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> et un déclencheur de style pour fournir des commentaires visuels afin d’informer l’utilisateur lorsqu’une valeur non valide est entrée, en fonction d’une règle de validation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="436e4-104">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>

## <a name="example"></a><span data-ttu-id="436e4-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="436e4-105">Example</span></span>

<span data-ttu-id="436e4-106">Le contenu de texte du <xref:System.Windows.Controls.TextBox> dans l’exemple suivant est lié à la `Age` propriété (de type int) d’un objet de source de liaison nommé `ods` .</span><span class="sxs-lookup"><span data-stu-id="436e4-106">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="436e4-107">La liaison est configurée pour utiliser une règle de validation nommée `AgeRangeRule` afin que si l’utilisateur entre des caractères non numériques ou une valeur inférieure à 21 ou supérieure à 130, un point d’exclamation rouge apparaisse en regard de la zone de texte et une info-bulle contenant le message d’erreur s’affiche lorsque l’utilisateur déplace la souris sur la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="436e4-107">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

<span data-ttu-id="436e4-108">L’exemple suivant illustre l’implémentation de `AgeRangeRule` , qui hérite de <xref:System.Windows.Controls.ValidationRule> et substitue la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="436e4-108">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="436e4-109">La `Int32.Parse` méthode est appelée sur la valeur pour s’assurer qu’elle ne contient pas de caractères non valides.</span><span class="sxs-lookup"><span data-stu-id="436e4-109">The `Int32.Parse` method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="436e4-110">La <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode retourne une <xref:System.Windows.Controls.ValidationResult> valeur qui indique si la valeur est valide selon qu’une exception est interceptée pendant l’analyse et si la valeur d’âge est en dehors des limites inférieure et supérieure.</span><span class="sxs-lookup"><span data-stu-id="436e4-110">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

<span data-ttu-id="436e4-111">L’exemple suivant montre le personnalisé <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` qui crée un point d’exclamation rouge pour notifier l’utilisateur d’une erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="436e4-111">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="436e4-112">Les modèles de contrôle sont utilisés pour redéfinir l’apparence d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="436e4-112">Control templates are used to redefine the appearance of a control.</span></span>

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

<span data-ttu-id="436e4-113">Comme indiqué dans l’exemple suivant, le <xref:System.Windows.Controls.ToolTip> qui affiche le message d’erreur est créé à l’aide du style nommé `textBoxInError` .</span><span class="sxs-lookup"><span data-stu-id="436e4-113">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="436e4-114">Si la valeur de <xref:System.Windows.Controls.Validation.HasError%2A> est `true` , le déclencheur affecte à l’info-bulle du actuel la <xref:System.Windows.Controls.TextBox> première erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="436e4-114">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="436e4-115"><xref:System.Windows.Data.Binding.RelativeSource%2A>A la valeur <xref:System.Windows.Data.RelativeSourceMode.Self> , en faisant référence à l’élément actuel.</span><span class="sxs-lookup"><span data-stu-id="436e4-115">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

<span data-ttu-id="436e4-116">Pour obtenir un exemple complet, consultez [exemple de validation de liaison](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="436e4-116">For the complete example, see [Bind Validation sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>
  
<span data-ttu-id="436e4-117">Notez que si vous ne fournissez pas de personnalisé, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> le modèle d’erreur par défaut apparaît pour fournir des commentaires visuels à l’utilisateur en cas d’erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="436e4-117">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="436e4-118">Pour plus d’informations, consultez la section relative à la validation de données de la rubrique [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="436e4-118">See "Data Validation" in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="436e4-119">En outre, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une règle de validation intégrée qui capte les exceptions levées pendant la mise à jour de la propriété de source de liaison.</span><span class="sxs-lookup"><span data-stu-id="436e4-119">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="436e4-120">Pour plus d’informations, consultez <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="436e4-120">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>

## <a name="see-also"></a><span data-ttu-id="436e4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="436e4-121">See also</span></span>

- [<span data-ttu-id="436e4-122">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="436e4-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="436e4-123">Rubriques de procédures</span><span class="sxs-lookup"><span data-stu-id="436e4-123">How-to Topics</span></span>](data-binding-how-to-topics.md)
