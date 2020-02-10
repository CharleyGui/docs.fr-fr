---
title: Création d'un contrôle d'entrée d'encre
ms.date: 03/30/2017
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
ms.openlocfilehash: 98b2abf813a232e36b80683254174b12b97659bb
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095214"
---
# <a name="creating-an-ink-input-control"></a>Création d'un contrôle d'entrée d'encre
Vous pouvez créer un contrôle personnalisé qui restitue de manière dynamique et statique l’encre. Autrement dit, le rendu de l’encre en tant qu’utilisateur trace un trait, provoquant l’affichage de l’encre sur « Flow » du stylet, et l’affichage de l’encre après son ajout au contrôle, via le stylet, collé à partir du presse-papiers ou chargé à partir d’un fichier. Pour restituer l’encre de manière dynamique, votre contrôle doit utiliser un <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Pour restituer de manière statique l’encre, vous devez substituer les méthodes d’événement de stylet (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>et <xref:System.Windows.UIElement.OnStylusUp%2A>) pour collecter <xref:System.Windows.Input.StylusPoint> données, créer des traits et les ajouter à un <xref:System.Windows.Controls.InkPresenter> (qui restitue l’encre sur le contrôle).  
  
 Cette rubrique contient les sous-sections suivantes :  
  
- [Comment : collecter des données de point de stylet et créer des traits d’encre](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Comment : activer votre contrôle pour accepter l’entrée de la souris](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Rassembler](#PuttingItTogether)  
  
- [Utilisation de plug-ins et DynamicRenderers supplémentaires](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Conclusion](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Comment : collecter des données de point de stylet et créer des traits d’encre  
 Pour créer un contrôle qui recueille et gère les traits d’encre, procédez comme suit :  
  
1. Dérivez une classe de <xref:System.Windows.Controls.Control> ou l’une des classes dérivées de <xref:System.Windows.Controls.Control>, comme <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Ajoutez un <xref:System.Windows.Controls.InkPresenter> à la classe et affectez à la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> la nouvelle <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Attachez le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> du <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> au <xref:System.Windows.Controls.InkPresenter> en appelant la méthode <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>, puis ajoutez le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à la collection <xref:System.Windows.UIElement.StylusPlugIns%2A>. Cela permet à l' <xref:System.Windows.Controls.InkPresenter> d’afficher l’encre au fur et à mesure que les données du point de stylet sont collectées par votre contrôle.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Remplacez la méthode <xref:System.Windows.UIElement.OnStylusDown%2A> .  Dans cette méthode, capturez le stylet à l’aide d’un appel à <xref:System.Windows.Input.Stylus.Capture%2A>. En capturant le stylet, votre contrôle doit continuer à recevoir des événements <xref:System.Windows.UIElement.StylusMove> et <xref:System.Windows.UIElement.StylusUp> même si le stylet quitte les limites du contrôle. Ce n’est pas strictement obligatoire, mais il est presque toujours souhaitable pour une expérience utilisateur optimale. Créez un <xref:System.Windows.Input.StylusPointCollection> pour collecter des données <xref:System.Windows.Input.StylusPoint>. Enfin, ajoutez l’ensemble initial de <xref:System.Windows.Input.StylusPoint> données au <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Substituez la méthode <xref:System.Windows.UIElement.OnStylusMove%2A> et ajoutez les données <xref:System.Windows.Input.StylusPoint> à l’objet <xref:System.Windows.Input.StylusPointCollection> que vous avez créé précédemment.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Substituez la méthode <xref:System.Windows.UIElement.OnStylusUp%2A> et créez un nouveau <xref:System.Windows.Ink.Stroke> avec les données de <xref:System.Windows.Input.StylusPointCollection>. Ajoutez le nouvel <xref:System.Windows.Ink.Stroke> que vous avez créé à la collection de <xref:System.Windows.Controls.InkPresenter.Strokes%2A> du <xref:System.Windows.Controls.InkPresenter> et lancez la capture du stylet.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Comment : activer votre contrôle pour accepter l’entrée de la souris  
 Si vous ajoutez le contrôle précédent à votre application, que vous l’exécutez et que vous utilisez la souris comme périphérique d’entrée, vous remarquerez que les traits ne sont pas conservés. Pour conserver les traits lorsque la souris est utilisée comme périphérique d’entrée, procédez comme suit :  
  
1. Substituez le <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> et créez un nouvel <xref:System.Windows.Input.StylusPointCollection> obtenir la position de la souris lorsque l’événement s’est produit et créez un <xref:System.Windows.Input.StylusPoint> à l’aide des données point et ajoutez le <xref:System.Windows.Input.StylusPoint> à la <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Remplacez la méthode <xref:System.Windows.UIElement.OnMouseMove%2A> . Obtient la position de la souris lorsque l’événement s’est produit et crée un <xref:System.Windows.Input.StylusPoint> à l’aide des données point.  Ajoutez le <xref:System.Windows.Input.StylusPoint> à l’objet <xref:System.Windows.Input.StylusPointCollection> que vous avez créé précédemment.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Remplacez la méthode <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> .  Créez un <xref:System.Windows.Ink.Stroke> avec les données <xref:System.Windows.Input.StylusPointCollection>, puis ajoutez le nouveau <xref:System.Windows.Ink.Stroke> que vous avez créé à la collection <xref:System.Windows.Controls.InkPresenter.Strokes%2A> du <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Rassembler  
 L’exemple suivant est un contrôle personnalisé qui collecte l’encre lorsque l’utilisateur utilise la souris ou le stylet.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Utilisation de plug-ins et DynamicRenderers supplémentaires  
 À l’instar de l’InkCanvas, votre contrôle personnalisé peut avoir des <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personnalisées et des objets <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> supplémentaires. Ajoutez-les à la collection <xref:System.Windows.UIElement.StylusPlugIns%2A>. L’ordre des objets <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dans le <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> affecte l’apparence de l’encre lorsqu’il est rendu. Supposons que vous avez une <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> appelée `dynamicRenderer` et un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personnalisé appelé `translatePlugin` qui décale l’encre du stylet. Si `translatePlugin` est le premier <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> du <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>et `dynamicRenderer` est le second, l’encre « flows » sera décalée lorsque l’utilisateur déplace le stylet. Si `dynamicRenderer` est en premier, et que `translatePlugin` est Deuxièmement, l’encre n’est pas décalée jusqu’à ce que l’utilisateur soulève le stylet.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Conclusion  
 Vous pouvez créer un contrôle qui collecte et restitue l’encre en substituant les méthodes d’événement de stylet. En créant votre propre contrôle, en dérivant vos propres classes <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>, et en les insérant dans <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, vous pouvez implémenter pratiquement n’importe quel comportement imaginaire avec l’encre numérique. Vous avez accès aux données de <xref:System.Windows.Input.StylusPoint> lors de leur génération, ce qui vous donne la possibilité de personnaliser <xref:System.Windows.Input.Stylus> entrée et de la rendre sur l’écran en fonction de votre application. Étant donné que vous disposez d’un accès de bas niveau aux données <xref:System.Windows.Input.StylusPoint>, vous pouvez implémenter la collecte d’encre et l’afficher avec des performances optimales pour votre application.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion avancée de l’encre](advanced-ink-handling.md)
- [Accès et manipulation de l’entrée de stylet](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
