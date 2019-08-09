---
title: Vue d'ensemble de la création d'images
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
ms.openlocfilehash: 845095567459fc486dd2f1c52e575444612c7bb8
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869123"
---
# <a name="imaging-overview"></a>Vue d'ensemble de la création d'images
Cette rubrique fournit une introduction au [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] permet aux développeurs d’afficher, de transformer et de mettre en forme des images.  

<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>Composant de création d’images WPF  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] apporte d’importantes améliorations aux fonctionnalités de création d’images dans [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Les fonctionnalités d’acquisition d’images, telles que l’affichage d’une bitmap ou l’utilisation d’une image sur un contrôle commun, s’appuient précédemment sur les bibliothèques Microsoft Windows Graphics Device Interface (GDI) ou Microsoft Windows GDI+. Ces API offrent une fonctionnalité de création d’images de base, mais ne disposent pas de fonctionnalités telles que la prise en charge de l’extensibilité des codecs et la prise en charge des images [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]est conçu pour surmonter les lacunes de GDI et GDI+ et fournir un nouvel ensemble d’API pour afficher et utiliser des images dans vos applications.  
  
 Il existe deux façons d’accéder à [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] l’API, à un composant managé et à un composant non managé. Le composant non managé fournit les fonctionnalités suivantes.  
  
- Modèle d’extensibilité pour les formats d’image nouveaux ou propriétaires.  
  
- Amélioration des performances et de la sécurité sur les formats d’images natives [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], notamment [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)]bitmap [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)](BMP), [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)],,,, gif (Graphics Interchange Format) et icône (. ico).  
  
- Préservation de la profondeur de couleur élevée des données image jusqu’à 8 bits par canal (32 bits par pixel).  
  
- Mise à l’échelle, rognage et rotation d’image non destructives.  
  
- Gestion des couleurs simplifiée.  
  
- Prise en charge des métadonnées dans les fichiers propriétaires.  
  
- Le composant managé utilise l’infrastructure non managée pour fournir une intégration transparente d’images avec d’autres fonctionnalités [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], telles que l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], l’animation et les graphiques. Le composant managé tire également parti du modèle d’extensibilité du codec d’imagerie Windows Presentation Foundation (WPF), qui permet la reconnaissance automatique [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] de nouveaux formats d’image dans les applications.  
  
 La majorité des [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] API managées résident dans l' <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> espace de noms, bien que plusieurs types importants, <xref:System.Windows.Media.ImageBrush> tels <xref:System.Windows.Media.ImageDrawing> que et résident dans <xref:System.Windows.Media?displayProperty=nameWithType> l’espace <xref:System.Windows.Controls.Image> de noms et résident dans <xref:System.Windows.Controls?displayProperty=nameWithType> le joint.  
  
 Cette rubrique fournit des informations supplémentaires sur le composant managé. Pour plus d’informations sur l’API non managée, consultez la documentation du [composant de création d’images WPF non managé](/windows/desktop/wic/-wic-lh) .  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formats d’image WPF  
 Un codec est utilisé pour décoder ou encoder un format de média spécifique. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]comprend un codec pour les formats image BMP [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]JPEG [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)],,,, GIF et icône. Chacun de ces codecs permet aux applications de décoder et, sauf pour les icônes, d’encoder leurs formats d’image respectifs.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>est une classe importante utilisée dans le décodage et l’encodage d’images. Il s’agit du bloc de construction de base du pipeline de [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] et représente un seul jeu constant de pixels à une certaine taille et à une résolution donnée. Un <xref:System.Windows.Media.Imaging.BitmapSource> peut être un frame individuel d’une image à plusieurs frames, ou il peut être le résultat d’une transformation effectuée <xref:System.Windows.Media.Imaging.BitmapSource>sur un. C’est le parent de la plupart des classes principales utilisées dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] les images telles <xref:System.Windows.Media.Imaging.BitmapFrame>que.  
  
 Un <xref:System.Windows.Media.Imaging.BitmapFrame> est utilisé pour stocker les données bitmap réelles d’un format d’image. De nombreux formats d’image ne prennent <xref:System.Windows.Media.Imaging.BitmapFrame>en charge qu’un seul format, [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] bien que des formats tels que GIF et prennent en charge plusieurs images par image. Les cadres sont utilisés par les décodeurs comme données d’entrée et sont transmis à des encodeurs pour créer des fichiers image.  
  
 L’exemple suivant montre comment un <xref:System.Windows.Media.Imaging.BitmapFrame> est créé à partir <xref:System.Windows.Media.Imaging.BitmapSource> d’un, puis ajouté [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] à une image.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Décodage du format d’image  
 Le décodage d’une image est la traduction d’un format d’image en données d’image pouvant être utilisées par le système. Les données d’image peuvent ensuite être utilisées pour afficher, traiter ou encoder dans un format différent. La sélection du décodeur dépend du format d’image. La sélection du codec est automatique à moins qu’un décodeur spécifique ne soit indiqué. Les exemples de la section [Affichage d’images dans WPF](#_displayingimages) illustrent le décodage automatique. Les décodeurs de formats personnalisés développés à l’aide d’interfaces [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] non managées et inscrits automatiquement dans le système participent à la sélection du décodeur. Cela permet d’afficher automatiquement les formats personnalisés dans les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 L’exemple suivant illustre l’utilisation d’un décodeur bitmap pour décoder une image au format BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Encodage du format d’image  
 L’encodage d’image est la traduction de données d’image en un format d’image spécifique. Les données d’image encodées peuvent ensuite servir à créer des fichiers image. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] fournit des encodeurs pour chacun des formats d’image décrits ci-dessus.  
  
 L’exemple suivant illustre l’utilisation d’un encodeur pour enregistrer une image bitmap nouvellement créée.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Affichage d’images dans WPF  
 Il existe plusieurs façons d’afficher une image dans une application Windows Presentation Foundation (WPF). Les images peuvent être affichées à <xref:System.Windows.Controls.Image> l’aide d’un contrôle, peint sur <xref:System.Windows.Media.ImageBrush>un visuel à l’aide <xref:System.Windows.Media.ImageDrawing>d’un ou dessiné à l’aide d’un.  
  
### <a name="using-the-image-control"></a>Utilisation du contrôle Image  
 <xref:System.Windows.Controls.Image>est un élément de Framework et le principal moyen d’afficher des images dans des applications. Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ,<xref:System.Windows.Controls.Image> peut être utilisé de deux manières: la syntaxe d’attribut ou la syntaxe de propriété. L’exemple suivant montre comment restituer une image de 200 pixels de large à l’aide de la syntaxe d’attribut et de la syntaxe de balise de propriété. Pour plus d’informations sur les syntaxes d’attribut et de propriété, consultez [Vue d’ensemble des propriétés de dépendance](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 La plupart des exemples utilisent un <xref:System.Windows.Media.Imaging.BitmapImage> objet pour référencer un fichier image. <xref:System.Windows.Media.Imaging.BitmapImage>est un spécialisé <xref:System.Windows.Media.Imaging.BitmapSource> qui est optimisé pour [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] le <xref:System.Windows.Controls.Image.Source%2A> chargement et est un moyen simple d’afficher des images en tant <xref:System.Windows.Controls.Image> que d’un contrôle.  
  
 L’exemple suivant montre comment afficher une image de 200 pixels de large à l’aide de code.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage>implémente l' <xref:System.ComponentModel.ISupportInitialize> interface pour optimiser l’initialisation sur plusieurs propriétés. Les modifications de propriété ne peuvent se produire que lors de l’initialisation de l’objet. Appelez <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> pour signaler que l’initialisation a démarré et <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> pour signaler que l’initialisation est terminée. Une fois initialisées, les modifications de propriété sont ignorées.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Rotation, conversion et rognage d’images  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]permet aux utilisateurs de transformer des images à l' <xref:System.Windows.Media.Imaging.BitmapImage> aide des propriétés de ou de à <xref:System.Windows.Media.Imaging.CroppedBitmap> l' <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>aide d’objets supplémentaires <xref:System.Windows.Media.Imaging.BitmapSource> tels que ou. Ces transformations d’image peuvent mettre à l’échelle ou faire pivoter une image, changer le format de pixel d’une image ou rogner une image.  
  
 Les rotations d’image sont effectuées <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> à l' <xref:System.Windows.Media.Imaging.BitmapImage>aide de la propriété de. Les rotations s’effectuent uniquement par incréments de 90 degrés. Dans l’exemple suivant, une image est pivotée de 90 degrés.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 La conversion d’une image dans un format de pixel différent, tel que <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>les nuances de gris, s’effectue à l’aide de. Dans les exemples suivants, une image est convertie <xref:System.Windows.Media.PixelFormats.Gray4%2A>en.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Pour rogner une image, vous <xref:System.Windows.UIElement.Clip%2A> pouvez utiliser <xref:System.Windows.Controls.Image> la <xref:System.Windows.Media.Imaging.CroppedBitmap> propriété de ou. En général, si vous souhaitez simplement afficher une partie d’une image, <xref:System.Windows.UIElement.Clip%2A> doit être utilisé. Si vous devez encoder et enregistrer une image rognée <xref:System.Windows.Media.Imaging.CroppedBitmap> , doit être utilisé. Dans l’exemple suivant, une image est rognée à l’aide de la <xref:System.Windows.Media.EllipseGeometry>propriété clip à l’aide d’un.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Étirement d’images  
 La <xref:System.Windows.Controls.Image.Stretch%2A> propriété contrôle la manière dont une image est étirée pour remplir son conteneur. La <xref:System.Windows.Controls.Image.Stretch%2A> propriété accepte les valeurs suivantes, définies par l' <xref:System.Windows.Media.Stretch> énumération:  
  
- <xref:System.Windows.Media.Stretch.None>: L’image n’est pas étirée pour remplir la zone de sortie. Si l’image est plus grande que la zone de sortie, elle est dessinée sur la zone de sortie, en découpant ce qui ne s’ajuste pas.  
  
- <xref:System.Windows.Media.Stretch.Fill>: L’image est mise à l’échelle pour s’ajuster à la zone de sortie. Étant donné que la hauteur et la largeur de l’image sont mises à l’échelle indépendamment, les proportions d’origine de l’image risquent de ne pas être conservées. Autrement dit, l’image peut être déformée pour remplir complètement le conteneur de sortie.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: L’image est mise à l’échelle pour s’ajuster entièrement dans la zone de sortie. Les proportions de l’image sont conservées.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: L’image est mise à l’échelle afin de remplir complètement la zone de sortie tout en conservant les proportions d’origine de l’image.  
  
 L’exemple suivant applique chacune des énumérations <xref:System.Windows.Media.Stretch> disponibles à un. <xref:System.Windows.Controls.Image>  
  
 L’illustration suivante montre la sortie de l’exemple et montre les répercussions des différents <xref:System.Windows.Controls.Image.Stretch%2A> paramètres lorsqu’ils sont appliqués à une image.  
  
 ![Différents paramètres d’étirement TileBrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Différents paramètres d’étirement TileBrush  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Peinture avec des images  
 Les images peuvent également être affichées dans une application en peignant avec <xref:System.Windows.Media.Brush>un. Les pinceaux permettent de peindre des objets de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aussi bien avec de simples couleurs unies qu’avec des ensembles complexes de modèles et d’images. Pour peindre avec des images, utilisez <xref:System.Windows.Media.ImageBrush>un. Un <xref:System.Windows.Media.ImageBrush> est un type de <xref:System.Windows.Media.TileBrush> qui définit son contenu sous la forme d’une image bitmap. Un <xref:System.Windows.Media.ImageBrush> affiche une seule image, qui est spécifiée par sa <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriété. Vous pouvez contrôler la manière dont l’image est étirée, alignée et mise en mosaïque, ce qui vous permet d’éviter la distorsion et de produire des modèles et d’autres effets. L’illustration suivante montre certains effets pouvant être obtenus avec un <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemples de sortie ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Les pinceaux d’image peuvent remplir des formes, des contrôles, du texte, etc.  
  
 L’exemple suivant montre comment peindre l’arrière-plan d’un bouton avec une image à <xref:System.Windows.Media.ImageBrush>l’aide d’un.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Pour plus d’informations <xref:System.Windows.Media.ImageBrush> sur et la peinture d’images [, consultez Peinture avec des images, des dessins et](painting-with-images-drawings-and-visuals.md)des éléments visuels.  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Métadonnées d’image  
 Certains fichiers image contiennent des métadonnées qui décrivent le contenu ou les caractéristiques du fichier. Par exemple, la plupart des appareils photo numériques créent des images qui contiennent des métadonnées sur la marque et le modèle de l’appareil photo utilisé pour capturer l’image. Chaque format d’image gère les métadonnées différemment, mais [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] offre un moyen uniforme de stocker et récupérer des métadonnées pour chaque format d’image pris en charge.  
  
 L’accès aux métadonnées est fourni <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> par le biais <xref:System.Windows.Media.Imaging.BitmapSource> de la propriété d’un objet. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>retourne un <xref:System.Windows.Media.Imaging.BitmapMetadata> objet qui contient toutes les métadonnées contenues dans l’image. Ces données peuvent figurer dans un schéma de métadonnées ou dans une combinaison de différents schémas. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]prend en charge les schémas de métadonnées d’image suivants: Fichier image d’échange (EXIF), texte (données textuelles png), répertoire du fichier image (IFD) [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)], et [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Pour simplifier le processus de lecture des métadonnées, <xref:System.Windows.Media.Imaging.BitmapMetadata> fournit plusieurs propriétés nommées qui peuvent être facilement accessibles telles <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>que <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>, et <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. La plupart de ces propriétés nommées peuvent également servir à écrire des métadonnées. Une prise en charge de lecture des métadonnées supplémentaire est fournie par le lecteur de requêtes de métadonnées. La <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> méthode est utilisée pour récupérer un lecteur de requêtes de métadonnées en fournissant une requête de chaîne telle que *«/app1/exif/»* . Dans l’exemple suivant, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> est utilisé pour obtenir le texte stocké à l’emplacement *«/texte/Description»* .  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Pour écrire des métadonnées, un lecteur de requêtes de métadonnées est utilisé. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>Obtient le writer de requête et définit la valeur souhaitée. Dans l’exemple suivant, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> est utilisé pour écrire le texte stocké à l’emplacement *«/texte/Description»* .  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Extensibilité des codecs  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] intègre, entre autres fonctionnalités essentielles, un modèle d’extensibilité pour les nouveaux codecs d’image. Ces interfaces non managées permettent aux développeurs de codecs d’intégrer des codecs à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] afin que les nouveaux formats d’image puissent automatiquement servir aux applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 Pour obtenir un exemple de l’API d’extensibilité, consultez l' [exemple de codec Win32](https://go.microsoft.com/fwlink/?LinkID=160052). Cet exemple montre comment créer un décodeur et un encodeur pour un format d’image personnalisé.  
  
> [!NOTE]
>  Le codec doit être signé numériquement pour pouvoir être reconnu par le système.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [Graphiques 2D et acquisition d'images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Codec Win32, exemple](https://go.microsoft.com/fwlink/?LinkID=160052)
