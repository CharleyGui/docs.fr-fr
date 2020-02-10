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
ms.openlocfilehash: 7629843730a82584e94448ceac1ea574906876c9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095136"
---
# <a name="intercepting-input-from-the-stylus"></a>Interception d'entrée à partir du stylet
L’architecture <xref:System.Windows.Input.StylusPlugIns> fournit un mécanisme permettant d’implémenter un contrôle de bas niveau sur <xref:System.Windows.Input.Stylus> entrée et la création d’objets <xref:System.Windows.Ink.Stroke> d’encre numérique. La classe <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> fournit un mécanisme vous permettant d’implémenter un comportement personnalisé et de l’appliquer au flux de données provenant du périphérique de stylet pour des performances optimales.  
  
 Cette rubrique contient les sous-sections suivantes :  
  
- [Architecture](#Architecture)  
  
- [Implémentation de plug-ins de stylet](#ImplementingStylusPlugins)  
  
- [Ajout de votre plug-in à un InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Conclusion](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architecture  
 Le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> est l’évolution des API [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) , décrite dans [accès et manipulation des entrées de stylet](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).  
  
 Chaque <xref:System.Windows.UIElement> a une propriété <xref:System.Windows.UIElement.StylusPlugIns%2A> qui est un <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Vous pouvez ajouter une <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à la propriété <xref:System.Windows.UIElement.StylusPlugIns%2A> d’un élément pour manipuler les données de <xref:System.Windows.Input.StylusPoint> lors de leur génération. <xref:System.Windows.Input.StylusPoint> données se composent de toutes les propriétés prises en charge par le digitaliseur système, y compris les données de <xref:System.Windows.Input.StylusPoint.X%2A> et de point de <xref:System.Windows.Input.StylusPoint.Y%2A>, ainsi que <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> données.  
  
 Vos objets <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sont insérés directement dans le flux de données provenant du périphérique <xref:System.Windows.Input.Stylus> lorsque vous ajoutez le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à la propriété <xref:System.Windows.UIElement.StylusPlugIns%2A>. L’ordre dans lequel les plug-ins sont ajoutés à la collection <xref:System.Windows.UIElement.StylusPlugIns%2A> détermine l’ordre dans lequel ils recevront les données <xref:System.Windows.Input.StylusPoint>. Par exemple, si vous ajoutez un plug-in de filtre qui restreint l’entrée à une région particulière, puis ajoutez un plug-in qui reconnaît les gestes au fur et à mesure de leur écriture, le plug-in qui reconnaît les gestes recevra des données de <xref:System.Windows.Input.StylusPoint> filtrées.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implémentation de plug-ins de stylet  
 Pour implémenter un plug-in, dérivez une classe de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Cette classe est appliquée au flux de données tel qu’il provient du <xref:System.Windows.Input.Stylus>. Dans cette classe, vous pouvez modifier les valeurs des données de <xref:System.Windows.Input.StylusPoint>.  
  
> [!CAUTION]
> Si une <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> lève ou provoque une exception, l’application se ferme. Vous devez tester minutieusement les contrôles qui consomment un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et utiliser un contrôle uniquement si vous êtes certain que le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ne lèvera pas d’exception.  
  
 L’exemple suivant illustre un plug-in qui restreint l’entrée du stylet en modifiant le <xref:System.Windows.Input.StylusPoint.X%2A> et <xref:System.Windows.Input.StylusPoint.Y%2A> valeurs dans les données <xref:System.Windows.Input.StylusPoint> à mesure qu’elles proviennent de l’appareil <xref:System.Windows.Input.Stylus>.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Ajout de votre plug-in à un InkCanvas  
 Le moyen le plus simple d’utiliser votre plug-in personnalisé consiste à implémenter une classe qui dérive de InkCanvas et à l’ajouter à la propriété <xref:System.Windows.UIElement.StylusPlugIns%2A>.  
  
 L’exemple suivant illustre une <xref:System.Windows.Controls.InkCanvas> personnalisée qui filtre l’encre.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Si vous ajoutez une `FilterInkCanvas` à votre application et que vous l’exécutez, vous remarquerez que l’encre n’est pas limitée à une région tant que l’utilisateur n’a pas terminé un trait. Cela est dû au fait que la <xref:System.Windows.Controls.InkCanvas> a une propriété <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>, qui est un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et qui est déjà membre de la collection <xref:System.Windows.UIElement.StylusPlugIns%2A>. La <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personnalisée que vous avez ajoutée à la collection de <xref:System.Windows.UIElement.StylusPlugIns%2A> reçoit les données de <xref:System.Windows.Input.StylusPoint> après <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> de réception des données. Par conséquent, les données de <xref:System.Windows.Input.StylusPoint> ne sont pas filtrées tant que l’utilisateur n’a pas levé le stylet pour terminer un trait. Pour filtrer l’encre au fur et à mesure que l’utilisateur la dessine, vous devez insérer le `FilterPlugin` avant le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Le code C# suivant illustre une <xref:System.Windows.Controls.InkCanvas> personnalisée qui filtre l’encre au fur et à mesure de son dessin.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusion  
 En dérivant vos propres classes <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et en les insérant dans des collections <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, vous pouvez améliorer le comportement de votre encre numérique. Vous avez accès aux données de <xref:System.Windows.Input.StylusPoint> lors de leur génération, ce qui vous donne la possibilité de personnaliser l’entrée de <xref:System.Windows.Input.Stylus>. Étant donné que vous disposez d’un accès de bas niveau aux données <xref:System.Windows.Input.StylusPoint>, vous pouvez implémenter la collecte et le rendu d’encre avec des performances optimales pour votre application.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion avancée de l’encre](advanced-ink-handling.md)
- [Accès et manipulation de l’entrée de stylet](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
