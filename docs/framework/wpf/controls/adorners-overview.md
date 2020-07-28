---
title: Vue d'ensemble des ornements
description: Découvrez Windows Presentation Foundation ornements, un type spécial de FrameworkElement qui fournit des piles à un utilisateur, telles que des handles fonctionnels pour des éléments.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167736"
---
# <a name="adorners-overview"></a>Vue d'ensemble des ornements

Les ornements sont un type spécial de <xref:System.Windows.FrameworkElement> , utilisé pour fournir des signaux visuels à un utilisateur. Les ornements permettent notamment d’ajouter des descripteurs fonctionnels à des éléments ou de fournir des informations d’état sur un contrôle.

## <a name="about-adorners"></a>À propos des ornements

Un <xref:System.Windows.Documents.Adorner> est un personnalisé <xref:System.Windows.FrameworkElement> qui est lié à un <xref:System.Windows.UIElement> . Les ornements sont restitués dans un <xref:System.Windows.Documents.AdornerLayer> , qui est une surface de rendu toujours au-dessus de l’élément orné ou d’une collection d’éléments ornés. Le rendu d’un ornement est indépendant du rendu du <xref:System.Windows.UIElement> auquel l’ornement est lié. Un ornement est généralement positionné par rapport à l’élément auquel il est lié, à l’aide de l’origine de la coordonnée 2D standard située dans l’angle supérieur gauche de l’élément orné.

Parmi les applications courantes des ornements, citons les suivantes :

- Ajout de handles fonctionnels à un <xref:System.Windows.UIElement> qui permet à un utilisateur de manipuler l’élément d’une certaine façon (redimensionner, faire pivoter, repositionner, etc.).
- Retour visuel pour indiquer différents états, ou en réponse à différents événements
- Superposition des décorations visuelles sur un <xref:System.Windows.UIElement> .
- Masquer ou substituer visuellement tout ou partie d’un <xref:System.Windows.UIElement> .

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit une infrastructure de base pour orner des éléments visuels. Le tableau suivant répertorie les principaux types utilisés pour orner des objets et leur but. Voici quelques exemples d’utilisation :

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Classe de base abstraite à partir de laquelle toutes les implémentations d’ornement concrètes sont héritées.|
|<xref:System.Windows.Documents.AdornerLayer>|Classe représentant une couche de rendu pour le ou les ornements d’un ou plusieurs éléments ornés.|
|<xref:System.Windows.Documents.AdornerDecorator>|Classe permettant d’associer une couche d’ornement à une collection d’éléments.|

## <a name="implementing-a-custom-adorner"></a>Implémentation d’un ornement personnalisé

L’infrastructure des ornements fournie par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est principalement destinée à prendre en charge la création d’ornements personnalisés. Un ornement personnalisé est créé en implémentant une classe qui hérite de la classe abstraite <xref:System.Windows.Documents.Adorner> .

> [!NOTE]
> Le parent d’un <xref:System.Windows.Documents.Adorner> est le <xref:System.Windows.Documents.AdornerLayer> qui restitue <xref:System.Windows.Documents.Adorner> , et non l’élément qui est orné.

L’exemple suivant montre une classe qui implémente un ornement simple. L’ornement d’exemple Orne simplement les angles d’un <xref:System.Windows.UIElement> avec des cercles.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
L’illustration suivante montre le SimpleCircleAdorner appliqué à un <xref:System.Windows.Controls.TextBox> :

![Capture d’écran montrant une zone de texte ornée.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Comportement de rendu des ornements

Il est important de noter que les ornements n’incluent aucun comportement de rendu inhérent ; il appartient donc à l’implémenteur d’un ornement de vérifier son rendu. Une méthode courante pour implémenter le comportement de rendu consiste à substituer la <xref:System.Windows.UIElement.OnRender%2A> méthode et à utiliser un ou plusieurs <xref:System.Windows.Media.DrawingContext> objets pour restituer les visuels de l’ornement en fonction des besoins (comme indiqué dans l’exemple ci-dessus).

> [!NOTE]
> Tout ce que vous placez dans la couche d’ornement s’affiche au dessus de tous les styles que vous avez définis. En d’autres termes, les ornements sont toujours visuellement en haut et ne peuvent pas être substitués à l’aide de l’ordre de plan.

## <a name="events-and-hit-testing"></a>Événements et test de positionnement

Les ornements reçoivent des événements d’entrée comme n’importe quel autre <xref:System.Windows.FrameworkElement> .  Étant donné qu’un ornement a toujours un ordre de plan plus élevé que l’élément qu’il Orne, l’ornement reçoit des événements d’entrée (tels que <xref:System.Windows.UIElement.Drop> ou <xref:System.Windows.UIElement.MouseMove> ) qui peuvent être prévus pour l’élément orné sous-jacent.  Un ornement peut écouter certains événements d’entrée et les passer à l’élément orné sous-jacent en déclenchant à nouveau l’événement.

Pour activer le test de positionnement direct d’éléments sous un ornement, affectez à la propriété de test de positionnement la <xref:System.Windows.UIElement.IsHitTestVisible%2A> **valeur false** sur l’ornement.  Pour plus d’informations sur le test de positionnement, consultez [test de positionnement dans la couche visuelle](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Ornementation d’un UIElement unique

Pour lier un ornement à un particulier <xref:System.Windows.UIElement> , procédez comme suit :

1. Appelez la méthode statique <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour obtenir un <xref:System.Windows.Documents.AdornerLayer> objet pour le <xref:System.Windows.UIElement> à orner. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>parcourt l’arborescence d’éléments visuels, en commençant au spécifié <xref:System.Windows.UIElement> , et retourne la première couche d’ornements qu’elle trouve. (Si aucune couche d’ornement n’est trouvée, la méthode retourne Null.)

2. Appelez la <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier l’ornement à la cible <xref:System.Windows.UIElement> .

 L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) à <xref:System.Windows.Controls.TextBox> un *myTextBox*nommé :

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.

## <a name="adorning-the-children-of-a-panel"></a>Ornementation des enfants d’un panneau

Pour lier un ornement aux enfants d’un <xref:System.Windows.Controls.Panel> , procédez comme suit :

1. Appelez la `static` méthode <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour rechercher une couche d’ornement pour l’élément dont les enfants doivent être ornés.

2. Énumérez les enfants de l’élément parent et appelez la <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier un ornement à chaque élément enfant.

L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) aux enfants d’un <xref:System.Windows.Controls.StackPanel> *myStackPanel*nommé :

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Vue d'ensemble des formes et dessins de base dans WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Peinture avec des objets d'image, de dessin et visuels](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Vue d'ensemble des objets Drawing](../graphics-multimedia/drawing-objects-overview.md)
- [Rubriques Comment](adorners-how-to-topics.md)
