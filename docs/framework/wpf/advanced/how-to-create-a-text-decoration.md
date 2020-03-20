---
title: 'Comment : créer une décoration de texte'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185921"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="06c6d-102">Comment : créer une décoration de texte</span><span class="sxs-lookup"><span data-stu-id="06c6d-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="06c6d-103">Un <xref:System.Windows.TextDecoration> objet est une ornementation visuelle que vous pouvez ajouter au texte.</span><span class="sxs-lookup"><span data-stu-id="06c6d-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="06c6d-104">Il existe quatre types de décorations de texte : souligner, baseline, strikethrough, et overline.</span><span class="sxs-lookup"><span data-stu-id="06c6d-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="06c6d-105">L’exemple suivant montre l’emplacement des décorations de texte par rapport au texte.</span><span class="sxs-lookup"><span data-stu-id="06c6d-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 ![Diagramme des types de décoration de texte](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 <span data-ttu-id="06c6d-107">Pour ajouter une décoration de <xref:System.Windows.TextDecoration> texte au texte, créez un objet et modifiez ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="06c6d-107">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="06c6d-108">Utilisez <xref:System.Windows.TextDecoration.Location%2A> la propriété pour spécifier où la décoration de texte apparaît, comme souligner.</span><span class="sxs-lookup"><span data-stu-id="06c6d-108">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="06c6d-109">Utilisez <xref:System.Windows.TextDecoration.Pen%2A> la propriété pour spécifier l’apparence de la décoration de texte, telle qu’un remplissage solide ou une couleur de gradient.</span><span class="sxs-lookup"><span data-stu-id="06c6d-109">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="06c6d-110">Si vous ne spécifiez pas une valeur pour la <xref:System.Windows.TextDecoration.Pen%2A> propriété, les décorations par défaut à la même couleur que le texte.</span><span class="sxs-lookup"><span data-stu-id="06c6d-110">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="06c6d-111">Une fois que <xref:System.Windows.TextDecoration> vous avez défini <xref:System.Windows.TextDecorations> un objet, ajoutez-le à la collection de l’objet texte désiré.</span><span class="sxs-lookup"><span data-stu-id="06c6d-111">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="06c6d-112">L’exemple suivant montre une décoration de texte qui a été stylée avec un pinceau de gradient linéaire et un stylo pointillé.</span><span class="sxs-lookup"><span data-stu-id="06c6d-112">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 ![Ornement de texte avec souligné dégradé linéaire](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <span data-ttu-id="06c6d-114">L’objet <xref:System.Windows.Documents.Hyperlink> est un élément de contenu de flux au niveau de l’intérieur qui vous permet d’héberger des hyperliens dans le contenu du flux.</span><span class="sxs-lookup"><span data-stu-id="06c6d-114">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="06c6d-115">Par défaut, <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.TextDecoration> utilise un objet pour afficher un soulignement.</span><span class="sxs-lookup"><span data-stu-id="06c6d-115">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="06c6d-116"><xref:System.Windows.TextDecoration>les objets peuvent être intensifs en matière <xref:System.Windows.Documents.Hyperlink> de performances pour instantané, en particulier si vous avez de nombreux objets.</span><span class="sxs-lookup"><span data-stu-id="06c6d-116"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="06c6d-117">Si vous faites <xref:System.Windows.Documents.Hyperlink> un usage intensif des éléments, vous pouvez envisager de montrer <xref:System.Windows.ContentElement.MouseEnter> un point de évidence seulement lors du déclenchement d’un événement, comme l’événement.</span><span class="sxs-lookup"><span data-stu-id="06c6d-117">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="06c6d-118">Dans l’exemple suivant, le soulignement du lien « My MSN » est dynamique , il n’apparaît que lorsque l’événement <xref:System.Windows.ContentElement.MouseEnter> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="06c6d-118">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 ![Liens hypertexte affichant TextDecorations](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 <span data-ttu-id="06c6d-120">Pour plus d’informations, consultez [Spécifier si un lien hypertexte est souligné ou non](how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="06c6d-120">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06c6d-121"> Exemple</span><span class="sxs-lookup"><span data-stu-id="06c6d-121">Example</span></span>  
 <span data-ttu-id="06c6d-122">Dans l’exemple de code suivant, une décoration de texte de souligner utilise la valeur de police par défaut.</span><span class="sxs-lookup"><span data-stu-id="06c6d-122">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="06c6d-123">Dans l’exemple de code suivant, une décoration de texte de souligner est créée avec une brosse de couleur solide pour le stylo.</span><span class="sxs-lookup"><span data-stu-id="06c6d-123">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="06c6d-124">Dans l’exemple de code suivant, une décoration de texte de souligner est créée avec un pinceau de gradient linéaire pour le stylo pointillé.</span><span class="sxs-lookup"><span data-stu-id="06c6d-124">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="06c6d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06c6d-125">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="06c6d-126">Spécifier si un lien hypertexte est souligné ou non</span><span class="sxs-lookup"><span data-stu-id="06c6d-126">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
