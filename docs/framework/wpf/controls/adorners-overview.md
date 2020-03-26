---
title: Vue d'ensemble des ornements
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111177"
---
# <a name="adorners-overview"></a>Vue d'ensemble des ornements

Les adorateurs sont un <xref:System.Windows.FrameworkElement>type spécial de , utilisé pour fournir des indices visuels à un utilisateur. Les ornements permettent notamment d’ajouter des descripteurs fonctionnels à des éléments ou de fournir des informations d’état sur un contrôle.

## <a name="about-adorners"></a>À propos des ornements

Un <xref:System.Windows.Documents.Adorner> est <xref:System.Windows.FrameworkElement> une coutume qui <xref:System.Windows.UIElement>est lié à un . Les adorateurs sont rendus <xref:System.Windows.Documents.AdornerLayer>dans un , qui est une surface de rendu qui est toujours au-dessus de l’élément orné ou une collection d’éléments ornés. Le rendu d’un adorant est <xref:System.Windows.UIElement> indépendant du rendu de l’adorant lié à. Un adorant est généralement positionné par rapport à l’élément auquel il est lié, en utilisant l’origine de coordonnées 2D standard située en haut à gauche de l’élément orné.

Parmi les applications courantes des ornements, citons les suivantes :

- Ajout de poignées <xref:System.Windows.UIElement> fonctionnelles à un qui permet à un utilisateur de manipuler l’élément d’une manière ou d’une autre (resize, rotate, repositionnement, etc.).
- Retour visuel pour indiquer différents états, ou en réponse à différents événements
- Superposer les <xref:System.Windows.UIElement>décorations visuelles sur un .
- Masquer visuellement ou remplacer une <xref:System.Windows.UIElement>partie ou la totalité d’un .

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit une infrastructure de base pour orner des éléments visuels. Le tableau suivant répertorie les principaux types utilisés pour orner des objets et leur but. Voici plusieurs exemples d’utilisation :

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Classe de base abstraite à partir de laquelle toutes les implémentations d’ornement concrètes sont héritées.|
|<xref:System.Windows.Documents.AdornerLayer>|Classe représentant une couche de rendu pour le ou les ornements d’un ou plusieurs éléments ornés.|
|<xref:System.Windows.Documents.AdornerDecorator>|Classe permettant d’associer une couche d’ornement à une collection d’éléments.|

## <a name="implementing-a-custom-adorner"></a>Implémentation d’un ornement personnalisé

L’infrastructure des ornements fournie par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est principalement destinée à prendre en charge la création d’ornements personnalisés. Un adorant personnalisé est créé en mettant en <xref:System.Windows.Documents.Adorner> œuvre une classe qui hérite de la classe abstraite.

> [!NOTE]
> Le parent <xref:System.Windows.Documents.Adorner> d’un est <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.Documents.Adorner>le qui rend le , pas l’élément étant orné.

L’exemple suivant montre une classe qui implémente un ornement simple. L’exemple orne simplement les <xref:System.Windows.UIElement> coins d’un avec des cercles.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
L’image suivante montre le SimpleCircleAdorner appliqué à un <xref:System.Windows.Controls.TextBox>:

![Capture d’écran qui montre une boîte de texte ornée.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Comportement de rendu des ornements

Il est important de noter que les ornements n’incluent aucun comportement de rendu inhérent ; il appartient donc à l’implémenteur d’un ornement de vérifier son rendu. Une façon courante d’implémenter le <xref:System.Windows.UIElement.OnRender%2A> comportement de rendu <xref:System.Windows.Media.DrawingContext> est de remplacer la méthode et d’utiliser un ou plusieurs objets pour rendre les visuels de l’adorant au besoin (comme indiqué dans l’exemple ci-dessus).

> [!NOTE]
> Tout ce que vous placez dans la couche d’ornement s’affiche au dessus de tous les styles que vous avez définis. En d’autres termes, les ornements sont toujours visuellement en haut et ne peuvent pas être substitués à l’aide de l’ordre de plan.

## <a name="events-and-hit-testing"></a>Événements et test de positionnement

Les adorateurs reçoivent des événements <xref:System.Windows.FrameworkElement>d’entrée comme les autres .  Parce qu’un adorant a toujours un z-ordre plus élevé que l’élément qu’il orne, l’adorant reçoit des événements d’entrée (tels <xref:System.Windows.UIElement.Drop> que ou <xref:System.Windows.UIElement.MouseMove>) qui peuvent être destinés à l’élément orné sous-jacent.  Un ornement peut écouter certains événements d’entrée et les passer à l’élément orné sous-jacent en déclenchant à nouveau l’événement.

Pour permettre l’essai de frappe de passage des éléments <xref:System.Windows.UIElement.IsHitTestVisible%2A> sous un ornement, définissez la propriété d’essai de coup à **faux** sur l’adorant.  Pour plus d’informations sur les tests à succès, voir [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Ornementation d’un UIElement unique

Pour lier un adorant à un particulier, <xref:System.Windows.UIElement>suivez ces étapes:

1. Appelez la <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> méthode statique <xref:System.Windows.Documents.AdornerLayer> pour <xref:System.Windows.UIElement> obtenir un objet pour que le soit orné. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>marche vers le haut de <xref:System.Windows.UIElement>l’arbre visuel, commençant à la spécifiée, et renvoie la première couche d’ornement qu’il trouve. (Si aucune couche d’ornement n’est trouvée, la méthode retourne Null.)

2. Appelez <xref:System.Windows.Documents.AdornerLayer.Add%2A> la méthode pour lier <xref:System.Windows.UIElement>l’adorant à la cible .

 L’exemple suivant lie un SimpleCircleAdorner (voir ci-dessus) à un <xref:System.Windows.Controls.TextBox> *myTextBox*nommé :

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.

## <a name="adorning-the-children-of-a-panel"></a>Ornementation des enfants d’un panneau

Pour lier un adorant <xref:System.Windows.Controls.Panel>aux enfants d’un , suivez ces étapes:

1. Appelez `static` la <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> méthode pour trouver une couche d’ornement pour l’élément dont les enfants doivent être ornés.

2. Énumérer à travers les enfants de <xref:System.Windows.Documents.AdornerLayer.Add%2A> l’élément parent et appeler la méthode pour lier un ornement à chaque élément enfant.

L’exemple suivant lie un SimpleCircleAdorner (montré ci-dessus) aux enfants d’un <xref:System.Windows.Controls.StackPanel> *myStackPanel*nommé :

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Vue d’ensemble des formes et dessins de base dans WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Peinture avec des images, des dessins et des objets visuels](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Vue d'ensemble des objets Drawing](../graphics-multimedia/drawing-objects-overview.md)
- [Sujets comment se passer](adorners-how-to-topics.md)
