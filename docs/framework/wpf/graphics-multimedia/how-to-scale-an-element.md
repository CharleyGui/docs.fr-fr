---
title: "Comment : mettre à l'échelle un élément"
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 34d954f68747be9eedc0ef71634e0c18b411d260
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112048"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="0d5f7-102">Comment : mettre à l'échelle un élément</span><span class="sxs-lookup"><span data-stu-id="0d5f7-102">How to: Scale an Element</span></span>
<span data-ttu-id="0d5f7-103">Cet exemple montre comment <xref:System.Windows.Media.ScaleTransform> utiliser un élément à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="0d5f7-104">Utilisez <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> les <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriétés et les propriétés pour resize l’élément par le facteur que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="0d5f7-105">Par exemple, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> une valeur de 1,5 étend l’élément à 150 pour cent de sa largeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="0d5f7-106">Une <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> valeur de 0,5 réduit la hauteur d’un élément de 50 pour cent.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="0d5f7-107">Utilisez <xref:System.Windows.Media.ScaleTransform.CenterX%2A> le <xref:System.Windows.Media.ScaleTransform.CenterY%2A> et les propriétés pour spécifier le point qui est le centre de l’opération échelle.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="0d5f7-108">Par défaut, <xref:System.Windows.Media.ScaleTransform> a est centré au point (0,0), ce qui correspond au coin supérieur gauche du rectangle.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="0d5f7-109">Cela a pour effet de déplacer l’élément et aussi de <xref:System.Windows.Media.Transform>le faire paraître plus grand, parce que lorsque vous appliquez un , vous modifiez l’espace de coordonnées dans lequel l’objet réside.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="0d5f7-110">L’exemple suivant <xref:System.Windows.Media.ScaleTransform> utilise un pour doubler la taille d’un 50-par-50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="0d5f7-111">Le <xref:System.Windows.Media.ScaleTransform> a une valeur de 0 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> (la valeur) pour les deux et <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d5f7-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="0d5f7-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="0d5f7-113">Typiquement, vous <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> définissez et au centre de l’objet qui est mis à l’échelle: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span><span class="sxs-lookup"><span data-stu-id="0d5f7-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="0d5f7-114">L’exemple suivant <xref:System.Windows.Shapes.Rectangle> montre un autre qui est doublé de taille; cependant, <xref:System.Windows.Media.ScaleTransform> cela a une valeur de <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>25 pour les deux et , qui correspond au centre du rectangle.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="0d5f7-115">L’illustration suivante montre la <xref:System.Windows.Media.ScaleTransform> différence entre les deux opérations.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="0d5f7-116">La ligne en pointillés affiche la taille et la position du rectangle avant la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="0d5f7-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="0d5f7-117">![Échelles de 2x avec différents points centraux](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="0d5f7-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="0d5f7-118">Deux opérations ScaleTransform avec des valeurs ScaleX et ScaleY identiques, mais des centres différents</span><span class="sxs-lookup"><span data-stu-id="0d5f7-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="0d5f7-119">Pour l’échantillon complet, voir [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="0d5f7-119">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5f7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d5f7-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="0d5f7-121">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="0d5f7-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="0d5f7-122">Sujets comment se passer</span><span class="sxs-lookup"><span data-stu-id="0d5f7-122">How-to Topics</span></span>](transformations-how-to-topics.md)
