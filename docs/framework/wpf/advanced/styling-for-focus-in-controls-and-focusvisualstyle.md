---
title: FocusVisualStyle et application d'un style au focus dans les contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: fda7ed12d232af5a7cfb8eb43cbb09eb793da171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141197"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>FocusVisualStyle et application d'un style au focus dans les contrôles
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose deux mécanismes parallèles permettant de changer l’apparence visuelle d’un contrôle lorsqu’il reçoit le focus clavier. Le premier mécanisme est d’utiliser des <xref:System.Windows.UIElement.IsKeyboardFocused%2A> ensembles de propriétés pour des propriétés telles que dans le style ou le modèle qui est appliqué au contrôle. Le deuxième mécanisme consiste à fournir un <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> style distinct comme valeur de la propriété; le « style visuel de mise au point » crée un arbre visuel séparé pour un adorant qui tire sur le dessus du contrôle, plutôt que de changer l’arbre visuel du contrôle ou d’un autre élément d’interface utilisateur en le remplaçant. Cette rubrique décrit les scénarios où chacun de ces mécanismes convient.  

<a name="Purpose"></a>
## <a name="the-purpose-of-focus-visual-style"></a>L’objectif du style de focus visuel  
 La fonctionnalité de style de focus visuel fournit un « modèle objet » commun permettant d’introduire un retour visuel utilisateur basé sur la navigation au clavier pour n’importe quel élément d’interface utilisateur. C’est possible sans appliquer un nouveau modèle au contrôle et sans connaître la composition spécifique du modèle.  
  
 Toutefois, étant donné que la fonctionnalité de style de focus visuel peut être utilisée sans connaître les modèles de contrôle, le retour visuel qui peut être affiché pour un contrôle avec un style de focus visuel est forcément limité. Cette fonctionnalité permet de superposer une arborescence d’éléments visuels différente (un ornement) sur l’arborescence d’éléments visuels créée par le rendu d’un contrôle via son modèle. Vous définissez cet arbre visuel séparé <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> en utilisant un style qui remplit la propriété.  
  
<a name="Default"></a>
## <a name="default-focus-visual-style-behavior"></a>Comportement du style de focus visuel par défaut  
 Les styles de focus visuels agissent uniquement lorsque l’action du focus a été démarrée par le clavier. Une action de la souris ou un changement de focus par programmation désactive le mode de style de focus visuel. Pour plus d’informations sur les différences entre les modes de focus, consultez [Vue d’ensemble du focus](focus-overview.md).  
  
 Les thèmes des contrôles proposent un comportement de style de focus visuel par défaut qui devient celui de tous les contrôles du thème. Ce style de thème est identifié <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>par la valeur de la clé statique . Lorsque vous déclarez votre propre style de focus visuel au niveau de l’application, vous remplacez ce comportement de style par défaut dans les thèmes. Si vous définissez l’ensemble du thème, vous devez utiliser cette même clé pour définir le style du comportement par défaut à appliquer à l’ensemble du thème.  
  
 Dans les thèmes, le style de focus visuel par défaut est généralement très simple. En voici une brève description :  
  
```xaml  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>
## <a name="when-to-use-focus-visual-styles"></a>Quand utiliser des styles de focus visuels  
 D’un point de vue conceptuel, l’apparence des styles de focus visuels appliqués aux contrôles doit être la même pour tous les contrôles. Un moyen de garantir l’homogénéité du style est de ne changer le style de focus visuel que si vous créez un thème entier, dans lequel chaque contrôle défini reçoit le même style de focus visuel ou une variation d’un style visuellement semblable. Vous pouvez également utiliser le même style (ou des styles similaires) pour tous les éléments d’une page ou d’une interface utilisateur auxquels vous pouvez donner le focus à l’aide du clavier.  
  
 S’inscrivant <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> sur des styles de contrôle individuels qui ne font pas partie d’un thème n’est pas l’utilisation prévue de styles visuels de mise au point. En effet, un comportement visuel incohérent entre les contrôles peut porter à confusion au niveau du focus clavier. Si vous avez l’intention de contrôler des comportements spécifiques pour la mise au point clavier qui ne sont délibérément pas <xref:System.Windows.UIElement.IsFocused%2A> cohérents à travers un thème, une approche beaucoup mieux est d’utiliser des déclencheurs dans les styles pour les propriétés individuelles d’état d’entrée, tels que ou <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Les styles de focus visuels agissent exclusivement pour le focus clavier. Ils constituent donc un type de fonctionnalité d’accessibilité. Si vous souhaitez changer l’interface utilisateur au niveau d’un type de focus, que ce soit par la souris, le clavier ou par programmation, vous ne devez pas utiliser les styles de focus visuels. Vous devez utiliser des setters et des déclencheurs dans les styles ou les modèles qui utilisent la valeur des propriétés de focus générales, telles que <xref:System.Windows.UIElement.IsFocused%2A> ou <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>
## <a name="how-to-create-a-focus-visual-style"></a>Comment créer un style de focus visuel  
 Le style que vous créez pour un <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Controls.Control>style visuel de mise au point devrait toujours avoir le de . Le style doit se <xref:System.Windows.Controls.ControlTemplate>composer principalement d’un . Vous ne spécifiez pas le type cible pour <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>être le type où le style visuel de mise au point est assigné à la .  
  
 Parce que le <xref:System.Windows.Controls.Control>type cible est toujours, vous devez style en utilisant <xref:System.Windows.Controls.Control> des propriétés qui sont communes à tous les contrôles (en utilisant les propriétés de la classe et ses classes de base). Vous devez créer un modèle qui soit superposé à un élément d’interface utilisateur et qui ne masque pas les zones fonctionnelles du contrôle. En général, cela signifie que le retour visuel doit apparaître en dehors des marges du contrôle, ou sous la forme d’effets temporaires ou discrets qui ne bloquent pas le test d’atteinte du contrôle auquel est appliqué le style de focus visuel. Propriétés que vous pouvez utiliser dans la liaison de modèle qui sont <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A>utiles pour déterminer le dimensionnement et le positionnement de votre modèle de superposition incluent, , <xref:System.Windows.FrameworkElement.Margin%2A>, et <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternatives à l’utilisation des styles de focus visuels  
 Lorsque l’utilisation d’un style de focus visuel n’est pas adaptée, soit parce que vous appliquez un style différent à chaque contrôle, soit parce que vous souhaitez contrôler davantage le modèle de contrôle, il existe plusieurs autres propriétés et techniques accessibles qui peuvent créer un comportement visuel en réponse aux changements du focus.  
  
 Les déclencheurs, les setters et les setters d’événement sont tous abordés en détail dans [Styles et modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md). La gestion des événements routés est abordée dans [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Si vous êtes spécifiquement intéressé <xref:System.Windows.UIElement.IsKeyboardFocused%2A> par la mise au <xref:System.Windows.Trigger>point du clavier, la propriété de dépendance peut être utilisée pour une propriété. L’utilisation d’un déclencheur de propriété dans un style ou un modèle convient mieux à la définition d’un comportement de focus clavier qui est propre à un seul contrôle, et qui peut ne pas correspondre visuellement au comportement de focus clavier des autres contrôles.  
  
 Une autre propriété <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>de dépendance similaire est , qui pourrait être approprié à utiliser si vous voulez appeler visuellement que la mise au point clavier est quelque part dans le compositing ou dans la zone fonctionnelle du contrôle. Par exemple, vous <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> pouvez placer un déclencheur de telle sorte qu’un panneau qui regroupe plusieurs contrôles apparaît différemment, même si la mise au point du clavier peut plus précisément être sur un élément individuel dans ce panneau.  
  
 Vous pouvez également <xref:System.Windows.UIElement.GotKeyboardFocus> utiliser <xref:System.Windows.UIElement.LostKeyboardFocus> les événements et (ainsi que leurs équivalents Aperçu). Vous pouvez utiliser ces événements <xref:System.Windows.EventSetter>comme base d’un , ou vous pouvez écrire des gestionnaires pour les événements en retard de code.  
  
### <a name="other-focus-properties"></a>Autres propriétés de focus  
 Si vous voulez toutes les causes possibles de changer de mise au point <xref:System.Windows.UIElement.IsFocused%2A> pour produire un comportement <xref:System.Windows.UIElement.GotFocus> <xref:System.Windows.UIElement.LostFocus> visuel, vous <xref:System.Windows.EventSetter>devez baser un setter ou déclencher sur la propriété de dépendance, ou alternativement sur le ou les événements utilisés pour un .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble du focus](focus-overview.md)
- [Vue d’ensemble des entrées](input-overview.md)
