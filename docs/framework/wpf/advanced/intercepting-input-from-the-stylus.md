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
ms.openlocfilehash: 2547c0aa2f3a14080868c2760fa8999eb99d3d16
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046326"
---
# <a name="intercepting-input-from-the-stylus"></a>Interception d'entrée à partir du stylet
L' <xref:System.Windows.Input.StylusPlugIns> architecture fournit un mécanisme permettant d’implémenter un contrôle de <xref:System.Windows.Input.Stylus> bas niveau sur l’entrée et la <xref:System.Windows.Ink.Stroke> création d’objets d’encre numérique. La <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classe fournit un mécanisme qui vous permet d’implémenter un comportement personnalisé et de l’appliquer au flux de données provenant du périphérique de stylet pour des performances optimales.  
  
 Cette rubrique contient les sous-sections suivantes :  
  
- [Architecture](#Architecture)  
  
- [Implémentation de plug-ins de stylet](#ImplementingStylusPlugins)  
  
- [Ajout de votre plug-in à un InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Conclusion](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architecture  
 Est l’évolution des API [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) , décrite dans [accès et manipulation](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)du stylet, dans le [Kit de développement logiciel (SDK) de Microsoft Windows XP Tablet PC Edition 1,7.](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409) <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>  
  
 Chaque <xref:System.Windows.UIElement> a une <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété qui est un <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Vous pouvez ajouter un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à la <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété d’un élément pour <xref:System.Windows.Input.StylusPoint> manipuler les données au fur et à mesure de leur génération. <xref:System.Windows.Input.StylusPoint>les données se composent de toutes les propriétés prises en charge par le <xref:System.Windows.Input.StylusPoint.X%2A> digitaliseur système, y compris les <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> données de point et <xref:System.Windows.Input.StylusPoint.Y%2A> , ainsi que les données.  
  
 Vos <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objets sont insérés directement dans le flux de données provenant de <xref:System.Windows.Input.Stylus> l' <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> appareil lorsque vous ajoutez à la <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété. L’ordre dans lequel les plug-ins sont ajoutés à <xref:System.Windows.UIElement.StylusPlugIns%2A> la collection détermine l’ordre dans lequel ils doivent recevoir <xref:System.Windows.Input.StylusPoint> les données. Par exemple, si vous ajoutez un plug-in de filtre qui restreint l’entrée à une région particulière, puis ajoutez un plug-in qui reconnaît les gestes au fur et à mesure de leur écriture, le plug-in qui reconnaît les gestes recevra les <xref:System.Windows.Input.StylusPoint> données filtrées.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implémentation de plug-ins de stylet  
 Pour implémenter un plug-in, dérivez <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>une classe de. Cette classe est appliquée au flux de données tel qu’il provient de <xref:System.Windows.Input.Stylus>. Dans cette classe, vous pouvez modifier les valeurs des <xref:System.Windows.Input.StylusPoint> données.  
  
> [!CAUTION]
> Si un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> lève une exception ou provoque une exception, l’application se ferme. Vous devez tester minutieusement les <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> contrôles qui consomment un et utiliser un contrôle uniquement si vous êtes certain que ne lèvera pas d’exception.  
  
 L’exemple suivant illustre un plug-in qui restreint l' <xref:System.Windows.Input.StylusPoint.X%2A> entrée du stylet en modifiant les valeurs et <xref:System.Windows.Input.StylusPoint.Y%2A> dans les <xref:System.Windows.Input.StylusPoint> données à mesure qu’elles proviennent de l' <xref:System.Windows.Input.Stylus> appareil.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Ajout de votre plug-in à un InkCanvas  
 Le moyen le plus simple d’utiliser votre plug-in personnalisé consiste à implémenter une classe qui dérive de InkCanvas et à <xref:System.Windows.UIElement.StylusPlugIns%2A> l’ajouter à la propriété.  
  
 L’exemple suivant montre un personnalisé <xref:System.Windows.Controls.InkCanvas> qui filtre l’encre.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Si vous ajoutez un `FilterInkCanvas` à votre application et que vous l’exécutez, vous remarquerez que l’encre n’est pas limitée à une région tant que l’utilisateur n’a pas terminé un trait. Cela est dû au <xref:System.Windows.Controls.InkCanvas> fait que <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> le a une propriété, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> qui est un et qui est déjà <xref:System.Windows.UIElement.StylusPlugIns%2A> membre de la collection. Le personnalisé <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> que vous avez ajouté <xref:System.Windows.UIElement.StylusPlugIns%2A> à la collection <xref:System.Windows.Input.StylusPoint> reçoit les <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> données après avoir reçu les données. Par conséquent, les <xref:System.Windows.Input.StylusPoint> données ne sont pas filtrées tant que l’utilisateur n’a pas levé le stylet pour terminer un trait. Pour filtrer l’encre lorsque l’utilisateur la dessine, vous devez insérer `FilterPlugin` le avant <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>le.  
  
 Le code C# suivant illustre un personnalisé <xref:System.Windows.Controls.InkCanvas> qui filtre l’encre au fur et à mesure de son dessin.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusion  
 En dérivant vos propres <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes et en les insérant dans <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> des collections, vous pouvez améliorer le comportement de votre encre numérique. Vous avez accès aux <xref:System.Windows.Input.StylusPoint> données à mesure qu’elles sont générées, ce qui vous donne la possibilité de personnaliser l' <xref:System.Windows.Input.Stylus> entrée. Comme vous disposez d’un accès de bas niveau aux <xref:System.Windows.Input.StylusPoint> données, vous pouvez implémenter la collecte et le rendu d’encre avec des performances optimales pour votre application.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion avancée de l’encre](advanced-ink-handling.md)
- [Accès et manipulation de l’entrée de stylet](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
