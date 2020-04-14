---
title: 'Comment : créer du texte avec contour'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: 86bfa396a2aa44eb511c014687501d60e170a396
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278923"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="76da5-102">Comment : Créer un texte décrit</span><span class="sxs-lookup"><span data-stu-id="76da5-102">How to: Create outlined text</span></span>

<span data-ttu-id="76da5-103">Dans la plupart des cas, lorsque vous ajoutez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] l’ornementation aux chaînes de texte de votre application, vous utilisez du texte en termes de collection de caractères discrets, ou glyphes.</span><span class="sxs-lookup"><span data-stu-id="76da5-103">In most cases, when you're adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="76da5-104">Par exemple, vous pouvez créer un pinceau de <xref:System.Windows.Controls.Control.Foreground%2A> gradient <xref:System.Windows.Controls.TextBox> linéaire et l’appliquer à la propriété d’un objet.</span><span class="sxs-lookup"><span data-stu-id="76da5-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="76da5-105">Lorsque vous affichez ou modifiez la boîte de texte, le pinceau de gradient linéaire est automatiquement appliqué à l’ensemble actuel des caractères de la chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="76da5-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Texte affiché avec un pinceau de dégradé linéaire](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 <span data-ttu-id="76da5-107">Cependant, vous pouvez également <xref:System.Windows.Media.Geometry> convertir le texte en objets, vous permettant de créer d’autres types de texte visuellement riche.</span><span class="sxs-lookup"><span data-stu-id="76da5-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="76da5-108">Par exemple, vous <xref:System.Windows.Media.Geometry> pouvez créer un objet en fonction du contour d’une chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="76da5-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="76da5-110">Lorsque le texte est <xref:System.Windows.Media.Geometry> converti en objet, il ne s’agit plus d’une collection de caractères, vous ne pouvez pas modifier les caractères de la chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="76da5-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="76da5-111">Vous pouvez néanmoins modifier l’apparence du texte converti en changeant ses propriétés de trait et de remplissage.</span><span class="sxs-lookup"><span data-stu-id="76da5-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="76da5-112">Le trait fait référence au contour du texte converti et le remplissage à la zone située à l’intérieur du contour du texte converti.</span><span class="sxs-lookup"><span data-stu-id="76da5-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="76da5-113">Les exemples suivants illustrent plusieurs façons de créer des effets visuels en modifiant le trait et le remplissage du texte converti.</span><span class="sxs-lookup"><span data-stu-id="76da5-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Texte avec différentes couleurs de trait et de remplissage](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Texte avec pinceau image appliqué au trait](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="76da5-116">Il est également possible de modifier le rectangle de la boîte de délimitation, ou de mettre en évidence, du texte converti.</span><span class="sxs-lookup"><span data-stu-id="76da5-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="76da5-117">L’exemple suivant illustre un moyen de créer des effets visuels en modifiant le trait et le point culminant du texte converti.</span><span class="sxs-lookup"><span data-stu-id="76da5-117">The following example illustrates a way to create visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Texte avec pinceau d’image appliqué à la course et mettre en évidence](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="76da5-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="76da5-119">Example</span></span>  
 <span data-ttu-id="76da5-120">La clé pour convertir <xref:System.Windows.Media.Geometry> le texte en <xref:System.Windows.Media.FormattedText> un objet est d’utiliser l’objet.</span><span class="sxs-lookup"><span data-stu-id="76da5-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="76da5-121">Une fois que vous avez créé <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> cet objet, vous <xref:System.Windows.Media.Geometry> pouvez utiliser le et les méthodes pour convertir le texte en objets.</span><span class="sxs-lookup"><span data-stu-id="76da5-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="76da5-122">La première méthode renvoie la géométrie du texte formaté; la deuxième méthode renvoie la géométrie de la boîte de délimitation du texte formaté.</span><span class="sxs-lookup"><span data-stu-id="76da5-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="76da5-123">L’exemple de code suivant <xref:System.Windows.Media.FormattedText> montre comment créer un objet et récupérer les géométries du texte formaté et de sa boîte de délimitation.</span><span class="sxs-lookup"><span data-stu-id="76da5-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="76da5-124">Afin d’afficher les <xref:System.Windows.Media.Geometry> objets récupérés, vous <xref:System.Windows.Media.DrawingContext> devez accéder à l’objet qui affiche le texte converti.</span><span class="sxs-lookup"><span data-stu-id="76da5-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that's displaying the converted text.</span></span> <span data-ttu-id="76da5-125">Dans ces exemples de code, cet accès est atteint en créant un objet de contrôle personnalisé dérivé d’une classe qui prend en charge le rendu défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="76da5-125">In these code examples, this access is achieved by creating a custom control object that's derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="76da5-126">Pour <xref:System.Windows.Media.Geometry> afficher des objets dans le contrôle <xref:System.Windows.UIElement.OnRender%2A> personnalisé, fournir un remplacement pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="76da5-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="76da5-127">Votre méthode précédée <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> devrait utiliser <xref:System.Windows.Media.Geometry> la méthode pour dessiner les objets.</span><span class="sxs-lookup"><span data-stu-id="76da5-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="76da5-128">Pour la source de l’objet de contrôle utilisateur personnalisé par exemple, voir [OutlineTextControl.cs pour C et](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) [OutlineTextControl.vb pour Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="76da5-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="76da5-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76da5-129">See also</span></span>

- [<span data-ttu-id="76da5-130">Dessin du texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="76da5-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
