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
ms.openlocfilehash: 394318488b0afb8e043389e0abc3f51dce8604c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186295"
---
# <a name="creating-an-ink-input-control"></a>Création d'un contrôle d'entrée d'encre
Vous pouvez créer un contrôle personnalisé qui rend dynamiquement et statiquement l’encre. C’est-à-dire, rendre de l’encre comme un utilisateur tire un trait, provoquant l’encre à apparaître à "flux" à partir du stylo tablette, et l’encre d’affichage après qu’il est ajouté au contrôle, soit via le stylo tablette, collé à partir de la planche à clip, ou chargé à partir d’un fichier. Pour rendre dynamiquement l’encre, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>votre contrôle doit utiliser un . Pour rendre statiquement l’encre, vous devez remplacer<xref:System.Windows.UIElement.OnStylusDown%2A>les <xref:System.Windows.UIElement.OnStylusMove%2A>méthodes <xref:System.Windows.UIElement.OnStylusUp%2A>d’événement stylet ( , , et ) pour recueillir des <xref:System.Windows.Input.StylusPoint> données, créer des traits, et les ajouter à un <xref:System.Windows.Controls.InkPresenter> (qui rend l’encre sur le contrôle).  
  
 Cette rubrique contient les sous-sections suivantes :  
  
- [Comment : Recueillir des données sur le point de stylet et créer des aVC d’encre](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Comment : Activez votre contrôle pour accepter l’entrée de la souris](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Synthèse](#PuttingItTogether)  
  
- [Utilisation de plug-ins supplémentaires et dynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Conclusion](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Comment : Recueillir des données sur le point de stylet et créer des aVC d’encre  
 Pour créer un contrôle qui recueille et gère les coups d’encre faire ce qui suit:  
  
1. Dérivez une <xref:System.Windows.Controls.Control> classe ou l’une des classes dérivées de <xref:System.Windows.Controls.Control>, tels que <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Ajoutez <xref:System.Windows.Controls.InkPresenter> un à la <xref:System.Windows.Controls.ContentControl.Content%2A> classe et <xref:System.Windows.Controls.InkPresenter>définissez la propriété à la nouvelle .  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Attachez <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> de <xref:System.Windows.Controls.InkPresenter> la <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> à l’appelant <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> la <xref:System.Windows.UIElement.StylusPlugIns%2A> méthode, et ajoutez la à la collection. Cela permet <xref:System.Windows.Controls.InkPresenter> d’afficher l’encre que les données de point de stylet est collectée par votre contrôle.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Remplacez la méthode <xref:System.Windows.UIElement.OnStylusDown%2A> .  Dans cette méthode, capturer le stylet <xref:System.Windows.Input.Stylus.Capture%2A>avec un appel à . En capturant le stylet, votre contrôle <xref:System.Windows.UIElement.StylusMove> continuera <xref:System.Windows.UIElement.StylusUp> à recevoir et les événements même si le stylet quitte les limites du contrôle. Ce n’est pas strictement obligatoire, mais presque toujours souhaité pour une bonne expérience utilisateur. Créez un <xref:System.Windows.Input.StylusPointCollection> nouveau <xref:System.Windows.Input.StylusPoint> pour recueillir des données. Enfin, ajouter l’ensemble initial de <xref:System.Windows.Input.StylusPoint> données à la <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Remplacez <xref:System.Windows.UIElement.OnStylusMove%2A> la méthode <xref:System.Windows.Input.StylusPoint> et ajoutez <xref:System.Windows.Input.StylusPointCollection> les données à l’objet que vous avez créé plus tôt.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Remplacer la <xref:System.Windows.UIElement.OnStylusUp%2A> méthode et <xref:System.Windows.Ink.Stroke> créer <xref:System.Windows.Input.StylusPointCollection> un nouveau avec les données. Ajoutez le <xref:System.Windows.Ink.Stroke> nouveau que <xref:System.Windows.Controls.InkPresenter.Strokes%2A> vous <xref:System.Windows.Controls.InkPresenter> avez créé à la collection de la capture et de la capture de stylet de libération.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Comment : Activez votre contrôle pour accepter l’entrée de la souris  
 Si vous ajoutez le contrôle précédent à votre application, l’exécutez et utilisez la souris comme dispositif d’entrée, vous remarquerez que les traits ne sont pas persistants. Pour persister les traits lorsque la souris est utilisée comme dispositif d’entrée faire ce qui suit:  
  
1. Remplacer le <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> et créer <xref:System.Windows.Input.StylusPointCollection> un nouveau Obtenir la position de <xref:System.Windows.Input.StylusPoint> la souris lorsque l’événement s’est produit et de créer une utilisation des données de point et d’ajouter le <xref:System.Windows.Input.StylusPoint> . <xref:System.Windows.Input.StylusPointCollection>  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Remplacez la méthode <xref:System.Windows.UIElement.OnMouseMove%2A> . Obtenez la position de la souris lorsque <xref:System.Windows.Input.StylusPoint> l’événement s’est produit et créez une utilisation des données ponctuelles.  Ajoutez <xref:System.Windows.Input.StylusPoint> <xref:System.Windows.Input.StylusPointCollection> l’objet que vous avez créé plus tôt.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Remplacez la méthode <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> .  Créez un <xref:System.Windows.Ink.Stroke> nouveau <xref:System.Windows.Input.StylusPointCollection> avec les données, et ajoutez le nouveau <xref:System.Windows.Ink.Stroke> que vous avez créé à la <xref:System.Windows.Controls.InkPresenter.Strokes%2A> collection de la <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>
## <a name="putting-it-together"></a>Synthèse  
 L’exemple suivant est un contrôle personnalisé qui recueille l’encre lorsque l’utilisateur utilise la souris ou le stylo.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Utilisation de plug-ins supplémentaires et dynamicRenderers  
 Comme les InkCanvas, votre contrôle <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personnalisé <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> peut avoir des objets personnalisés et supplémentaires. Ajoutez-les <xref:System.Windows.UIElement.StylusPlugIns%2A> à la collection. L’ordre <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> des objets <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> dans l’affecte l’apparence de l’encre quand il est rendu. Supposons que <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> `dynamicRenderer` vous avez <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> `translatePlugin` un appelé et une coutume appelée qui compense l’encre du stylo tablette. Si `translatePlugin` est <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> le <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>premier `dynamicRenderer` dans le , et est le second, l’encre qui "flux" sera compensée que l’utilisateur déplace le stylo. Si `dynamicRenderer` elle est `translatePlugin` la première, et est deuxième, l’encre ne sera pas compensée jusqu’à ce que l’utilisateur soulève le stylo.  
  
<a name="AdvancedInkHandling_Conclusion"></a>
## <a name="conclusion"></a>Conclusion  
 Vous pouvez créer un contrôle qui recueille et rend l’encre en dominant les méthodes d’événement stylet. En créant votre propre contrôle, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> en dérivant vos <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>propres classes, et en les insérant le dans , vous pouvez implémenter pratiquement n’importe quel comportement imaginable avec l’encre numérique. Vous avez accès <xref:System.Windows.Input.StylusPoint> aux données au fur et à <xref:System.Windows.Input.Stylus> mesure qu’elles sont générées, ce qui vous donne la possibilité de personnaliser l’entrée et de les rendre sur l’écran, le cas échéant pour votre application. Parce que vous avez un <xref:System.Windows.Input.StylusPoint> accès de si faible niveau aux données, vous pouvez implémenter la collecte d’encre et les rendre avec des performances optimales pour votre application.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion avancée de l'encre](advanced-ink-handling.md)
- [Accès et manipulation de l’entrée du stylo](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
