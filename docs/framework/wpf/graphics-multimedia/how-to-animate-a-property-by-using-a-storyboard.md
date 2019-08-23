---
title: 'Procédure : Animer une propriété à l’aide d’une table de montage séquentiel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: a7a2656d84d37d3e2726df009a07ccf29661df07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963040"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Procédure : Animer une propriété à l’aide d’une table de montage séquentiel
Cet exemple montre comment utiliser <xref:System.Windows.Media.Animation.Storyboard> pour animer des propriétés. Pour animer une propriété à l' <xref:System.Windows.Media.Animation.Storyboard>aide d’un, créez une animation pour chaque propriété que vous souhaitez animer et <xref:System.Windows.Media.Animation.Storyboard> créez également un pour contenir les animations.  
  
 Le type de propriété détermine le type d’animation à utiliser. Par exemple, pour animer une propriété qui <xref:System.Double> accepte des valeurs, <xref:System.Windows.Media.Animation.DoubleAnimation>utilisez. Les <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriétés <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> jointes et spécifient l’objet et la propriété auxquels l’animation est appliquée.  
  
 Pour démarrer une table de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]montage séquentiel dans <xref:System.Windows.Media.Animation.BeginStoryboard> , utilisez une <xref:System.Windows.EventTrigger>action et un. Le <xref:System.Windows.EventTrigger> commence l' <xref:System.Windows.Media.Animation.BeginStoryboard> action lorsque l’événement spécifié par sa <xref:System.Windows.EventTrigger.RoutedEvent%2A> propriété se produit. L' <xref:System.Windows.Media.Animation.BeginStoryboard> action<xref:System.Windows.Media.Animation.Storyboard>démarre.  
  
 L’exemple suivant utilise <xref:System.Windows.Media.Animation.Storyboard> des objets pour animer deux <xref:System.Windows.Controls.Button> contrôles. Pour que la taille du premier bouton change, son <xref:System.Windows.FrameworkElement.Width%2A> est animé. Pour que le deuxième bouton change de couleur, <xref:System.Windows.Media.SolidColorBrush.Color%2A> la propriété <xref:System.Windows.Media.SolidColorBrush> du est utilisée pour définir le <xref:System.Windows.Controls.Control.Background%2A> du bouton animé.  
  
## <a name="example"></a>Exemples  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Bien que les animations puissent cibler <xref:System.Windows.FrameworkElement> à la fois un objet <xref:System.Windows.Controls.Control> , <xref:System.Windows.Controls.Panel>tel qu’un <xref:System.Windows.Freezable> objet ou, et un <xref:System.Windows.Media.Brush> objet <xref:System.Windows.Media.Transform>, tel que ou, seuls <xref:System.Windows.FrameworkElement.Name%2A> les éléments de l’infrastructure ont une propriété. Pour attribuer un nom à un objet Freezable afin qu’il puisse être ciblé par une animation, utilisez la [Directive x:Name](../../xaml-services/x-name-directive.md), comme illustré dans l’exemple précédent.  
  
 Si vous utilisez du code, vous devez créer <xref:System.Windows.NameScope> un pour <xref:System.Windows.FrameworkElement> un et inscrire les noms des objets à animer avec <xref:System.Windows.FrameworkElement>celui-ci. Pour démarrer les animations dans le code, utilisez <xref:System.Windows.Media.Animation.BeginStoryboard> une action avec <xref:System.Windows.EventTrigger>un. Si vous le souhaitez, vous pouvez utiliser un gestionnaire d' <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> événements et <xref:System.Windows.Media.Animation.Storyboard>la méthode de. L'exemple suivant illustre l'utilisation de la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Pour plus d’informations sur l’animation et les tables de montage séquentiel, consultez [Vue d’ensemble de l’animation](animation-overview.md).  
  
 Si vous utilisez du code, vous n’êtes pas limité <xref:System.Windows.Media.Animation.Storyboard> à l’utilisation d’objets pour animer des propriétés. Pour obtenir d’autres informations et exemples, consultez [Comment : animer une propriété sans utiliser de storyboard](how-to-animate-a-property-without-using-a-storyboard.md) et [Comment : animer une propriété à l’aide d’un AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
