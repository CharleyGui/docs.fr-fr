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
ms.openlocfilehash: 3cf0d98c40e71a380b218c76d6e52d00cdd05342
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186348"
---
# <a name="custom-rendering-ink"></a>Encre de rendu personnalisé
La <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriété d’un accident vasculaire cérébral vous permet de spécifier l’apparence d’un accident vasculaire cérébral, <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> comme sa taille, sa couleur et sa forme, mais il peut y avoir des moments où vous voulez personnaliser l’apparence au-delà de ce que vous autorisez. Vous souhaiterez peut-être personnaliser l’apparence de l’encre en appliquant des effets tels qu’aérographe, peinture à l’huile et autres. La Windows Presentation Foundation (WPF) vous permet de rendre <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Ink.Stroke> l’encre personnalisée en implémentant une coutume et un objet.  
  
 Cette rubrique contient les sous-sections suivantes :  
  
- [Architecture](#Architecture)  
  
- [Implémentation d’un renderer dynamique](#ImplementingADynamicRenderer)  
  
- [Implémentation de traits personnalisés](#ImplementingCustomStrokes)  
  
- [Implémentation d’un InkCanvas personnalisé](#ImplementingACustomInkCanvas)  
  
- [Conclusion](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Architecture  
 Le rendu de l’encre se produit deux fois : quand un utilisateur écrit de l’encre sur une surface d’entrée manuscrite, et une fois que le trait a été ajouté à la surface d’entrée manuscrite. Le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> rend l’encre lorsque l’utilisateur déplace le stylo <xref:System.Windows.Ink.Stroke> tablette sur le numériseur, et le rendu lui-même une fois qu’il est ajouté à un élément.  
  
 Vous devez implémenter trois classes lors du rendu dynamique de l’encre.  
  
1. **DynamicRenderer**: Mettre en œuvre une classe qui dérive de <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Cette classe est <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> spécialisée qui rend le trait tel qu’il est tiré. Le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> rendu sur un thread séparé, de sorte que la surface d’encre semble recueillir de l’encre même lorsque l’interface utilisateur d’application (interface utilisateur) thread est bloqué. Pour plus d’informations sur le modèle de thread, consultez [Modèle de thread de l’encre](the-ink-threading-model.md). Pour personnaliser dynamiquement le rendu d’un trait, remplacez la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> méthode.  
  
2. **Stroke**: Mettre en œuvre une classe qui dérive de <xref:System.Windows.Ink.Stroke>. Cette classe est responsable du <xref:System.Windows.Input.StylusPoint> rendu statique des données après <xref:System.Windows.Ink.Stroke> qu’elles ont été converties en objet. Remplacer la <xref:System.Windows.Ink.Stroke.DrawCore%2A> méthode pour s’assurer que le rendu statique de la course est compatible avec le rendu dynamique.  
  
3. **EncreCanvas:** Mettre en œuvre <xref:System.Windows.Controls.InkCanvas>une classe qui dérive de . Assignez les <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personnalisés à la <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> propriété. Remplacer la <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> méthode et ajouter un <xref:System.Windows.Controls.InkCanvas.Strokes%2A> coup personnalisé à la propriété. Cela garantit la cohérence de l’apparence de l’encre.  
  
<a name="ImplementingADynamicRenderer"></a>
## <a name="implementing-a-dynamic-renderer"></a>Implémentation d’un renderer dynamique  
 Bien <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> que la classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]soit une partie standard de , pour effectuer un rendu plus <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> spécialisé, vous <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> devez créer un rendu dynamique personnalisé qui dérive de la méthode et l’emporte sur la méthode.  
  
 L’exemple suivant montre <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> une personnalisation qui attire l’encre avec un effet de brosse de gradient linéaire.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>
## <a name="implementing-custom-strokes"></a>Implémentation de traits personnalisés  
 Implémentez une classe qui dérive de <xref:System.Windows.Ink.Stroke> ; Cette classe est responsable <xref:System.Windows.Input.StylusPoint> du rendu des données <xref:System.Windows.Ink.Stroke> après qu’elles ont été converties en objet. Remplacer la <xref:System.Windows.Ink.Stroke.DrawCore%2A> classe pour faire le dessin réel.  
  
 Votre classe Stroke peut également stocker <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> des données personnalisées en utilisant la méthode. Ces données sont stockées avec les données du trait quand elles sont rendues persistantes.  
  
 La <xref:System.Windows.Ink.Stroke> classe peut également effectuer des tests à succès. Vous pouvez également implémenter votre propre <xref:System.Windows.Ink.Stroke.HitTest%2A> algorithme de test à succès en l’emporteant sur la méthode dans la classe actuelle.  
  
 Le code CMD suivant <xref:System.Windows.Ink.Stroke> démontre une <xref:System.Windows.Input.StylusPoint> classe personnalisée qui rend les données comme un AVC 3D.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>
## <a name="implementing-a-custom-inkcanvas"></a>Implémentation d’un InkCanvas personnalisé  
 La façon la plus <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> simple d’utiliser votre personnalisé et <xref:System.Windows.Controls.InkCanvas> aVC est de mettre en œuvre une classe qui dérive et utilise ces classes. Le <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> une propriété qui spécifie comment le coup est rendu lorsque l’utilisateur est le dessin.  
  
 Pour rendre les traits personnalisés sur un <xref:System.Windows.Controls.InkCanvas> faire ce qui suit :  
  
- Créer une classe qui <xref:System.Windows.Controls.InkCanvas>dérive de la .  
  
- Affectez votre <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personnalisé <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> à la propriété.  
  
- Remplacez la méthode <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> . Dans cette méthode, supprimez le trait d’origine qui a été ajouté à InkCanvas. Ensuite, créez un trait personnalisé, ajoutez-le à la <xref:System.Windows.Controls.InkCanvas.Strokes%2A> <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> propriété et appelez la classe de base avec un nouveau qui contient le trait personnalisé.  
  
 Le code CMD suivant <xref:System.Windows.Controls.InkCanvas> démontre une classe <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personnalisée qui utilise un personnalisé et recueille des traits personnalisés.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Un <xref:System.Windows.Controls.InkCanvas> peut avoir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>plus d’un . Vous pouvez <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ajouter plusieurs <xref:System.Windows.Controls.InkCanvas> objets à <xref:System.Windows.UIElement.StylusPlugIns%2A> la en les ajoutant à la propriété.  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Conclusion  
 Vous pouvez personnaliser l’apparence de l’encre <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Ink.Stroke>en <xref:System.Windows.Controls.InkCanvas> dérivant votre propre, , et les classes. Ensemble, ces classes garantissent que l’apparence du trait est cohérente quand l’utilisateur dessine le trait et après que celui-ci a été recueilli.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion avancée de l'encre](advanced-ink-handling.md)
