---
title: 'Procédure : Détecter la modification du texte figurant dans un TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855620"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="72a6b-102">Procédure : Détecter la modification du texte figurant dans un TextBox</span><span class="sxs-lookup"><span data-stu-id="72a6b-102">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="72a6b-103">Cet exemple illustre une façon d’utiliser l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement pour exécuter une méthode chaque fois que le texte <xref:System.Windows.Controls.TextBox> d’un contrôle a changé.</span><span class="sxs-lookup"><span data-stu-id="72a6b-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="72a6b-104">Dans la classe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code-behind du qui contient le <xref:System.Windows.Controls.TextBox> contrôle dont vous souhaitez analyser les modifications, insérez une méthode à appeler chaque fois que l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement se déclenche.</span><span class="sxs-lookup"><span data-stu-id="72a6b-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="72a6b-105">Cette méthode doit avoir une signature qui correspond à ce qui est attendu <xref:System.Windows.Controls.TextChangedEventHandler> par le délégué.</span><span class="sxs-lookup"><span data-stu-id="72a6b-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="72a6b-106">Le gestionnaire d’événements est appelé chaque fois que le <xref:System.Windows.Controls.TextBox> contenu du contrôle est modifié, soit par un utilisateur, soit par programme.</span><span class="sxs-lookup"><span data-stu-id="72a6b-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="72a6b-107">Cet événement se déclenche lorsque <xref:System.Windows.Controls.TextBox> le contrôle est créé et initialement rempli avec du texte.</span><span class="sxs-lookup"><span data-stu-id="72a6b-107">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="72a6b-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="72a6b-108">Example</span></span>

<span data-ttu-id="72a6b-109">Dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit votre <xref:System.Windows.Controls.TextBox> contrôle, spécifiez <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> l’attribut avec une valeur qui correspond au nom de la méthode de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="72a6b-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="72a6b-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="72a6b-110">Example</span></span>

<span data-ttu-id="72a6b-111">Dans la classe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code-behind du qui contient le <xref:System.Windows.Controls.TextBox> contrôle dont vous souhaitez analyser les modifications, insérez une méthode à appeler chaque fois que l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement se déclenche.</span><span class="sxs-lookup"><span data-stu-id="72a6b-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="72a6b-112">Cette méthode doit avoir une signature qui correspond à ce qui est attendu <xref:System.Windows.Controls.TextChangedEventHandler> par le délégué.</span><span class="sxs-lookup"><span data-stu-id="72a6b-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="72a6b-113">Le gestionnaire d’événements est appelé chaque fois que le <xref:System.Windows.Controls.TextBox> contenu du contrôle est modifié, soit par un utilisateur, soit par programme.</span><span class="sxs-lookup"><span data-stu-id="72a6b-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="72a6b-114">Cet événement se déclenche lorsque <xref:System.Windows.Controls.TextBox> le contrôle est créé et initialement rempli avec du texte.</span><span class="sxs-lookup"><span data-stu-id="72a6b-114">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="72a6b-115">Commentaires</span><span class="sxs-lookup"><span data-stu-id="72a6b-115">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="72a6b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72a6b-116">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="72a6b-117">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="72a6b-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="72a6b-118">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="72a6b-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
