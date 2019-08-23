---
title: 'Procédure : Utiliser l’élément Image'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: 164eee7c10d9e388c6e6ee695af479ca2d6974b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958323"
---
# <a name="how-to-use-the-image-element"></a>Procédure : Utiliser l’élément Image
Cet exemple montre comment inclure des images dans une application à l’aide <xref:System.Windows.Controls.Image> de l’élément.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment afficher une image de 200 pixels de large. Dans cet exemple en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe d’attribut et la syntaxe de balise de propriété sont utilisées pour définir l’image. Pour plus d’informations sur les syntaxes d’attribut et de propriété, consultez [Vue d’ensemble des propriétés de dépendance](../advanced/dependency-properties-overview.md). Un <xref:System.Windows.Media.Imaging.BitmapImage> est utilisé pour définir les données sources de l’image et est défini explicitement pour l’exemple de syntaxe de balise de propriété. De plus, le <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.Media.Imaging.BitmapImage> du est défini sur la même <xref:System.Windows.Controls.Image>largeur que le <xref:System.Windows.FrameworkElement.Width%2A> du. Cela garantit que la quantité minimale de mémoire est utilisée pour le rendu de l’image.  
  
> [!NOTE]
> En général, si vous souhaitez spécifier la taille d’une image rendue, spécifiez uniquement le <xref:System.Windows.FrameworkElement.Width%2A> ou le <xref:System.Windows.FrameworkElement.Height%2A> , mais pas les deux. Si vous ne spécifiez qu’un seul de ces paramètres, les proportions de l’image sont conservées. Dans le cas contraire, l’image peut apparaître étirée ou déformée. Pour contrôler le comportement d’étirement de l’image <xref:System.Windows.Controls.Image.Stretch%2A> , <xref:System.Windows.Controls.Image.StretchDirection%2A> utilisez les propriétés et.  
  
> [!NOTE]
> Lorsque vous spécifiez la taille d’une image avec <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vous devez également définir ou <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> sur la même taille respective.  
  
 La <xref:System.Windows.Controls.Image.Stretch%2A> propriété détermine la façon dont la source de l’image est étirée pour remplir l’élément image. Pour plus d’informations, consultez l’énumération <xref:System.Windows.Media.Stretch>.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre comment afficher une image de 200 pixels de large à l’aide de code.  
  
> [!NOTE]
> Les <xref:System.Windows.Media.Imaging.BitmapImage> propriétés de définition doivent être exécutées <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> dans un <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> bloc et.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la création d’images](../graphics-multimedia/imaging-overview.md)
