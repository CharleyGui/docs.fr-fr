---
title: Encre de rendu personnalisé
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: 9a62a16f4fa16cfe40bbf830de2255bea25f8d3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611983"
---
# <a name="custom-rendering-ink"></a>Encre de rendu personnalisé
Le <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriété d’un trait vous permet de spécifier l’apparence d’un trait, telles que sa taille, la couleur et la forme, mais il peut arriver que vous souhaitez personnaliser l’apparence au-delà de ce que <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> autoriser. Vous souhaiterez peut-être personnaliser l’apparence de l’encre en appliquant des effets tels qu’aérographe, peinture à l’huile et autres. Permet à Windows Presentation Foundation (WPF) vous permettent de personnaliser l’encre de rendu en implémentant un personnalisé <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> et <xref:System.Windows.Ink.Stroke> objet.  
  
 Cette rubrique contient les sous-sections suivantes :  
  
- [Architecture](#Architecture)  
  
- [Implémentation d’un renderer dynamique](#ImplementingADynamicRenderer)  
  
- [Implémentation de traits personnalisés](#ImplementingCustomStrokes)  
  
- [Implémentation d’un InkCanvas personnalisé](#ImplementingACustomInkCanvas)  
  
- [Conclusion](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architecture  
 Le rendu de l’encre se produit deux fois : quand un utilisateur écrit de l’encre sur une surface d’entrée manuscrite, et une fois que le trait a été ajouté à la surface d’entrée manuscrite. Le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> restitue l’encre lorsque l’utilisateur déplace le stylet sur le digitaliseur et le <xref:System.Windows.Ink.Stroke> est rendue une fois qu’il est ajouté à un élément.  
  
 Vous devez implémenter trois classes lors du rendu dynamique de l’encre.  
  
1. **DynamicRenderer**: Implémentez une classe qui dérive de <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ; Cette classe est spécialisé <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> qui restitue le trait comme il est dessiné. Le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> effectue le rendu sur un thread distinct, afin de la surface d’entrée manuscrite semble collecter l’encre même quand le thread d’interface (UI) applications utilisateur est bloqué. Pour plus d’informations sur le modèle de thread, consultez [Modèle de thread de l’encre](the-ink-threading-model.md). Pour personnaliser le rendu dynamique d’un trait, substituez le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> (méthode).  
  
2. **Trait**: Implémentez une classe qui dérive de <xref:System.Windows.Ink.Stroke> ; Cette classe est responsable du rendu statique de la <xref:System.Windows.Input.StylusPoint> données une fois qu’il a été converti en un <xref:System.Windows.Ink.Stroke> objet. Remplacer le <xref:System.Windows.Ink.Stroke.DrawCore%2A> pour s’assurer que le rendu statique du trait est cohérent avec le rendu dynamique.  
  
3. **InkCanvas :** Implémentez une classe qui dérive de <xref:System.Windows.Controls.InkCanvas> ; Affecter le personnalisé <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à la <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> propriété. Remplacer le <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> (méthode) et ajoutez un trait personnalisé à la <xref:System.Windows.Controls.InkCanvas.Strokes%2A> propriété. Cela garantit la cohérence de l’apparence de l’encre.  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>Implémentation d’un renderer dynamique  
 Bien que le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> classe est une partie standard de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plus effectuer un rendu spécialisé, vous devez créer un renderer dynamique personnalisé qui dérive de la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> et remplacer le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> (méthode).  
  
 L’exemple suivant montre un texte personnalisé <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> qui dessine l’encre avec un effet de pinceau de dégradé linéaire.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>Implémentation de traits personnalisés  
 Implémentez une classe qui dérive de <xref:System.Windows.Ink.Stroke> ; Cette classe est responsable du rendu <xref:System.Windows.Input.StylusPoint> données une fois qu’il a été converti en un <xref:System.Windows.Ink.Stroke> objet. Remplacer la <xref:System.Windows.Ink.Stroke.DrawCore%2A> classe pour effectuer le dessin proprement dit.  
  
 Votre classe Stroke peut également stocker des données personnalisées à l’aide de la <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> (méthode). Ces données sont stockées avec les données du trait quand elles sont rendues persistantes.  
  
 Le <xref:System.Windows.Ink.Stroke> classe peut également effectuer le test de positionnement. Vous pouvez également implémenter votre propre algorithme de test en remplaçant le <xref:System.Windows.Ink.Stroke.HitTest%2A> méthode dans la classe en cours.  
  
 Ce qui suit C# code illustre un personnalisé <xref:System.Windows.Ink.Stroke> classe restitue <xref:System.Windows.Input.StylusPoint> données sous la forme d’un trait en 3D.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>Implémentation d’un InkCanvas personnalisé  
 Le moyen le plus simple d’utiliser votre page Web personnalisée <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> et stroke consiste à implémenter une classe qui dérive de <xref:System.Windows.Controls.InkCanvas> et utilise ces classes. Le <xref:System.Windows.Controls.InkCanvas> a un <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> propriété qui spécifie comment le trait est affiché lorsque l’utilisateur le dessine.  
  
 Pour personnaliser le rendu traits sur un <xref:System.Windows.Controls.InkCanvas> procédez comme suit :  
  
- Créez une classe qui dérive de la <xref:System.Windows.Controls.InkCanvas>.  
  
- Affectez votre personnalisé <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à la <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> propriété.  
  
- Remplacez la méthode <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> . Dans cette méthode, supprimez le trait d’origine qui a été ajouté à InkCanvas. Ensuite, créez un trait personnalisé, ajoutez-le à la <xref:System.Windows.Controls.InkCanvas.Strokes%2A> propriété, puis appelez la classe de base avec un nouveau <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> qui contient le trait personnalisé.  
  
 Ce qui suit C# code illustre un personnalisé <xref:System.Windows.Controls.InkCanvas> classe qui utilise un personnalisé <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> et collecte des traits personnalisés.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Un <xref:System.Windows.Controls.InkCanvas> peut avoir plusieurs <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Vous pouvez ajouter plusieurs <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> des objets sur le <xref:System.Windows.Controls.InkCanvas> en les ajoutant à la <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusion  
 Vous pouvez personnaliser l’apparence de l’encre en dérivant vos propres <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, et <xref:System.Windows.Controls.InkCanvas> classes. Ensemble, ces classes garantissent que l’apparence du trait est cohérente quand l’utilisateur dessine le trait et après que celui-ci a été recueilli.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion avancée de l’encre](advanced-ink-handling.md)
