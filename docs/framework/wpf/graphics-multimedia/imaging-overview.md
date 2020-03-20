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
ms.openlocfilehash: 3365c35e3e7b7fe5c0be48a65d7a14da0882c90e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186693"
---
# <a name="imaging-overview"></a>Vue d'ensemble de la création d'images
Ce sujet fournit une introduction à la Microsoft Windows Presentation Foundation Imaging Component. WPF Imaging permet aux développeurs d’afficher, de transformer et de formater des images.  

## <a name="wpf-imaging-component"></a>Composant de création d’images WPF  
 WPF Imaging fournit des améliorations significatives dans les capacités d’imagerie au sein de Microsoft Windows. Les capacités d’imagerie, telles que l’affichage d’une bitmap ou l’utilisation d’une image sur un contrôle commun dépendaient auparavant de l’interface microsoft Windows Graphics Device Interface (GDI) ou des bibliothèques Microsoft Windows GDIMD. Ces API fournissent des fonctionnalités d’imagerie de base, mais manquent de fonctionnalités telles que le support pour l’extéabilité codec et le support d’image haute fidélité. WPF Imaging est conçu pour surmonter les lacunes de GDI et GDI et de fournir un nouvel ensemble d’API pour afficher et utiliser des images dans vos applications.  
  
 Il existe deux façons d’accéder à l’API D’imagerie WPF, un composant géré et un composant non géré. Le composant non managé fournit les fonctionnalités suivantes.  
  
- Modèle d’extensibilité pour les formats d’image nouveaux ou propriétaires.  
  
- Amélioration des performances et de la sécurité sur les formats d’images autochtones, y compris le bitmap (BMP), Joint Photographics Experts Group (JPEG), Portable Network Graphics (PNG), Tagged Image File Format (TIFF), Microsoft Windows Media Photo, Graphics Interchange Format (GIF), et icône (.ico).  
  
- Préservation de la profondeur de couleur élevée des données image jusqu’à 8 bits par canal (32 bits par pixel).  
  
- Mise à l’échelle, rognage et rotation d’image non destructives.  
  
- Gestion des couleurs simplifiée.  
  
- Prise en charge des métadonnées dans les fichiers propriétaires.  
  
- Le composant géré utilise l’infrastructure non gérée pour fournir une intégration [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]transparente des images avec d’autres fonctionnalités WPF telles que , l’animation et les graphiques. Le composant géré bénéficie également du modèle d’extéabilité codec d’imagerie de la Windows Presentation Foundation (WPF) qui permet la reconnaissance automatique de nouveaux formats d’images dans les applications WPF.  
  
 La majorité de l’API WPF <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> Imaging gérée réside dans l’espace de <xref:System.Windows.Media?displayProperty=nameWithType> nom, <xref:System.Windows.Controls.Image> bien que <xref:System.Windows.Controls?displayProperty=nameWithType> plusieurs types importants, tels que <xref:System.Windows.Media.ImageBrush> et <xref:System.Windows.Media.ImageDrawing> résident dans l’espace de nom et réside dans l’espace de nom.  
  
 Cette rubrique fournit des informations supplémentaires sur le composant managé. Pour plus d’informations sur l’API non gestion, consultez la documentation de la [composante d’imagerie WPF non gestion.](/windows/desktop/wic/-wic-lh)  
  
<a name="_imageformats"></a>
## <a name="wpf-image-formats"></a>Formats d’image WPF  

 Un codec est utilisé pour décoder ou encoder un format de média spécifique. WPF Imaging comprend un codec pour les formats d’images BMP, JPEG, PNG, TIFF, Windows Media Photo, GIF et ICON. Chacun de ces codecs permet aux applications de décoder et, sauf pour les icônes, d’encoder leurs formats d’image respectifs.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>est une classe importante utilisée dans le décodage et l’encodage des images. Il s’agit de la pierre angulaire du pipeline WPF Imaging et représente un ensemble unique et constant de pixels à une certaine taille et résolution. A <xref:System.Windows.Media.Imaging.BitmapSource> peut être un cadre individuel d’une image à plusieurs images, <xref:System.Windows.Media.Imaging.BitmapSource>ou il peut être le résultat d’une transformation effectuée sur un . Il est le parent de nombreuses classes primaires utilisées <xref:System.Windows.Media.Imaging.BitmapFrame>dans l’imagerie WPF tels que .  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> est utilisé pour stocker les données bitmap réelles d’un format d’image. De nombreux formats d’images ne prennent en charge qu’un seul <xref:System.Windows.Media.Imaging.BitmapFrame>format, bien que des formats tels que GIF et TIFF prennent en charge plusieurs images par image. Les cadres sont utilisés par les décodeurs comme données d’entrée et sont transmis à des encodeurs pour créer des fichiers image.  
  
 L’exemple suivant montre <xref:System.Windows.Media.Imaging.BitmapFrame> comment un <xref:System.Windows.Media.Imaging.BitmapSource> est créé à partir d’une image puis ajouté à une image TIFF.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Décodage du format d’image  
 Le décodage d’une image est la traduction d’un format d’image en données d’image pouvant être utilisées par le système. Les données d’image peuvent ensuite être utilisées pour afficher, traiter ou encoder dans un format différent. La sélection du décodeur dépend du format d’image. La sélection du codec est automatique à moins qu’un décodeur spécifique ne soit indiqué. Les exemples de la section [Affichage d’images dans WPF](#_displayingimages) illustrent le décodage automatique. Les décodeurs de format personnalisés développés à l’aide des interfaces WPF Imaging non managérées et enregistrées auprès du système participent automatiquement à la sélection des décodeurs. Cela permet d’afficher automatiquement des formats personnalisés dans les applications WPF.  
  
 L’exemple suivant montre l’utilisation d’un décodeur bitmap pour décoder une image de format BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Encodage du format d’image  
 L’encodage d’image est la traduction de données d’image en un format d’image spécifique. Les données d’image encodées peuvent ensuite servir à créer des fichiers image. WPF Imaging fournit des encodeurs pour chacun des formats d’image décrits ci-dessus.  
  
 L’exemple suivant illustre l’utilisation d’un encodeur pour enregistrer une image bitmap nouvellement créée.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>
## <a name="displaying-images-in-wpf"></a>Affichage d’images dans WPF  
 Il existe plusieurs façons d’afficher une image dans une application De la Windows Presentation Foundation (WPF). Les images peuvent <xref:System.Windows.Controls.Image> être affichées à l’aide d’un contrôle, peintes sur un visuel à l’aide d’un <xref:System.Windows.Media.ImageBrush>, ou dessinées à l’aide d’un <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Utilisation du contrôle Image  
 <xref:System.Windows.Controls.Image>est un élément-cadre et la principale façon d’afficher des images dans les applications. Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Image> , peut être utilisé de deux façons; attribuer la syntaxe ou la syntaxe de propriété. L’exemple suivant montre comment restituer une image de 200 pixels de large à l’aide de la syntaxe d’attribut et de la syntaxe de balise de propriété. Pour plus d’informations sur les syntaxes d’attribut et de propriété, consultez [Vue d’ensemble des propriétés de dépendance](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Bon nombre des <xref:System.Windows.Media.Imaging.BitmapImage> exemples utilisent un objet pour référencer un fichier d’image. <xref:System.Windows.Media.Imaging.BitmapImage>est un <xref:System.Windows.Media.Imaging.BitmapSource> spécialisé qui [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] est optimisé pour le chargement <xref:System.Windows.Controls.Image.Source%2A> et <xref:System.Windows.Controls.Image> est un moyen facile d’afficher des images comme le d’un contrôle.  
  
 L’exemple suivant montre comment afficher une image de 200 pixels de large à l’aide de code.  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage>implémente l’interface <xref:System.ComponentModel.ISupportInitialize> pour optimiser l’initialisation sur plusieurs propriétés. Les modifications de propriété ne peuvent se produire que lors de l’initialisation de l’objet. Appelez <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> pour signaler que l’initialisation a commencé et <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> pour signaler que l’initialisation est terminée. Une fois initialisées, les modifications de propriété sont ignorées.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Rotation, conversion et rognage d’images  
 WPF permet aux utilisateurs de <xref:System.Windows.Media.Imaging.BitmapImage> transformer des <xref:System.Windows.Media.Imaging.BitmapSource> images en <xref:System.Windows.Media.Imaging.CroppedBitmap> <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>utilisant des propriétés ou en utilisant des objets supplémentaires tels que ou . Ces transformations d’image peuvent mettre à l’échelle ou faire pivoter une image, changer le format de pixel d’une image ou rogner une image.  
  
 Les rotations d’images sont effectuées à l’aide de la <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> propriété de <xref:System.Windows.Media.Imaging.BitmapImage>. Les rotations s’effectuent uniquement par incréments de 90 degrés. Dans l’exemple suivant, une image est pivotée de 90 degrés.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Convertir une image en un format de pixel <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>différent tel que l’échelle grise est fait en utilisant . Dans les exemples suivants, une <xref:System.Windows.Media.PixelFormats.Gray4%2A>image est convertie en .  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Pour recadrer une <xref:System.Windows.UIElement.Clip%2A> image, soit la propriété de <xref:System.Windows.Controls.Image> ou <xref:System.Windows.Media.Imaging.CroppedBitmap> peut être utilisé. Typiquement, si vous voulez juste afficher une <xref:System.Windows.UIElement.Clip%2A> partie d’une image, doit être utilisé. Si vous avez besoin d’encoder <xref:System.Windows.Media.Imaging.CroppedBitmap> et d’enregistrer une image recadrée, il faut l’utiliser. Dans l’exemple suivant, une image est recadrée à l’aide de la propriété Clip à l’aide d’un <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Étirement d’images  
 La <xref:System.Windows.Controls.Image.Stretch%2A> propriété contrôle la façon dont une image est étirée pour remplir son conteneur. Le <xref:System.Windows.Controls.Image.Stretch%2A> bien accepte les valeurs suivantes, définies par l’énumération <xref:System.Windows.Media.Stretch> :  
  
- <xref:System.Windows.Media.Stretch.None>: L’image n’est pas étirée pour remplir la zone de sortie. Si l’image est plus grande que la zone de sortie, elle est dessinée sur la zone de sortie, en découpant ce qui ne s’ajuste pas.  
  
- <xref:System.Windows.Media.Stretch.Fill>: L’image est mise à l’échelle pour s’adapter à la zone de sortie. Étant donné que la hauteur et la largeur de l’image sont mises à l’échelle indépendamment, les proportions d’origine de l’image risquent de ne pas être conservées. Autrement dit, l’image peut être déformée pour remplir complètement le conteneur de sortie.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: L’image est mise à l’échelle de sorte qu’elle s’intègre complètement dans la zone de sortie. Les proportions de l’image sont conservées.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: L’image est mise à l’échelle de sorte qu’elle remplit complètement la zone de sortie tout en préservant le rapport d’aspect original de l’image.  
  
 L’exemple suivant applique <xref:System.Windows.Media.Stretch> chacune des énumérations disponibles à un <xref:System.Windows.Controls.Image>.  
  
 L’image suivante montre la sortie de l’exemple et démontre l’effet des différents <xref:System.Windows.Controls.Image.Stretch%2A> paramètres lorsqu’ils sont appliqués à une image.  
  
 ![Différents paramètres d’étirement TileBrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Différents paramètres d’étirement TileBrush  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Peinture avec des images  
 Les images peuvent également être affichées <xref:System.Windows.Media.Brush>dans une application en peignant avec un . Les pinceaux permettent de peindre des objets de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aussi bien avec de simples couleurs unies qu’avec des ensembles complexes de modèles et d’images. Pour peindre avec des <xref:System.Windows.Media.ImageBrush>images, utilisez un . Un <xref:System.Windows.Media.ImageBrush> est un <xref:System.Windows.Media.TileBrush> type qui définit son contenu comme une image bitmap. Une <xref:System.Windows.Media.ImageBrush> image unique, qui est <xref:System.Windows.Media.ImageBrush.ImageSource%2A> spécifiée par sa propriété. Vous pouvez contrôler la manière dont l’image est étirée, alignée et mise en mosaïque, ce qui vous permet d’éviter la distorsion et de produire des modèles et d’autres effets. L’illustration suivante montre quelques effets <xref:System.Windows.Media.ImageBrush>qui peuvent être atteints avec un .  
  
 ![Exemples de sortie ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Les pinceaux d’image peuvent remplir des formes, des contrôles, du texte, etc.  
  
 L’exemple suivant montre comment peindre l’arrière-plan <xref:System.Windows.Media.ImageBrush>d’un bouton avec une image à l’aide d’un .  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Pour plus <xref:System.Windows.Media.ImageBrush> d’informations et peindre des images voir [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>
## <a name="image-metadata"></a>Métadonnées d’image  
 Certains fichiers image contiennent des métadonnées qui décrivent le contenu ou les caractéristiques du fichier. Par exemple, la plupart des appareils photo numériques créent des images qui contiennent des métadonnées sur la marque et le modèle de l’appareil photo utilisé pour capturer l’image. Chaque format d’image gère différemment les métadonnées, mais WPF Imaging fournit un moyen uniforme de stocker et de récupérer des métadonnées pour chaque format d’image pris en charge.  
  
 L’accès aux métadonnées est assuré par la <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> propriété d’un <xref:System.Windows.Media.Imaging.BitmapSource> objet. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>retourne <xref:System.Windows.Media.Imaging.BitmapMetadata> un objet qui comprend toutes les métadonnées contenues par l’image. Ces données peuvent figurer dans un schéma de métadonnées ou dans une combinaison de différents schémas. WPF Imaging prend en charge les schémas de métadonnées d’images suivants : Fichier d’image échangeable (Exif), tEXt (PNG Textual Data), répertoire de fichiers d’images (IFD), Conseil international des télécommunications de presse (CIPI) et plate-forme de métadonnées extensibles (XMP).  
  
 Afin de simplifier le processus de <xref:System.Windows.Media.Imaging.BitmapMetadata> lecture des métadonnées, fournit <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>plusieurs <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>propriétés nommées qui peuvent être facilement accessibles telles que , , et <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. La plupart de ces propriétés nommées peuvent également servir à écrire des métadonnées. Une prise en charge de lecture des métadonnées supplémentaire est fournie par le lecteur de requêtes de métadonnées. La <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> méthode est utilisée pour récupérer un lecteur de requêtes métadonnées en fournissant une requête à cordes telles que *"/app1/exif/"*. Dans l’exemple <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> suivant, est utilisé pour obtenir le texte stocké dans le *"/Texte / Description"* emplacement.  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Pour écrire des métadonnées, un lecteur de requêtes de métadonnées est utilisé. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>obtient l’auteur de requête et définit la valeur désirée. Dans l’exemple <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> suivant, est utilisé pour écrire le texte stocké dans le *"/Texte / Description"* emplacement.  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>
## <a name="codec-extensibility"></a>Extensibilité des codecs  
 Une caractéristique essentielle de WPF Imaging est le modèle d’extéabilité pour les nouveaux codecs d’image. Ces interfaces non mentées permettent aux développeurs de codec d’intégrer des codecs avec WPF afin que les nouveaux formats d’image puissent être automatiquement utilisés par les applications WPF.  
  
 Pour un échantillon de l’API extétabilité, voir le [Codec de l’échantillon Win32](https://go.microsoft.com/fwlink/?LinkID=160052). Cet exemple montre comment créer un décodeur et un encodeur pour un format d’image personnalisé.  
  
> [!NOTE]
> Le codec doit être signé numériquement pour pouvoir être reconnu par le système.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Codec Win32, exemple](https://go.microsoft.com/fwlink/?LinkID=160052)
