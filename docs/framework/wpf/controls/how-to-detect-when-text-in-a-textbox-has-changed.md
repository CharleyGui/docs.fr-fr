---
title: 'Comment : détecter la modification du texte figurant dans un TextBox'
description: Découvrez comment utiliser l’événement TextChanged pour exécuter une méthode chaque fois que le texte d’un contrôle TextBox change dans une application Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166230"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="b8bd1-103">Comment : détecter la modification du texte figurant dans un TextBox</span><span class="sxs-lookup"><span data-stu-id="b8bd1-103">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="b8bd1-104">Cet exemple illustre une façon d’utiliser l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement pour exécuter une méthode chaque fois que le texte d’un <xref:System.Windows.Controls.TextBox> contrôle a changé.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-104">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="b8bd1-105">Dans la classe code-behind du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le <xref:System.Windows.Controls.TextBox> contrôle dont vous souhaitez analyser les modifications, insérez une méthode à appeler chaque fois que l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement se déclenche.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-105">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="b8bd1-106">Cette méthode doit avoir une signature qui correspond à ce qui est attendu par le <xref:System.Windows.Controls.TextChangedEventHandler> délégué.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-106">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="b8bd1-107">Le gestionnaire d’événements est appelé chaque fois que le contenu du <xref:System.Windows.Controls.TextBox> contrôle est modifié, soit par un utilisateur, soit par programme.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-107">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="b8bd1-108">Cet événement se déclenche lorsque le <xref:System.Windows.Controls.TextBox> contrôle est créé et initialement rempli avec du texte.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-108">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="b8bd1-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8bd1-109">Example</span></span>

<span data-ttu-id="b8bd1-110">Dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit votre <xref:System.Windows.Controls.TextBox> contrôle, spécifiez l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribut avec une valeur qui correspond au nom de la méthode de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-110">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="b8bd1-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8bd1-111">Example</span></span>

<span data-ttu-id="b8bd1-112">Dans la classe code-behind du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le <xref:System.Windows.Controls.TextBox> contrôle dont vous souhaitez analyser les modifications, insérez une méthode à appeler chaque fois que l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement se déclenche.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-112">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="b8bd1-113">Cette méthode doit avoir une signature qui correspond à ce qui est attendu par le <xref:System.Windows.Controls.TextChangedEventHandler> délégué.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-113">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="b8bd1-114">Le gestionnaire d’événements est appelé chaque fois que le contenu du <xref:System.Windows.Controls.TextBox> contrôle est modifié, soit par un utilisateur, soit par programme.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-114">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="b8bd1-115">Cet événement se déclenche lorsque le <xref:System.Windows.Controls.TextBox> contrôle est créé et initialement rempli avec du texte.</span><span class="sxs-lookup"><span data-stu-id="b8bd1-115">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="b8bd1-116">Commentaires</span><span class="sxs-lookup"><span data-stu-id="b8bd1-116">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="b8bd1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8bd1-117">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="b8bd1-118">Vue d'ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="b8bd1-118">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="b8bd1-119">Vue d'ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b8bd1-119">RichTextBox Overview</span></span>](richtextbox-overview.md)
