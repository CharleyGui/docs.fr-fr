---
title: 'Procédure : Définir une propriété après l’avoir animée avec une table de montage séquentiel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 593d3fcefe3bb81518d0886afde82f9a172874ba
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912383"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>Procédure : Définir une propriété après l’avoir animée avec une table de montage séquentiel
Dans certains cas, il peut sembler que vous ne pouvez pas modifier la valeur d’une propriété après que qu’elle a été animée.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un <xref:System.Windows.Media.Animation.Storyboard> est utilisé pour animer la couleur d’un <xref:System.Windows.Media.SolidColorBrush>. La table de montage séquentiel est déclenchée lorsque le bouton est activé. Le <xref:System.Windows.Media.Animation.Timeline.Completed> événement est géré afin que le programme est informé lorsque le <xref:System.Windows.Media.Animation.ColorAnimation> se termine.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>Exemple  
 Une fois la <xref:System.Windows.Media.Animation.ColorAnimation> terminée, le programme tente de modifier la couleur du pinceau en bleu.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 Le code précédent ne semble pas faire quelque chose : le pinceau reste jaune, qui est la valeur fournie par le <xref:System.Windows.Media.Animation.ColorAnimation> qui anime le pinceau. La valeur de propriété sous-jacente (la valeur de base) est réellement modifiée bleu. Toutefois, la valeur effective, ou actuelle, reste jaune, car le <xref:System.Windows.Media.Animation.ColorAnimation> remplace toujours la valeur de base. Si vous souhaitez que la valeur de base soit à la valeur effective nouveau, vous devez arrêter l’animation d’influencer la propriété. Il existe trois façons de le faire avec des animations de storyboard :  
  
- Définir l’animation <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
- Supprimer l’ensemble du Storyboard.  
  
- Supprimez l’animation de la propriété individuelle.  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>FillBehavior (propriété) de l’animation la valeur Stop  
 En définissant <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> à <xref:System.Windows.Media.Animation.FillBehavior.Stop>, vous dites à l’animation de cesser d’affecter sa propriété cible après avoir atteint la fin de sa période active.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>Supprimer l’ensemble du storyboard  
 En utilisant un <xref:System.Windows.Media.Animation.RemoveStoryboard> déclencheur ou la <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> (méthode), que vous demandez aux animations de storyboard de cesser d’affecter leurs propriétés cibles. La différence entre cette approche et en définissant le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété est que vous pouvez supprimer la table de montage séquentiel à tout moment, tandis que le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété n’a d’effet que lorsque l’animation atteint la fin de sa période active.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>Supprimer une animation d’une propriété individuelle  
 Une autre technique pour empêcher une animation d’affecter une propriété consiste à utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> méthode de l’objet en cours d’animation. Spécifiez la propriété animée comme premier paramètre et `null` en tant que la seconde.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Cette technique fonctionne également pour les animations table de montage séquentiel.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md)
