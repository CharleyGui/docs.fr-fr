---
title: 'Procédure : Animer l’opacité d’un élément ou d’un pinceau'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 2f18861eb18f81b631245d1d933b7acb1b3e0e42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950509"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Procédure : Animer l’opacité d’un élément ou d’un pinceau
Pour faire apparaître et disparaître un élément de l’infrastructure, vous pouvez animer sa <xref:System.Windows.UIElement.Opacity%2A> propriété ou vous pouvez animer <xref:System.Windows.Media.Brush.Opacity%2A> la propriété des <xref:System.Windows.Media.Brush> pinceaux (ou) utilisés pour le peindre. L’animation de l’opacité de l’élément le rend et les enfants se estompent et sont hors de la vue, mais l’animation du pinceau utilisé pour peindre l’élément vous permet d’être plus sélectif quant à la partie de l’élément qui apparaît en fondu. Par exemple, vous pouvez animer l’opacité d’un pinceau utilisé pour peindre l’arrière-plan d’un bouton. Cela entraînerait un fondu de l’arrière-plan du bouton, tout en laissant son texte entièrement opaque.  
  
> [!NOTE]
> L' <xref:System.Windows.Media.Brush.Opacity%2A> animation du d’un <xref:System.Windows.Media.Brush> offre des avantages en matière de performances <xref:System.Windows.UIElement.Opacity%2A> par rapport à l’animation de la propriété d’un élément.  
  
 Dans l’exemple suivant, deux boutons sont animés de sorte qu’ils apparaissent et s’affichent en fondu. L’opacité de la première <xref:System.Windows.Controls.Button> est `1.0` animée de jusqu' `0.0` à <xref:System.Windows.Media.Animation.Timeline.Duration%2A> cinq secondes. Le deuxième bouton est également animé, mais l’opacité du SolidColorBrush utilisé pour peindre son <xref:System.Windows.Controls.Control.Background%2A> est animée au lieu de l’opacité du bouton entier. Lorsque l’exemple est exécuté, le premier bouton apparaît complètement en fondu dans et hors de l’affichage, tandis que seul l’arrière-plan du deuxième bouton apparaît et disparaît en fondu. Son texte et sa bordure restent entièrement opaques.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 Le code a été omis de cet exemple. L’exemple complet montre également comment animer l’opacité d’un <xref:System.Windows.Media.Color> dans un <xref:System.Windows.Media.LinearGradientBrush>.  Pour obtenir l’exemple complet, consultez l' [exemple animation de l’opacité d’un élément](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation).
