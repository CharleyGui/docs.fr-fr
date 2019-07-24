---
title: Vue d'ensemble des événements attachés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: a3a2f711840ad7f6e28443dac3c18501cd4400e0
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401403"
---
# <a name="attached-events-overview"></a>Vue d'ensemble des événements attachés
Le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] définit un composant de langage et un type d’événement appelé *événement attaché*. Le concept d’un événement attaché vous permet d’ajouter un gestionnaire pour un événement particulier à un élément arbitraire plutôt qu’à un élément qui définit réellement l’événement ou qui en hérite. Dans ce cas, ni l’objet qui déclenche potentiellement l’événement, ni l’instance de gestion de destination ne définit ou ne « détient » l’événement.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique suppose que vous avez lu [Vue d’ensemble des événements routés](routed-events-overview.md) et [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Syntaxe d’un événement attaché  
 Les événements attachés ont une syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et un modèle de codage qui doivent être utilisés par le code de stockage pour prendre en charge l’utilisation des événements attachés.  
  
 Dans la syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], l’événement attaché est spécifié non seulement par son nom d’évènement, mais aussi par son type propriétaire, les deux étant séparés par un point (.). Comme le nom de l’évènement est qualifié avec le nom de son type propriétaire, la syntaxe de l’événement attaché permet à celui-ci d’être attaché à tout élément pouvant être instancié.  
  
 Par exemple, vous trouverez ci-dessous la syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nécessaire pour attacher un gestionnaire à un événement attaché `NeedsCleaning` personnalisé :  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Notez le préfixe `aqua:`. Ce préfixe est nécessaire dans le cas présent, car l’événement attaché est un événement personnalisé qui provient d’un fichier xmlns mappé personnalisé.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Comment WPF implémente des événements attachés  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les événements attachés sont sauvegardés <xref:System.Windows.RoutedEvent> par un champ et sont routés via l’arborescence après leur déclenchement. En général, la source de l’événement attaché (l’objet qui déclenche l’événement) est une source système ou de service. L’objet qui exécute le code qui déclenche l’événement ne fait donc pas directement partie de l’arborescence d’éléments.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scénarios pour les événements attachés  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les événements attachés sont présents dans certains domaines de fonctionnalités où il existe une abstraction au niveau du service, par exemple pour les <xref:System.Windows.Input.Mouse> événements activés <xref:System.Windows.Controls.Validation> par la classe statique ou la classe. Les classes qui interagissent avec le service, ou qui l’utilisent, peuvent employer l’événement dans la syntaxe de l’événement attaché ou choisir de surfacer l’événement attaché en tant qu’événement routé faisant partie de la façon dont la classe intègre les fonctionnalités du service.  
  
 Bien que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définisse un certain nombre d’événements attachés, les scénarios dans lesquels vous utilisez ou gérez directement l’événement attaché sont très limités. En règle générale, l’événement attaché répond à un objectif d’architecture, mais est ensuite transféré à un événement routé non attaché (avec un wrapper d’événement CLR).  
  
 Par exemple <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> , l’événement attaché sous-jacent peut être géré plus facilement sur tout donné <xref:System.Windows.UIElement.MouseDown> <xref:System.Windows.UIElement> en utilisant <xref:System.Windows.UIElement> sur, plutôt que de gérer la syntaxe de l' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] événement attaché dans ou dans le code. L’événement attaché a une fonction d’architecture, car il permet l’extension future des périphériques d’entrée. L’appareil hypothétique n’aurait besoin d’être <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> déclenché que pour simuler l’entrée de la souris et n’aurait pas <xref:System.Windows.Input.Mouse> besoin de dériver de pour ce faire. Toutefois, ce scénario implique une gestion du code des événements, et une gestion [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de l’événement attaché n’est pas pertinente dans ce cas.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Gestion d’un événement attaché dans WPF  
 La gestion d’un événement attaché et le code du gestionnaire que vous allez écrire sont essentiellement les mêmes que pour un événement routé.  
  
 En général, un événement attaché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’est pas très différent d’un événement routé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Les différences portent sur la provenance de l’événement et sur la façon dont il est exposé par une classe en tant que membre (ce qui affecte également la syntaxe du gestionnaire [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]).  
  
 Toutefois, comme indiqué précédemment, les événements attachés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants ne sont pas particulièrement destinés à être gérés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le plus souvent, le but de l’événement est de permettre à un élément composé de signaler un état à un élément parent au moment de la composition. Dans ce cas, l’événement est généralement déclenché dans du code et compte également sur une gestion de classe dans la classe parente appropriée. Par exemple, les éléments d' <xref:System.Windows.Controls.Primitives.Selector> un sont censés déclencher l' <xref:System.Windows.Controls.Primitives.Selector.Selected> événement attaché, qui est ensuite géré par la <xref:System.Windows.Controls.Primitives.Selector> classe, puis potentiellement converti par la <xref:System.Windows.Controls.Primitives.Selector> classe en un événement routé différent, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Pour plus d’informations sur les événements routés et la gestion de classe, consultez [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Définition de vos propres événements attachés en tant qu’événements routés  
 Si vous effectuez une dérivation à partir de classes de base [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] communes, vous pouvez implémenter vos propres événements attachés en incluant certaines méthodes de modèle dans votre classe et en utilisant des méthodes utilitaires déjà présentes dans les classes de base.  
  
 Le modèle est le suivant :  
  
- Un **Gestionnaire Add*EventName*** de méthode avec deux paramètres. Le premier paramètre est l’instance à laquelle le gestionnaire d’événements est ajouté. Le deuxième paramètre est le gestionnaire d’événements à ajouter. La méthode doit être `public` et `static`, sans valeur de retour.  
  
- Un gestionnaire de méthode **Remove*EventName*** avec deux paramètres. Le premier paramètre est l’instance à partir de laquelle le gestionnaire d’événements est supprimé. Le deuxième paramètre est le gestionnaire d’événements à supprimer. La méthode doit être `public` et `static`, sans valeur de retour.  
  
 La méthode d’accesseur **Add*EventName*Handler** facilite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] le traitement lorsque des attributs de gestionnaire d’événements attachés sont déclarés sur un élément. Les méthodes de gestionnaire **Add*EventName*** et **Remove*NomÉvénement*** permettent également d’accéder au code du magasin de gestionnaires d’événements pour l’événement attaché.  
  
 Ce modèle général n’est pas encore assez précis pour une implémentation pratique dans un framework, car toute implémentation d’un lecteur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] donné peut avoir des méthodes différentes pour identifier les événements sous-jacents dans le langage et l’architecture de prise en charge. C’est l’une des raisons qui [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémente les événements attachés en tant qu’événements routés; l’identificateur à utiliser pour<xref:System.Windows.RoutedEvent>un événement () est déjà [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] défini par le système d’événements. De plus, le routage d’un événement est une extension d’implémentation naturelle pour le concept de niveau de langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d’un événement attaché.  
  
 L’implémentation du **Gestionnaire Add*EventName*** pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un événement attaché consiste à appeler <xref:System.Windows.UIElement.AddHandler%2A> le avec l’événement routé et le gestionnaire comme arguments.  
  
 Cette stratégie d’implémentation et le système d’événement routé en général restreignent la gestion des événements <xref:System.Windows.UIElement> attachés à <xref:System.Windows.ContentElement> des classes dérivées ou à des classes <xref:System.Windows.UIElement.AddHandler%2A> dérivées, car seules ces classes ont des implémentations.  
  
 Par exemple, le code suivant définit l’événement attaché `NeedsCleaning` sur la classe propriétaire `Aquarium` à l’aide de la stratégie d’événement attaché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui consiste à déclarer l’événement attaché en tant qu’événement routé.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Notez que la méthode utilisée pour établir le champ d’identificateur d’événement attaché <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>,, est en fait la même méthode que celle utilisée pour enregistrer un événement routé non attaché. Les événements attachés et les événements routés sont tous inscrits dans un magasin interne centralisé. Cette implémentation du magasin d’événements rend possible la considération conceptuelle des « événements en tant qu’interface » traitée dans [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Déclenchement d’un événement attaché WPF  
 En règle générale, vous n’avez pas besoin de déclencher les événements attachés définis par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir de votre code. Ces événements suivent le modèle conceptuel «service» général, et les classes de service <xref:System.Windows.Input.InputManager> telles que sont chargées de déclencher les événements.  
  
 Toutefois, si vous définissez un événement attaché personnalisé basé sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le modèle d’événements attachés de base sur <xref:System.Windows.RoutedEvent>, vous pouvez <xref:System.Windows.UIElement.RaiseEvent%2A> utiliser pour déclencher un événement attaché à <xref:System.Windows.UIElement> partir <xref:System.Windows.ContentElement>de n’importe quel ou. Le déclenchement d’un événement routé (attaché ou non) requiert que vous déclariez un élément particulier dans l’arborescence d’éléments comme source d’événement; cette source est signalée comme <xref:System.Windows.UIElement.RaiseEvent%2A> appelant. Votre service est chargé de déterminer quel est l’élément signalé en tant que source dans l’arborescence  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des événements routés](routed-events-overview.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
- [XAML et classes personnalisées pour WPF](xaml-and-custom-classes-for-wpf.md)
