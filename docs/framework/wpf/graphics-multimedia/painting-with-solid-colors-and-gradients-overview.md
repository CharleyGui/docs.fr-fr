---
title: Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés
description: Découvrez comment utiliser des objets pour peindre avec des couleurs unies, des dégradés linéaires et des dégradés radiaux dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
ms.openlocfilehash: 957593d758afda06db106c99f6695294d4f84f73
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853666"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés

Cette rubrique explique comment utiliser <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.LinearGradientBrush> les objets, et <xref:System.Windows.Media.RadialGradientBrush> pour peindre avec des couleurs unies, des dégradés linéaires et des dégradés radiaux.

<a name="solidcolor"></a>

## <a name="painting-an-area-with-a-solid-color"></a>Peindre une zone avec une couleur unie

L’une des opérations les plus courantes d’une plateforme consiste à peindre une zone avec un solide <xref:System.Windows.Media.Color> . Pour accomplir cette tâche, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit la <xref:System.Windows.Media.SolidColorBrush> classe. Les sections suivantes décrivent les différentes façons de peindre avec un <xref:System.Windows.Media.SolidColorBrush> .

<a name="solidcolorinxaml"></a>

### <a name="using-a-solidcolorbrush-in-xaml"></a>Utiliser un élément SolidColorBrush en « XAML »

Pour peindre une zone avec une couleur unie en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez l’une des options suivantes.

- Sélectionnez un pinceau couleur unie prédéfinie en fonction d’un nom.  Par exemple, vous pouvez définir un bouton <xref:System.Windows.Controls.Control.Background%2A> sur « rouge » ou « MediumBlue ».  Pour obtenir la liste des autres pinceaux de couleur unie prédéfinis, consultez les propriétés statiques de la <xref:System.Windows.Media.Brushes> classe. Voici un exemple.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]

- Choisissez une couleur dans la palette de couleurs 32 bits en spécifiant les quantités de rouge, de vert et de bleu à combiner en une seule couleur unie.  Le format pour spécifier une couleur de la palette 32 bits est «  *#rrggbb* », où *rr* est un nombre hexadécimal à deux chiffres spécifiant la quantité relative de rouge, où *gg* spécifie la quantité de vert et où *bb* spécifie la quantité de bleu.  En outre, la couleur peut être spécifiée sous la forme « #*aarrggbb* » où *aa* spécifie la valeur *alpha*, ou transparence, de la couleur. Cette approche vous permet de créer des couleurs qui sont partiellement transparentes.  Dans l’exemple suivant, le <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button> a la valeur rouge entièrement opaque à l’aide de la notation hexadécimale.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]

- Utilisez la syntaxe de balise de propriété pour décrire un <xref:System.Windows.Media.SolidColorBrush> . Cette syntaxe est plus détaillée mais vous permet de spécifier des paramètres supplémentaires, tels que l’opacité du pinceau. Dans l’exemple suivant, les <xref:System.Windows.Controls.Control.Background%2A> Propriétés de deux <xref:System.Windows.Controls.Button> éléments ont la valeur rouge entièrement opaque. La première couleur du pinceau est décrite à l’aide d’un nom de couleur prédéfinie. La deuxième couleur du pinceau est décrite à l’aide de la notation hexadécimale.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]

<a name="solidcolorsincode"></a>

### <a name="painting-with-a-solidcolorbrush-in-code"></a>Peindre avec un élément SolidColorBrush dans le code

Pour peindre une zone avec une couleur unie dans le code, utilisez l’une des options suivantes.

- Utilisez l’un des pinceaux prédéfinis fournis par la <xref:System.Windows.Media.Brushes> classe. Dans l’exemple suivant, le <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button> a la valeur <xref:System.Windows.Media.Brushes.Red%2A> .

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]

- Créez un <xref:System.Windows.Media.SolidColorBrush> et définissez sa <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriété à l’aide d’une <xref:System.Windows.Media.Color> structure. Vous pouvez utiliser une couleur prédéfinie de la <xref:System.Windows.Media.Colors> classe ou vous pouvez créer un <xref:System.Windows.Media.Color> à l’aide de la <xref:System.Windows.Media.Color.FromArgb%2A> méthode statique.

  L’exemple suivant montre comment définir la <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriété d’un <xref:System.Windows.Media.SolidColorBrush> à l’aide d’une couleur prédéfinie.

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]

Le statique <xref:System.Windows.Media.Color.FromArgb%2A> vous permet de spécifier les valeurs alpha, rouge, vert et bleu de la couleur. La plage par défaut pour chacune de ces valeurs est comprise entre 0 et 255. Par exemple, une valeur alpha de 0 indique qu’une couleur est entièrement transparente, tandis qu’une valeur de 255 indique que la couleur est entièrement opaque. De même, une valeur de rouge de 0 indique qu’une couleur n’est pas composée de rouge, tandis qu’une valeur de 255 indique qu’une couleur est composée de la quantité maximale de rouge possible.  Dans l’exemple suivant, la couleur d’un pinceau est décrite en spécifiant des valeurs alpha, de rouge, de vert et de bleu.

[!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]

Pour obtenir d’autres façons de spécifier la couleur, consultez la <xref:System.Windows.Media.Color> rubrique de référence.

<a name="gradient"></a>

## <a name="painting-an-area-with-a-gradient"></a>Peindre une zone avec un dégradé

Un pinceau de dégradé peint une zone avec plusieurs couleurs qui se mélangent le long d’un axe. Vous pouvez les utiliser pour créer des impressions de lumière et d’ombre et ainsi donner à vos contrôles une apparence 3D. Vous pouvez également les utiliser pour simuler le verre, le chrome, l’eau et d’autres surfaces lisses.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit deux types de pinceaux de dégradé : <xref:System.Windows.Media.LinearGradientBrush> et <xref:System.Windows.Media.RadialGradientBrush> .

<a name="lineargradientbrush"></a>

## <a name="linear-gradients"></a>Dégradés linéaires

<xref:System.Windows.Media.LinearGradientBrush>Peint une zone avec un dégradé défini le long d’une ligne, l' *axe du dégradé*.  Vous spécifiez les couleurs du dégradé et leur emplacement le long de l’axe du dégradé à l’aide d' <xref:System.Windows.Media.GradientStop> objets.  Vous pouvez également modifier l’axe du dégradé, ce qui vous permet de créer des dégradés horizontaux et verticaux et d’inverser le sens du dégradé. L’axe du dégradé est décrit dans la section suivante. Par défaut, un dégradé diagonal est créé.

L’exemple suivant montre le code qui crée un dégradé linéaire avec quatre couleurs.

[!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]

Ce code génère le dégradé suivant :

![Dégradé linéaire en diagonale](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")

> [!NOTE]
> Les exemples de dégradés de cette rubrique utilisent le système de coordonnées par défaut pour définir les points de départ et les points de terminaison. Le système de coordonnées par défaut est relatif à un rectangle englobant : 0 indique 0 % du rectangle englobant et 1 indique 100 % du rectangle englobant. Vous pouvez modifier ce système de coordonnées en affectant <xref:System.Windows.Media.GradientBrush.MappingMode%2A> à la propriété la valeur <xref:System.Windows.Media.BrushMappingMode.Absolute> . Un système de coordonnées absolu n’est pas relatif à un rectangle englobant. Les valeurs sont interprétées directement dans l’espace local.

<xref:System.Windows.Media.GradientStop>Est le bloc de construction de base d’un pinceau de dégradé.  Un point de dégradé spécifie un <xref:System.Windows.Media.GradientStop.Color%2A> à un <xref:System.Windows.Media.GradientStop.Offset%2A> le long de l’axe du dégradé.

- La propriété du point de dégradé <xref:System.Windows.Media.GradientStop.Color%2A> spécifie la couleur du point de dégradé. Vous pouvez définir la couleur à l’aide d’une couleur prédéfinie (fournie par la <xref:System.Windows.Media.Colors> classe) ou en spécifiant des valeurs ScRVB ou ARVB. En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également utiliser la notation hexadécimale pour décrire une couleur. Pour plus d’informations, consultez la <xref:System.Windows.Media.Color> structure.

- La propriété du point de dégradé <xref:System.Windows.Media.GradientStop.Offset%2A> spécifie la position de la couleur du point de dégradé sur l’axe du dégradé. Le décalage est un <xref:System.Double> qui est compris entre 0 et 1. Plus une valeur de décalage de point de dégradé est proche de 0, plus la couleur est proche du début du dégradé. Plus une valeur de décalage de point de dégradé est proche de 1, plus la couleur est proche de la fin du dégradé.

La couleur de chaque point entre les extrémités est interpolée de façon linéaire sous la forme d’une combinaison de la couleur spécifiée par les deux points de dégradé. L’illustration suivante met en évidence les points de dégradé de l’exemple précédent. Les cercles indiquent l’emplacement des points de dégradé et une ligne en pointillés montre l’axe du dégradé.

![Points de dégradé dans un dégradé linéaire](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")

Le premier point de dégradé spécifie la couleur jaune pour un décalage de `0.0`.  Le deuxième point de dégradé spécifie la couleur rouge pour un décalage de `0.25`.  Les points entre ces deux points passent graduellement du jaune au rouge lorsque vous passez de gauche à droite le long de l’axe du dégradé.  Le troisième point de dégradé spécifie la couleur bleue pour un décalage de `0.75`.  Les points situés entre le deuxième et le troisième point de dégradé passent progressivement du rouge au bleu. Le quatrième point de dégradé spécifie la couleur vert citron pour un décalage de `1.0`. Les points situés entre le troisième et le quatrième point de dégradé passent progressivement du bleu au vert citron.

<a name="gradientaxis"></a>

### <a name="the-gradient-axis"></a>Axe du dégradé

Comme mentionné précédemment, les points de dégradé d’un pinceau dégradé linéaire sont positionnés le long d’une ligne, l’axe du dégradé. Vous pouvez modifier l’orientation et la taille de la ligne à l’aide des <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> Propriétés et du pinceau <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> . En manipulant le pinceau <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> , vous pouvez créer des dégradés horizontaux et verticaux, inverser le sens du dégradé, condenser la répartition du dégradé, et bien plus encore.

Par défaut, le pinceau de dégradé linéaire <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> sont relatifs à la zone qui est peinte. Le point (0,0) représente l’angle supérieur gauche de la zone que vous êtes en train de peindre, tandis que (1,1) représente le coin inférieur droit de la zone que vous êtes en train de peindre. La valeur par défaut <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> de <xref:System.Windows.Media.LinearGradientBrush> est (0,0), et sa valeur par défaut <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> est (1,1), ce qui crée un dégradé Diagonal en commençant à l’angle supérieur gauche et en étendant au coin inférieur droit de la zone qui est peinte. L’illustration suivante montre l’axe du dégradé d’un pinceau de dégradé linéaire avec les valeurs par défaut <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> .

![Axe du dégradé pour un dégradé linéaire en diagonale](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")

L’exemple suivant montre comment créer un dégradé horizontal en spécifiant les et le du pinceau <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> . Notez que les points de dégradé sont les mêmes que dans les exemples précédents. en modifiant simplement <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> , le dégradé a été remplacé par horizontal.

[!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]

L’illustration suivante montre le dégradé qui est créé. L’axe du dégradé est indiqué avec une ligne en pointillés et les points de dégradé sont indiqués par des cercles.

![Axe du dégradé pour un dégradé linéaire horizontal](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")

L’exemple suivant montre comment créer un dégradé vertical.

[!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]

L’illustration suivante montre le dégradé qui est créé. L’axe du dégradé est indiqué avec une ligne en pointillés et les points de dégradé sont indiqués par des cercles.

![Axe du dégradé pour un dégradé vertical](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")

<a name="radialgradients"></a>

## <a name="radial-gradients"></a>Dégradés radiaux

Comme un <xref:System.Windows.Media.LinearGradientBrush> , un <xref:System.Windows.Media.RadialGradientBrush> peint une zone avec des couleurs qui fusionnent le long d’un axe. Les exemples précédents ont montré comment un axe de pinceau dégradé linéaire est une ligne droite. Un axe de pinceau dégradé radial est défini par un cercle ; ses couleurs « rayonnent » de l’extérieur vers son origine.

Dans l’exemple suivant, un pinceau dégradé radial est utilisé pour peindre l’intérieur d’un rectangle.

[!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]

L’illustration suivante montre le dégradé créé dans l’exemple précédent. Les points de dégradé du pinceau ont été mis en évidence. Notez que, même si les résultats sont différents, les points de dégradé de cet exemple sont identiques aux points de dégradé des exemples précédents de pinceau dégradé linéaire.

![Arrêts du dégradé dans un dégradé radial](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")

Le <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> spécifie le point de départ de l’axe du dégradé d’un pinceau de dégradé radial. L’axe du dégradé rayonne de l’origine du dégradé vers le cercle du dégradé. Le cercle de dégradé d’un pinceau est défini par ses <xref:System.Windows.Media.RadialGradientBrush.Center%2A> <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A> Propriétés, et <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> .

L’illustration suivante montre plusieurs dégradés radiaux avec différents paramètres,, <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> <xref:System.Windows.Media.RadialGradientBrush.Center%2A> <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A> et <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> .

![Paramètres de RadialGradientBrush](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii") RadialGradientBrushes avec différents paramètres GradientOrigin, Center, RadiusX et RadiusY.

<a name="specifyinggradientcolors"></a>

## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Spécifier des points de dégradé transparents ou partiellement transparents

Étant donné que les arrêts de dégradé ne fournissent pas de propriété Opacity, vous devez spécifier le canal alpha des couleurs à l’aide de la notation hexadécimale ARVB dans le balisage ou utiliser la <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> méthode pour créer des points de dégradé transparents ou partiellement transparents. Les sections suivantes expliquent comment créer des points de dégradé partiellement transparents en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et dans le code.

<a name="argbsyntax"></a>

### <a name="specifying-color-opacity-in-xaml"></a>Spécification de l’opacité de couleur en « XAML »

Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , vous utilisez la notation hexadécimale ARVB pour spécifier l’opacité des couleurs individuelles. La notation hexadécimale ARVB utilise la syntaxe suivante :

`#` **aa** *rrggbb*

*aa* dans la ligne précédente représente une valeur hexadécimale à deux chiffres utilisée pour spécifier l’opacité de la couleur. *rr*, *gg* et *bb* représentent une valeur hexadécimale à deux chiffres utilisée pour spécifier la quantité de rouge, de vert et de bleu dans la couleur. Chaque chiffre hexadécimal peut avoir une valeur comprise entre 0 et 9 ou A et F. 0 est la plus petite valeur et F est la plus grande. Une valeur alpha de 00 indique qu’une couleur est entièrement transparente, tandis qu’une valeur alpha de FF crée une couleur entièrement opaque.  Dans l’exemple suivant, la notation ARVB hexadécimale est utilisée pour spécifier deux couleurs. La première est partiellement transparente (elle a une valeur alpha de x20), tandis que la deuxième est entièrement opaque.

[!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]

<a name="fromscrgbsyntax"></a>

### <a name="specifying-color-opacity-in-code"></a>Spécifier l’opacité de couleur dans le code

Lorsque vous utilisez du code, la <xref:System.Windows.Media.Color.FromArgb%2A> méthode statique vous permet de spécifier une valeur alpha lorsque vous créez une couleur. La méthode prend quatre paramètres de type <xref:System.Byte> . Le premier paramètre spécifie le canal alpha de la couleur ; les trois autres paramètres spécifient les valeurs de rouge, de vert et de bleu de la couleur. Cette valeur doit être comprise entre 0 et 255 inclus. Une valeur alpha de 0 indique que la couleur est entièrement transparente, tandis qu’une valeur alpha de 255 indique que la couleur est entièrement opaque. Dans l’exemple suivant, la <xref:System.Windows.Media.Color.FromArgb%2A> méthode est utilisée pour produire deux couleurs. La première couleur est partiellement transparente (elle a une valeur alpha de 32), tandis que la deuxième est entièrement opaque.

[!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]

Vous pouvez également utiliser la <xref:System.Windows.Media.Color.FromScRgb%2A> méthode, qui vous permet d’utiliser des valeurs ScRVB pour créer une couleur.

<a name="otherbrushes"></a>

## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Peindre avec des images, des dessins, des objets visuels et des motifs

<xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.DrawingBrush>les classes, et <xref:System.Windows.Media.VisualBrush> vous permettent de peindre une zone avec des images, des dessins ou des éléments visuels. Pour plus d’informations sur la peinture avec des images, des dessins et des motifs, consultez [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [Peinture avec des objets d'image, de dessin et visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d'ensemble des transformations du pinceau](brush-transformation-overview.md)
- [Couches de rendu graphiques](../advanced/graphics-rendering-tiers.md)
