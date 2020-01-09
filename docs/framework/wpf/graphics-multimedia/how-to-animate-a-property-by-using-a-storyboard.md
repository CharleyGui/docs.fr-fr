---
title: "Comment : animer une propriété à l'aide d'un storyboard"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: 6cfce9a5b070a23ed9ac03473888bf572b61393b
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559636"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Comment : animer une propriété à l'aide d'un storyboard
Cet exemple montre comment utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour animer des propriétés. Pour animer une propriété à l’aide d’un <xref:System.Windows.Media.Animation.Storyboard>, créez une animation pour chaque propriété que vous souhaitez animer et créez également une <xref:System.Windows.Media.Animation.Storyboard> pour contenir les animations.  
  
 Le type de propriété détermine le type d’animation à utiliser. Par exemple, pour animer une propriété qui accepte <xref:System.Double> valeurs, utilisez une <xref:System.Windows.Media.Animation.DoubleAnimation>. Les propriétés jointes <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> spécifient l’objet et la propriété auxquels l’animation est appliquée.  
  
 Pour démarrer une table de montage séquentiel dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], utilisez une action <xref:System.Windows.Media.Animation.BeginStoryboard> et une <xref:System.Windows.EventTrigger>. L' <xref:System.Windows.EventTrigger> commence la <xref:System.Windows.Media.Animation.BeginStoryboard> action lorsque l’événement spécifié par sa propriété <xref:System.Windows.EventTrigger.RoutedEvent%2A> se produit. L’action <xref:System.Windows.Media.Animation.BeginStoryboard> démarre le <xref:System.Windows.Media.Animation.Storyboard>.  
  
 L’exemple suivant utilise des objets <xref:System.Windows.Media.Animation.Storyboard> pour animer deux contrôles <xref:System.Windows.Controls.Button>. Pour que la taille du premier bouton change, son <xref:System.Windows.FrameworkElement.Width%2A> est animée. Pour que le deuxième bouton change de couleur, la propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A> du <xref:System.Windows.Media.SolidColorBrush> est utilisée pour définir le <xref:System.Windows.Controls.Control.Background%2A> du bouton animé.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Bien que les animations puissent cibler à la fois un objet <xref:System.Windows.FrameworkElement>, tel qu’un <xref:System.Windows.Controls.Control> ou <xref:System.Windows.Controls.Panel>, et un objet <xref:System.Windows.Freezable>, tel qu’un <xref:System.Windows.Media.Brush> ou un <xref:System.Windows.Media.Transform>, seuls les éléments Framework ont une propriété <xref:System.Windows.FrameworkElement.Name%2A>. Pour attribuer un nom à un objet Freezable afin qu’il puisse être ciblé par une animation, utilisez la [Directive x:Name](../../../desktop-wpf/xaml-services/xname-directive.md), comme illustré dans l’exemple précédent.  
  
 Si vous utilisez du code, vous devez créer une <xref:System.Windows.NameScope> pour une <xref:System.Windows.FrameworkElement> et enregistrer les noms des objets à animer avec cette <xref:System.Windows.FrameworkElement>. Pour démarrer les animations dans le code, utilisez une action <xref:System.Windows.Media.Animation.BeginStoryboard> avec une <xref:System.Windows.EventTrigger>. Si vous le souhaitez, vous pouvez utiliser un gestionnaire d’événements et la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> de <xref:System.Windows.Media.Animation.Storyboard>. L'exemple suivant illustre l'utilisation de la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Pour plus d’informations sur l’animation et les tables de montage séquentiel, consultez [Vue d’ensemble de l’animation](animation-overview.md).  
  
 Si vous utilisez du code, vous n’êtes pas limité à l’utilisation de <xref:System.Windows.Media.Animation.Storyboard> objets pour animer des propriétés. Pour obtenir d’autres informations et exemples, consultez [Comment : animer une propriété sans utiliser de storyboard](how-to-animate-a-property-without-using-a-storyboard.md) et [Comment : animer une propriété à l’aide d’un AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
