---
title: Interception d'entrée à partir du stylet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 17cf42a9d6d94d6ea12399561af5647df3b4d8c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181916"
---
# <a name="intercepting-input-from-the-stylus"></a>Interception d'entrée à partir du stylet
L’architecture <xref:System.Windows.Input.StylusPlugIns> fournit un mécanisme pour mettre <xref:System.Windows.Input.Stylus> en œuvre un <xref:System.Windows.Ink.Stroke> contrôle de bas niveau sur l’entrée et la création d’objets d’encre numérique. La <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classe fournit un mécanisme pour vous permettre d’implémenter un comportement personnalisé et de l’appliquer au flux de données provenant du dispositif de stylet pour les performances optimales.  
  
 Cette rubrique contient les sous-sections suivantes :  
  
- [Architecture](#Architecture)  
  
- [Mise en œuvre de Stylus Plug-ins](#ImplementingStylusPlugins)  
  
- [Ajout de votre plug-in à un InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Conclusion](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Architecture  
 L’évolution <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> des API [StylusInput,](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) décrites dans [Accessing and Manipulating Pen Input](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).  
  
 Chacun <xref:System.Windows.UIElement> a <xref:System.Windows.UIElement.StylusPlugIns%2A> une propriété <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>qui est un . Vous pouvez <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ajouter un à <xref:System.Windows.UIElement.StylusPlugIns%2A> la <xref:System.Windows.Input.StylusPoint> propriété d’un élément pour manipuler les données au fur et à mesure qu’elles sont générées. <xref:System.Windows.Input.StylusPoint>toutes les propriétés prises en charge par <xref:System.Windows.Input.StylusPoint.X%2A> le <xref:System.Windows.Input.StylusPoint.Y%2A> numériseur <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> du système, y compris les données et les points, ainsi que les données.  
  
 Vos <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objets sont insérés directement dans le <xref:System.Windows.Input.Stylus> flux de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> données <xref:System.Windows.UIElement.StylusPlugIns%2A> provenant de l’appareil lorsque vous ajoutez la propriété. L’ordre dans lequel les plug-ins sont ajoutés à <xref:System.Windows.UIElement.StylusPlugIns%2A> <xref:System.Windows.Input.StylusPoint> la collecte dicte l’ordre dans lequel ils recevront des données. Par exemple, si vous ajoutez un plug-in de filtre qui limite l’entrée à une région particulière, puis ajoutez un plug-in <xref:System.Windows.Input.StylusPoint> qui reconnaît les gestes tels qu’ils sont écrits, le plug-in qui reconnaît les gestes recevront des données filtrées.  
  
<a name="ImplementingStylusPlugins"></a>
## <a name="implementing-stylus-plug-ins"></a>Mise en œuvre de Stylus Plug-ins  
 Pour implémenter un plug-in, tirer une classe de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Cette classe est appliquée o le flux de <xref:System.Windows.Input.Stylus>données comme il vient de la . Dans cette classe, vous pouvez <xref:System.Windows.Input.StylusPoint> modifier les valeurs des données.  
  
> [!CAUTION]
> Si <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> un lancer ou provoque une exception, l’application se ferme. Vous devez tester soigneusement les <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> commandes qui consomment un et <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> n’utiliser un contrôle que si vous êtes certain que le ne lancera pas une exception.  
  
 L’exemple suivant montre un plug-in qui restreint l’entrée <xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint.Y%2A> de stylet en modifiant les valeurs et les valeurs dans les <xref:System.Windows.Input.StylusPoint> données à mesure qu’elles proviennent de l’appareil. <xref:System.Windows.Input.Stylus>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Ajout de votre plug-in à un InkCanvas  
 La façon la plus simple d’utiliser votre plug-in personnalisé est d’implémenter une classe qui dérive de InkCanvas et de l’ajouter à la <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété.  
  
 L’exemple suivant montre <xref:System.Windows.Controls.InkCanvas> une coutume qui filtre l’encre.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Si vous `FilterInkCanvas` ajoutez un à votre application et l’exécutez, vous remarquerez que l’encre n’est pas limitée à une région jusqu’à ce que l’utilisateur ait terminé un AVC. C’est <xref:System.Windows.Controls.InkCanvas> parce <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> que le a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> une propriété, qui <xref:System.Windows.UIElement.StylusPlugIns%2A> est un et est déjà un membre de la collection. La <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> coutume que <xref:System.Windows.UIElement.StylusPlugIns%2A> vous avez <xref:System.Windows.Input.StylusPoint> ajoutée <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à la collection reçoit les données après réception de données. Par conséquent, <xref:System.Windows.Input.StylusPoint> les données ne seront filtrées qu’après que l’utilisateur ait levé le stylo pour mettre fin à un AVC. Pour filtrer l’encre au fur et `FilterPlugin` à <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>mesure que l’utilisateur la dessine, vous devez insérer l’avant le .  
  
 Le code CMD suivant <xref:System.Windows.Controls.InkCanvas> démontre une coutume qui filtre l’encre au fur et à mesure qu’elle est dessinée.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Conclusion  
 En dérivant <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> vos propres classes <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> et en les insérant dans les collections, vous pouvez grandement améliorer le comportement de votre encre numérique. Vous avez accès <xref:System.Windows.Input.StylusPoint> aux données au fur et à mesure <xref:System.Windows.Input.Stylus> qu’elles sont générées, ce qui vous donne la possibilité de personnaliser l’entrée. Parce que vous avez un <xref:System.Windows.Input.StylusPoint> accès de haut niveau aux données, vous pouvez implémenter la collecte et le rendu d’encre avec des performances optimales pour votre application.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion avancée de l'encre](advanced-ink-handling.md)
- [Accès et manipulation de l’entrée du stylo](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
