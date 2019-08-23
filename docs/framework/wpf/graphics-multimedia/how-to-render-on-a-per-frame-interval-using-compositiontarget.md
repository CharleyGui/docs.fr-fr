---
title: 'Procédure : Effectuer une restitution par intervalle de trame à l’aide de CompositionTarget'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 8864204ccdd1e860cc910dfe8baa2f25edfb2fcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956981"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Procédure : Effectuer une restitution par intervalle de trame à l’aide de CompositionTarget
Le moteur d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit de nombreuses fonctionnalités qui permettent de créer une animation à partir d’une trame. Il existe cependant des scénarios d’application dans lesquels vous devez affiner le rendu trame par trame. L' <xref:System.Windows.Media.CompositionTarget> objet permet de créer des animations personnalisées basées sur un rappel par image.  
  
 <xref:System.Windows.Media.CompositionTarget>est une classe statique qui représente la surface d’affichage sur laquelle votre application est dessinée. L' <xref:System.Windows.Media.CompositionTarget.Rendering> événement est déclenché chaque fois que la scène de l’application est dessinée. La fréquence d’images de rendu représente le nombre de fois que la scène est dessinée par seconde.  
  
> [!NOTE]
> Pour obtenir un exemple de code <xref:System.Windows.Media.CompositionTarget>complet utilisant, consultez [utilisation de l’exemple CompositionTarget](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Exemple  
 L' <xref:System.Windows.Media.CompositionTarget.Rendering> événement se déclenche pendant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le processus de rendu. L’exemple suivant montre comment inscrire un <xref:System.EventHandler> délégué à la méthode statique <xref:System.Windows.Media.CompositionTarget.Rendering> sur. <xref:System.Windows.Media.CompositionTarget>  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Vous pouvez utiliser la méthode de votre gestionnaire d’événements de rendu pour créer un contenu de dessin personnalisé. Cette méthode de gestionnaire d’événements est appelée une fois par image. Chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l’arborescence visuelle sur le graphique de la scène de composition, votre méthode de gestionnaire d’événements est appelée. En outre, si les modifications apportées à l’arborescence visuelle forcent les mises à jour sur le graphique de la scène de composition, votre méthode de gestionnaire d’événements est également appelée. Notez que votre méthode de gestionnaire d’événements est appelée une fois la disposition calculée. Vous pouvez cependant modifier la disposition dans votre méthode de gestionnaire d’événements, de sorte que cette disposition soit calculée avant le rendu.  
  
 L’exemple suivant montre comment vous pouvez fournir un dessin personnalisé dans <xref:System.Windows.Media.CompositionTarget> une méthode de gestionnaire d’événements. Dans ce cas, la couleur d’arrière- <xref:System.Windows.Controls.Canvas> plan de est dessinée avec une valeur de couleur en fonction de la position de la coordonnée de la souris. Si vous déplacez la souris à l' <xref:System.Windows.Controls.Canvas>intérieur du, sa couleur d’arrière-plan change. En outre, la fréquence d’images moyenne est calculée en fonction du temps écoulé actuel et du nombre total de trames rendues.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Vous pouvez voir que votre dessin personnalisé s’exécute à des vitesses différentes selon l’ordinateur utilisé. En effet, votre dessin personnalisé est dépendant de la fréquence d’images. En fonction du système que vous exécutez et de la charge de travail de ce système <xref:System.Windows.Media.CompositionTarget.Rendering> , l’événement peut être appelé un nombre différent de fois par seconde. Pour savoir comment déterminer les capacités et les performances du matériel graphique pour un appareil qui exécute une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez la page [Couches de rendu graphiques](../advanced/graphics-rendering-tiers.md).  
  
 L’ajout ou la suppression <xref:System.EventHandler> d’un délégué de rendu pendant le déclenchement de l’événement est retardé jusqu’à la fin du déclenchement de l’événement. Cela est cohérent avec les <xref:System.MulticastDelegate>événements basés sur la façon dont le Common Language Runtime (CLR) gère les événements basés sur la méthode. Notez également que les événements de rendu ne sont pas forcément appelés dans un ordre particulier. Si vous avez plusieurs <xref:System.EventHandler> délégués qui reposent sur un ordre particulier, vous devez inscrire <xref:System.Windows.Media.CompositionTarget.Rendering> un événement unique et multiplexer les délégués dans l’ordre approprié.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.CompositionTarget>
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
