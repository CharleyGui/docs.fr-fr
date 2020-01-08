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
ms.openlocfilehash: a4151ff610c67ac762f0096c6a136f4475317782
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636638"
---
# <a name="imaging-overview"></a>Vue d'ensemble de la création d'images
Cette rubrique fournit une introduction au composant Microsoft Windows Presentation Foundation Imaging. L’acquisition d’images WPF permet aux développeurs d’afficher, transformer et mettre en forme des images.  

## <a name="wpf-imaging-component"></a>Composant de création d’images WPF  
 L’acquisition d’images WPF apporte des améliorations significatives dans les fonctionnalités de création d’images dans Microsoft Windows. Les fonctionnalités d’acquisition d’images, telles que l’affichage d’une bitmap ou l’utilisation d’une image sur un contrôle commun, s’appuient précédemment sur les bibliothèques Microsoft Windows Graphics Device Interface (GDI) ou Microsoft Windows GDI+. Ces API offrent une fonctionnalité de création d’images de base, mais ne disposent pas de fonctionnalités telles que la prise en charge de l’extensibilité des codecs et la prise en charge des images L’imagerie WPF est conçue pour surmonter les lacunes de GDI et GDI+ et fournir un nouvel ensemble d’API pour afficher et utiliser des images dans vos applications.  
  
 Il existe deux façons d’accéder à l’API d’acquisition d’images WPF, un composant managé et un composant non managé. Le composant non managé fournit les fonctionnalités suivantes.  
  
- Modèle d’extensibilité pour les formats d’image nouveaux ou propriétaires.  
  
- Amélioration des performances et de la sécurité sur les formats d’images natives, notamment bitmap (BMP), JPEG (Graphics experts Group), PNG (Portable Network Graphics), TIFF (Tagged Image File Format), Microsoft Windows Media photo, GIF (Graphics Interchange Format), et icône (. ico).  
  
- Préservation de la profondeur de couleur élevée des données image jusqu’à 8 bits par canal (32 bits par pixel).  
  
- Mise à l’échelle, rognage et rotation d’image non destructives.  
  
- Gestion des couleurs simplifiée.  
  
- Prise en charge des métadonnées dans les fichiers propriétaires.  
  
- Le composant managé utilise l’infrastructure non gérée pour fournir une intégration transparente des images avec d’autres fonctionnalités WPF, telles que [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], l’animation et les graphiques. Le composant managé tire également parti du modèle d’extensibilité du codec d’imagerie Windows Presentation Foundation (WPF), qui permet la reconnaissance automatique de nouveaux formats d’image dans les applications WPF.  
  
 La majorité de l’API de création d’images WPF managée réside dans l’espace de noms <xref:System.Windows.Media.Imaging?displayProperty=nameWithType>, bien que plusieurs types importants, tels que <xref:System.Windows.Media.ImageBrush> et <xref:System.Windows.Media.ImageDrawing> résident dans l’espace de noms <xref:System.Windows.Media?displayProperty=nameWithType> et <xref:System.Windows.Controls.Image> se trouvent dans l’espace de noms <xref:System.Windows.Controls?displayProperty=nameWithType>.  
  
 Cette rubrique fournit des informations supplémentaires sur le composant managé. Pour plus d’informations sur l’API non managée, consultez la documentation du [composant de création d’images WPF non managé](/windows/desktop/wic/-wic-lh) .  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formats d’image WPF  

 Un codec est utilisé pour décoder ou encoder un format de média spécifique. L’acquisition d’images WPF comprend un codec pour les formats BMP, JPEG, PNG, TIFF, Windows Media photo, GIF et les images d’icône. Chacun de ces codecs permet aux applications de décoder et, sauf pour les icônes, d’encoder leurs formats d’image respectifs.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> est une classe importante utilisée dans le décodage et l’encodage d’images. Il s’agit du bloc de construction de base du pipeline d’images WPF et représente un jeu de pixels unique et constant à une certaine taille et résolution. Un <xref:System.Windows.Media.Imaging.BitmapSource> peut être un frame individuel d’une image à plusieurs frames, ou il peut être le résultat d’une transformation effectuée sur un <xref:System.Windows.Media.Imaging.BitmapSource>. C’est le parent de la plupart des classes principales utilisées dans les images WPF, telles que <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 Un <xref:System.Windows.Media.Imaging.BitmapFrame> est utilisé pour stocker les données bitmap réelles d’un format d’image. De nombreux formats d’image prennent uniquement en charge une seule <xref:System.Windows.Media.Imaging.BitmapFrame>, bien que les formats tels que GIF et TIFF prennent en charge plusieurs trames par image. Les cadres sont utilisés par les décodeurs comme données d’entrée et sont transmis à des encodeurs pour créer des fichiers image.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Media.Imaging.BitmapFrame> à partir d’un <xref:System.Windows.Media.Imaging.BitmapSource> puis l’ajouter à une image TIFF.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Décodage du format d’image  
 Le décodage d’une image est la traduction d’un format d’image en données d’image pouvant être utilisées par le système. Les données d’image peuvent ensuite être utilisées pour afficher, traiter ou encoder dans un format différent. La sélection du décodeur dépend du format d’image. La sélection du codec est automatique à moins qu’un décodeur spécifique ne soit indiqué. Les exemples de la section [Affichage d’images dans WPF](#_displayingimages) illustrent le décodage automatique. Les décodeurs de format personnalisés développés à l’aide des interfaces d’acquisition d’images WPF non managées et inscrits auprès du système participent automatiquement à la sélection du décodeur. Cela permet l’affichage automatique des formats personnalisés dans les applications WPF.  
  
 L’exemple suivant illustre l’utilisation d’un décodeur bitmap pour décoder une image au format BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Encodage du format d’image  
 L’encodage d’image est la traduction de données d’image en un format d’image spécifique. Les données d’image encodées peuvent ensuite servir à créer des fichiers image. L’acquisition d’images WPF fournit des encodeurs pour chacun des formats d’image décrits ci-dessus.  
  
 L’exemple suivant illustre l’utilisation d’un encodeur pour enregistrer une image bitmap nouvellement créée.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Affichage d’images dans WPF  
 Il existe plusieurs façons d’afficher une image dans une application Windows Presentation Foundation (WPF). Les images peuvent être affichées à l’aide d’un contrôle <xref:System.Windows.Controls.Image>, peint sur un visuel à l’aide d’un <xref:System.Windows.Media.ImageBrush>ou dessinées à l’aide d’un <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Utilisation du contrôle Image  
 <xref:System.Windows.Controls.Image> est un élément de Framework et le principal moyen d’afficher des images dans des applications. Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> peut être utilisé de deux manières : syntaxe d’attribut ou syntaxe de propriété. L’exemple suivant montre comment restituer une image de 200 pixels de large à l’aide de la syntaxe d’attribut et de la syntaxe de balise de propriété. Pour plus d’informations sur les syntaxes d’attribut et de propriété, consultez [Vue d’ensemble des propriétés de dépendance](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 La plupart des exemples utilisent un objet <xref:System.Windows.Media.Imaging.BitmapImage> pour référencer un fichier image. <xref:System.Windows.Media.Imaging.BitmapImage> est une <xref:System.Windows.Media.Imaging.BitmapSource> spécialisée qui est optimisée pour le chargement de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et est un moyen simple d’afficher des images en tant que <xref:System.Windows.Controls.Image.Source%2A> d’un contrôle <xref:System.Windows.Controls.Image>.  
  
 L’exemple suivant montre comment afficher une image de 200 pixels de large à l’aide de code.  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage> implémente l’interface <xref:System.ComponentModel.ISupportInitialize> pour optimiser l’initialisation sur plusieurs propriétés. Les modifications de propriété ne peuvent se produire que lors de l’initialisation de l’objet. Appelez <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> pour signaler que l’initialisation a commencé et <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> pour signaler que l’initialisation est terminée. Une fois initialisées, les modifications de propriété sont ignorées.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Rotation, conversion et rognage d’images  
 WPF permet aux utilisateurs de transformer des images à l’aide des propriétés de <xref:System.Windows.Media.Imaging.BitmapImage> ou à l’aide d’objets <xref:System.Windows.Media.Imaging.BitmapSource> supplémentaires tels que <xref:System.Windows.Media.Imaging.CroppedBitmap> ou <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Ces transformations d’image peuvent mettre à l’échelle ou faire pivoter une image, changer le format de pixel d’une image ou rogner une image.  
  
 Les rotations d’image sont effectuées à l’aide de la propriété <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> de <xref:System.Windows.Media.Imaging.BitmapImage>. Les rotations s’effectuent uniquement par incréments de 90 degrés. Dans l’exemple suivant, une image est pivotée de 90 degrés.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 La conversion d’une image dans un format de pixel différent, par exemple en nuances de gris, s’effectue à l’aide de <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Dans les exemples suivants, une image est convertie en <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Pour rogner une image, vous pouvez utiliser la propriété <xref:System.Windows.UIElement.Clip%2A> de <xref:System.Windows.Controls.Image> ou <xref:System.Windows.Media.Imaging.CroppedBitmap>. En règle générale, si vous souhaitez simplement afficher une partie d’une image, <xref:System.Windows.UIElement.Clip%2A> doit être utilisé. Si vous devez encoder et enregistrer une image rognée, le <xref:System.Windows.Media.Imaging.CroppedBitmap> doit être utilisé. Dans l’exemple suivant, une image est rognée à l’aide de la propriété clip à l’aide d’un <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Étirement d’images  
 La propriété <xref:System.Windows.Controls.Image.Stretch%2A> contrôle la manière dont une image est étirée pour remplir son conteneur. La propriété <xref:System.Windows.Controls.Image.Stretch%2A> accepte les valeurs suivantes, définies par l’énumération <xref:System.Windows.Media.Stretch> :  
  
- <xref:System.Windows.Media.Stretch.None>: l’image n’est pas étirée pour remplir la zone de sortie. Si l’image est plus grande que la zone de sortie, elle est dessinée sur la zone de sortie, en découpant ce qui ne s’ajuste pas.  
  
- <xref:System.Windows.Media.Stretch.Fill>: l’image est mise à l’échelle pour s’ajuster à la zone de sortie. Étant donné que la hauteur et la largeur de l’image sont mises à l’échelle indépendamment, les proportions d’origine de l’image risquent de ne pas être conservées. Autrement dit, l’image peut être déformée pour remplir complètement le conteneur de sortie.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: l’image est mise à l’échelle pour s’ajuster entièrement dans la zone de sortie. Les proportions de l’image sont conservées.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: l’image est mise à l’échelle afin de remplir complètement la zone de sortie tout en conservant les proportions d’origine de l’image.  
  
 L’exemple suivant applique chacune des énumérations <xref:System.Windows.Media.Stretch> disponibles à une <xref:System.Windows.Controls.Image>.  
  
 L’illustration suivante montre la sortie de l’exemple et montre l’impact des différents paramètres de <xref:System.Windows.Controls.Image.Stretch%2A> lorsqu’ils sont appliqués à une image.  
  
 ![Différents paramètres d’étirement TileBrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Différents paramètres d’étirement TileBrush  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Peinture avec des images  
 Les images peuvent également être affichées dans une application en peignant avec un <xref:System.Windows.Media.Brush>. Les pinceaux permettent de peindre des objets de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aussi bien avec de simples couleurs unies qu’avec des ensembles complexes de modèles et d’images. Pour peindre avec des images, utilisez un <xref:System.Windows.Media.ImageBrush>. Un <xref:System.Windows.Media.ImageBrush> est un type de <xref:System.Windows.Media.TileBrush> qui définit son contenu sous la forme d’une image bitmap. Une <xref:System.Windows.Media.ImageBrush> affiche une seule image, qui est spécifiée par sa propriété <xref:System.Windows.Media.ImageBrush.ImageSource%2A>. Vous pouvez contrôler la manière dont l’image est étirée, alignée et mise en mosaïque, ce qui vous permet d’éviter la distorsion et de produire des modèles et d’autres effets. L’illustration suivante montre certains effets pouvant être obtenus avec un <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemples de sortie ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Les pinceaux d’image peuvent remplir des formes, des contrôles, du texte, etc.  
  
 L’exemple suivant montre comment peindre l’arrière-plan d’un bouton avec une image à l’aide d’un <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.ImageBrush> et la peinture [d’images, consultez Peinture avec des images, des dessins et](painting-with-images-drawings-and-visuals.md)des éléments visuels.  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Métadonnées d’image  
 Certains fichiers image contiennent des métadonnées qui décrivent le contenu ou les caractéristiques du fichier. Par exemple, la plupart des appareils photo numériques créent des images qui contiennent des métadonnées sur la marque et le modèle de l’appareil photo utilisé pour capturer l’image. Chaque format d’image gère les métadonnées différemment, mais l’acquisition d’images WPF offre un moyen uniforme de stocker et de récupérer les métadonnées pour chaque format d’image pris en charge.  
  
 L’accès aux métadonnées est fourni via la propriété <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> d’un objet <xref:System.Windows.Media.Imaging.BitmapSource>. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> retourne un objet <xref:System.Windows.Media.Imaging.BitmapMetadata> qui comprend toutes les métadonnées contenues dans l’image. Ces données peuvent figurer dans un schéma de métadonnées ou dans une combinaison de différents schémas. L’acquisition d’images WPF prend en charge les schémas de métadonnées d’image suivants : le fichier image (EXIF), le texte (données textuelles PNG), le répertoire de fichiers image (IFD), le Conseil International Press Telecommunications (IPTC) et la plateforme de métadonnées extensible (XMP).  
  
 Pour simplifier le processus de lecture des métadonnées, <xref:System.Windows.Media.Imaging.BitmapMetadata> fournit plusieurs propriétés nommées qui peuvent être facilement accessibles comme <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>et <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. La plupart de ces propriétés nommées peuvent également servir à écrire des métadonnées. Une prise en charge de lecture des métadonnées supplémentaire est fournie par le lecteur de requêtes de métadonnées. La méthode <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> est utilisée pour récupérer un lecteur de requêtes de métadonnées en fournissant une requête de chaîne telle que *« /app1/exif/ »* . Dans l’exemple suivant, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> est utilisé pour obtenir le texte stocké à l’emplacement *« /texte/Description »* .  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Pour écrire des métadonnées, un lecteur de requêtes de métadonnées est utilisé. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> obtient le générateur de requêtes et définit la valeur souhaitée. Dans l’exemple suivant, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> est utilisé pour écrire le texte stocké à l’emplacement *« /texte/Description »* .  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Extensibilité des codecs  
 Une fonctionnalité principale de l’acquisition d’images WPF est le modèle d’extensibilité pour les nouveaux codecs d’image. Ces interfaces non managées permettent aux développeurs de codecs d’intégrer des codecs à WPF afin que de nouveaux formats d’image puissent être utilisés automatiquement par les applications WPF.  
  
 Pour obtenir un exemple de l’API d’extensibilité, consultez l' [exemple de codec Win32](https://go.microsoft.com/fwlink/?LinkID=160052). Cet exemple montre comment créer un décodeur et un encodeur pour un format d’image personnalisé.  
  
> [!NOTE]
> Le codec doit être signé numériquement pour pouvoir être reconnu par le système.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [Graphiques 2D et acquisition d'images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Codec Win32, exemple](https://go.microsoft.com/fwlink/?LinkID=160052)
