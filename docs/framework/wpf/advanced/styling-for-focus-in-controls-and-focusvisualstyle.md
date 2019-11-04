---
title: FocusVisualStyle et application d'un style au focus dans les contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 988b084144532df6f7a6073184fcf035b0813bfd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458682"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>FocusVisualStyle et application d'un style au focus dans les contrôles
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose deux mécanismes parallèles permettant de changer l’apparence visuelle d’un contrôle lorsqu’il reçoit le focus clavier. Le premier mécanisme consiste à utiliser des accesseurs set de propriété pour les propriétés telles que <xref:System.Windows.UIElement.IsKeyboardFocused%2A> dans le style ou le modèle appliqué au contrôle. Le deuxième mécanisme consiste à fournir un style distinct comme valeur de la propriété <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> ; le « style de focus visuel » crée une arborescence d’éléments visuels distincte pour un ornement qui dessine en haut du contrôle, plutôt que de modifier l’arborescence d’éléments visuels du contrôle ou d’un autre élément d’interface utilisateur en le remplaçant. Cette rubrique décrit les scénarios où chacun de ces mécanismes convient.  

<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>L’objectif du style de focus visuel  
 La fonctionnalité de style de focus visuel fournit un « modèle objet » commun permettant d’introduire un retour visuel utilisateur basé sur la navigation au clavier pour n’importe quel élément d’interface utilisateur. C’est possible sans appliquer un nouveau modèle au contrôle et sans connaître la composition spécifique du modèle.  
  
 Toutefois, étant donné que la fonctionnalité de style de focus visuel peut être utilisée sans connaître les modèles de contrôle, le retour visuel qui peut être affiché pour un contrôle avec un style de focus visuel est forcément limité. Cette fonctionnalité permet de superposer une arborescence d’éléments visuels différente (un ornement) sur l’arborescence d’éléments visuels créée par le rendu d’un contrôle via son modèle. Vous définissez cette arborescence d’éléments visuels distincte à l’aide d’un style qui remplit la propriété <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Comportement du style de focus visuel par défaut  
 Les styles de focus visuels agissent uniquement lorsque l’action du focus a été démarrée par le clavier. Une action de la souris ou un changement de focus par programmation désactive le mode de style de focus visuel. Pour plus d’informations sur les différences entre les modes de focus, consultez [Vue d’ensemble du focus](focus-overview.md).  
  
 Les thèmes des contrôles proposent un comportement de style de focus visuel par défaut qui devient celui de tous les contrôles du thème. Ce style de thème est identifié par la valeur de la <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>de clé statique. Lorsque vous déclarez votre propre style de focus visuel au niveau de l’application, vous remplacez ce comportement de style par défaut dans les thèmes. Si vous définissez l’ensemble du thème, vous devez utiliser cette même clé pour définir le style du comportement par défaut à appliquer à l’ensemble du thème.  
  
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
  
 La définition de <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> sur des styles de contrôle individuels qui ne font pas partie d’un thème n’est pas l’utilisation prévue des styles de focus visuels. En effet, un comportement visuel incohérent entre les contrôles peut porter à confusion au niveau du focus clavier. Si vous encadrez des comportements spécifiques au contrôle pour le focus clavier qui ne sont délibérément pas cohérents dans un thème, une approche bien meilleure consiste à utiliser des déclencheurs dans les styles pour les propriétés d’état d’entrée individuelles, telles que <xref:System.Windows.UIElement.IsFocused%2A> ou <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Les styles de focus visuels agissent exclusivement pour le focus clavier. Ils constituent donc un type de fonctionnalité d’accessibilité. Si vous souhaitez changer l’interface utilisateur au niveau d’un type de focus, que ce soit par la souris, le clavier ou par programmation, vous ne devez pas utiliser les styles de focus visuels. Vous devez utiliser des setters et des déclencheurs dans les styles ou les modèles qui utilisent la valeur des propriétés de focus générales, telles que <xref:System.Windows.UIElement.IsFocused%2A> ou <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Comment créer un style de focus visuel  
 Le style que vous créez pour un style de focus visuel doit toujours avoir le <xref:System.Windows.Style.TargetType%2A> de <xref:System.Windows.Controls.Control>. Le style doit se composer principalement d’un <xref:System.Windows.Controls.ControlTemplate>. Vous ne spécifiez pas le type de cible comme étant le type dans lequel le style de focus visuel est assigné au <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Étant donné que le type cible est toujours <xref:System.Windows.Controls.Control>, vous devez effectuer un style à l’aide des propriétés communes à tous les contrôles (à l’aide des propriétés de la classe <xref:System.Windows.Controls.Control> et de ses classes de base). Vous devez créer un modèle qui soit superposé à un élément d’interface utilisateur et qui ne masque pas les zones fonctionnelles du contrôle. En général, cela signifie que le retour visuel doit apparaître en dehors des marges du contrôle, ou sous la forme d’effets temporaires ou discrets qui ne bloquent pas le test d’atteinte du contrôle auquel est appliqué le style de focus visuel. Les propriétés que vous pouvez utiliser dans la liaison de modèle sont utiles pour déterminer le dimensionnement et le positionnement de votre modèle de superposition : <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>et <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternatives à l’utilisation des styles de focus visuels  
 Lorsque l’utilisation d’un style de focus visuel n’est pas adaptée, soit parce que vous appliquez un style différent à chaque contrôle, soit parce que vous souhaitez contrôler davantage le modèle de contrôle, il existe plusieurs autres propriétés et techniques accessibles qui peuvent créer un comportement visuel en réponse aux changements du focus.  
  
 Les déclencheurs, les setters et les setters d’événement sont tous abordés en détail dans [Styles et modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md). La gestion des événements routés est abordée dans [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Si vous êtes particulièrement intéressé par le focus clavier, vous pouvez utiliser la propriété de dépendance <xref:System.Windows.UIElement.IsKeyboardFocused%2A> pour une propriété <xref:System.Windows.Trigger>. L’utilisation d’un déclencheur de propriété dans un style ou un modèle convient mieux à la définition d’un comportement de focus clavier qui est propre à un seul contrôle, et qui peut ne pas correspondre visuellement au comportement de focus clavier des autres contrôles.  
  
 Une autre propriété de dépendance similaire est <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, qui peut être utile si vous souhaitez appeler visuellement que le focus clavier se trouve quelque part dans la composition ou dans la zone fonctionnelle du contrôle. Par exemple, vous pouvez placer un déclencheur <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> de façon à ce qu’un panneau qui regroupe plusieurs contrôles apparaisse différemment, même si le focus clavier peut se trouver plus précisément sur un élément individuel dans ce panneau.  
  
 Vous pouvez également utiliser les événements <xref:System.Windows.UIElement.GotKeyboardFocus> et <xref:System.Windows.UIElement.LostKeyboardFocus> (ainsi que leurs équivalents en version préliminaire). Vous pouvez utiliser ces événements comme base pour une <xref:System.Windows.EventSetter>, ou vous pouvez écrire des gestionnaires pour les événements dans le code-behind.  
  
### <a name="other-focus-properties"></a>Autres propriétés de focus  
 Si vous souhaitez que toutes les causes possibles d’une modification du focus produisent un comportement visuel, vous devez baser un accesseur set ou un déclencheur sur la propriété de dépendance <xref:System.Windows.UIElement.IsFocused%2A>, ou encore sur les événements <xref:System.Windows.UIElement.GotFocus> ou <xref:System.Windows.UIElement.LostFocus> utilisés pour un <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble du focus](focus-overview.md)
- [Vue d’ensemble des entrées](input-overview.md)
