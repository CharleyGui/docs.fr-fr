---
title: Événements de changement de propriété
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], change events
- property value changes [WPF]
- change events [WPF], property
- events [WPF], change in property values
- creating property triggers [WPF]
- property change events [WPF], types of
- property change events [WPF]
- property triggers [WPF]
- identifying changed property events [WPF]
- property triggers [WPF], definition of
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
ms.openlocfilehash: 06056b492439531aa60becbb7bca250a439bfb68
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567427"
---
# <a name="property-change-events"></a>Événements de changement de propriété
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] définit plusieurs événements déclenchés en réponse au changement de la valeur d’une propriété. Souvent, la propriété est une propriété de dépendance. L’événement lui-même est parfois un événement routé et est parfois un événement de common language runtime standard (CLR). La définition de l’événement varie selon le scénario, car certains changements de propriété sont routés de façon plus appropriée à travers une arborescence d’éléments, tandis que d’autres changements de propriété ne concernent en général que l’objet sur lequel la propriété a changé.  
  
## <a name="identifying-a-property-change-event"></a>Identification d’un événement de changement de propriété  
 Les événements qui signalent un changement de propriété ne sont pas tous explicitement identifiés comme événement de changement de propriété, selon le modèle de signature ou le modèle de renommage. En règle générale, la description de l’événement dans la documentation du kit de développement logiciel (SDK) indique si l’événement est directement lié à une modification de valeur de propriété et fournit des références croisées entre la propriété et l’événement.  
  
### <a name="routedpropertychanged-events"></a>Événements RoutedPropertyChanged  
 Certains événements utilisent un type de données d’événement et un délégué destinés explicitement aux événements de changement de propriété. Le type de données d' <xref:System.Windows.RoutedPropertyChangedEventArgs%601>événement est, et le <xref:System.Windows.RoutedPropertyChangedEventHandler%601>délégué est. Les données d’événement et le délégué ont tous deux un paramètre de type générique utilisé pour spécifier le type réel de la propriété changée quand vous définissez le gestionnaire. Les données d’événement contiennent deux propriétés <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> , <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>et, qui sont à la fois passées comme argument de type dans les données d’événement.  
  
 La partie « Routed » du nom indique que l’événement de changement de propriété est inscrit comme événement routé. L’avantage du routage d’un événement de changement de propriété est que le niveau supérieur d’un contrôle peut recevoir des événements de changement de propriété si la valeur des propriétés sur les éléments enfants (parties composites du contrôle) changent. Par exemple, vous pouvez créer un contrôle qui incorpore un <xref:System.Windows.Controls.Primitives.RangeBase> contrôle tel qu’un. <xref:System.Windows.Controls.Slider> Si la valeur de la <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriété change sur la partie du curseur, vous souhaiterez peut-être gérer cette modification sur le contrôle parent plutôt que sur le composant.  
  
 Comme vous avez une ancienne valeur et une nouvelle valeur, vous pouvez également utiliser ce gestionnaire d’événements comme validateur de la valeur de propriété. Toutefois, la plupart des événements de changement de propriété ne sont pas conçus dans cet objectif. En règle générale, les valeurs sont fournies pour pouvoir agir sur ces valeurs dans d’autres zones logiques de votre code, mais nous ne recommandons pas de changer les valeurs dans le gestionnaire d’événements, car cela peut entraîner une récursivité involontaire selon la façon dont votre gestionnaire est implémenté.  
  
 Si votre propriété est une propriété de dépendance personnalisée, ou si vous utilisez une classe dérivée dans laquelle vous avez défini le code d’instanciation, il existe un mécanisme bien plus efficace pour le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivi des modifications de propriétés qui est intégré au système de propriétés: <xref:System.Windows.CoerceValueCallback> les rappels du système <xref:System.Windows.PropertyChangedCallback>de propriétés et. Pour plus d’informations sur l’utilisation du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour la validation et le forçage de type, consultez [Validation et rappels de propriétés de dépendance](dependency-property-callbacks-and-validation.md) et [Propriétés de dépendance personnalisées](custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>Événements DependencyPropertyChanged  
 Une autre paire de types qui font partie d’un scénario d’événement de <xref:System.Windows.DependencyPropertyChangedEventArgs> modification <xref:System.Windows.DependencyPropertyChangedEventHandler>de propriété est et. Les événements de ces modifications de propriété ne sont pas routés; Il s’agit d’événements CLR standard. <xref:System.Windows.DependencyPropertyChangedEventArgs>est un type de rapport de données d’événement inhabituel, car <xref:System.EventArgs>il ne dérive pas de; <xref:System.Windows.DependencyPropertyChangedEventArgs> est une structure, et non une classe.  
  
 Les événements qui <xref:System.Windows.DependencyPropertyChangedEventArgs> utilisent <xref:System.Windows.DependencyPropertyChangedEventHandler> et sont légèrement plus courants `RoutedPropertyChanged` que les événements. Un exemple d’événement qui utilise ces types est <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Comme <xref:System.Windows.RoutedPropertyChangedEventArgs%601> ,<xref:System.Windows.DependencyPropertyChangedEventArgs> signale également une valeur ancienne et une nouvelle valeur pour la propriété. Par ailleurs, les mêmes considérations sur ce que vous pouvez faire avec les valeurs s’appliquent : il n’est généralement pas recommandé d’essayer de changer les valeurs dans l’expéditeur en réponse à l’événement.  
  
## <a name="property-triggers"></a>Déclencheurs de propriété  
 Le déclencheur de propriété est un concept étroitement lié à celui de l’événement de changement de propriété. Un déclencheur de propriété est créé dans un style ou un modèle, et vous permet de créer un comportement conditionnel basé sur la valeur de la propriété à laquelle le déclencheur de propriété est attribué.  
  
 La propriété d’un déclencheur de propriété doit être une propriété de dépendance. Elle peut être (et l’est souvent) une propriété de dépendance en lecture seule. Quand le nom de la propriété commence par « Is », cela signifie que la propriété de dépendance exposée par un contrôle est au moins partiellement conçue comme un déclencheur de propriété. Les propriétés qui ont cette désignation sont souvent des propriétés de dépendance booléennes en lecture seule dont l’objectif principal est de signaler l’état du contrôle susceptible d’avoir des conséquences sur l’interface utilisateur en temps réel et qui est donc un potentiel déclencheur de propriété.  
  
 Certaines de ces propriétés ont également un événement de changement de propriété dédié. Par exemple, la propriété <xref:System.Windows.UIElement.IsMouseCaptured%2A> a un événement <xref:System.Windows.UIElement.IsMouseCapturedChanged>property changed. La propriété elle-même est en lecture seule, avec sa valeur ajustée par le système d’entrée, et <xref:System.Windows.UIElement.IsMouseCapturedChanged> le système d’entrée déclenche chaque modification en temps réel.  
  
 Par rapport à un événement de changement de propriété avec la valeur true, l’utilisation d’un déclencheur de propriété pour agir quand une propriété change présente certaines limitations.  
  
 Les déclencheurs de propriété suivent une logique de correspondance exacte. Vous spécifiez une propriété et une valeur qui est la valeur spécifique pour laquelle le déclencheur doit agir. Par exemple : `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. En raison de cette limitation, la majorité des utilisations de déclencheur de propriété sont réservées aux propriétés booléennes ou aux propriétés qui prennent une valeur d’énumération dédiée, où la plage de valeurs possibles est suffisamment gérable pour définir un déclencheur pour chaque cas. Les déclencheurs de propriété peuvent aussi exister uniquement pour des valeurs spéciales, comme quand un nombre d’éléments atteint zéro et qu’il n’y a pas de déclencheur quand la valeur de propriété redevient différente de zéro (ici, au lieu d’avoir des déclencheurs pour tous les cas, vous avez besoin d’un gestionnaire d’événements de code ou d’un comportement par défaut qui rétablit l’état du déclencheur quand la valeur est différente de zéro).  
  
 La syntaxe du déclencheur de propriété est analogue à une instruction « if » en programmation. Si la condition de déclenchement est true, le « corps » du déclencheur de propriété est « exécuté ». Le « corps » d’un déclencheur de propriété n’est pas du code, mais un balisage. Ce balisage est limité à l’utilisation d' <xref:System.Windows.Setter> un ou plusieurs éléments pour définir d’autres propriétés de l’objet dans lequel le style ou le modèle est appliqué.  
  
 Pour compenser la condition «if» d’un déclencheur de propriété qui possède un large éventail de valeurs possibles, il est généralement recommandé de définir la même valeur de propriété sur <xref:System.Windows.Setter>une valeur par défaut à l’aide d’un. De cette façon, <xref:System.Windows.Trigger> l’accesseur Set contenu a la priorité lorsque la condition de déclenchement est <xref:System.Windows.Setter> true, et le qui <xref:System.Windows.Trigger> ne se trouve pas dans un est prioritaire chaque fois que la condition de déclencheur est false.  
  
 Les déclencheurs de propriété sont généralement appropriés quand une ou plusieurs propriétés d’apparence doivent changer en fonction de l’état d’une autre propriété sur le même élément.  
  
 Pour plus d’informations sur les déclencheurs de propriété, consultez [Application d’un style et création de modèles](../controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des événements routés](routed-events-overview.md)
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
