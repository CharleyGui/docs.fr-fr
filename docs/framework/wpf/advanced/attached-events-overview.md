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
ms.openlocfilehash: 2b3f659a5916aa63d510959583e8ae038085460c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655504"
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
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], joint les événements sont soutenus par une <xref:System.Windows.RoutedEvent> champ et sont routés via l’arborescence après leur déclenchement. En général, la source de l’événement attaché (l’objet qui déclenche l’événement) est une source système ou de service. L’objet qui exécute le code qui déclenche l’événement ne fait donc pas directement partie de l’arborescence d’éléments.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scénarios pour les événements attachés  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], joint les événements sont présentes dans certaines zones de fonctionnalités où figure l’abstraction de niveau de service, comme pour les événements activés par la méthode statique <xref:System.Windows.Input.Mouse> classe ou la <xref:System.Windows.Controls.Validation> classe. Les classes qui interagissent avec le service, ou qui l’utilisent, peuvent employer l’événement dans la syntaxe de l’événement attaché ou choisir de surfacer l’événement attaché en tant qu’événement routé faisant partie de la façon dont la classe intègre les fonctionnalités du service.  
  
 Bien que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définisse un certain nombre d’événements attachés, les scénarios dans lesquels vous utilisez ou gérez directement l’événement attaché sont très limités. En général, l’événement attaché a un but architectural, mais il est ensuite transmis à un événement routé non attaché (associé à un « wrapper » d’événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]).  
  
 Par exemple, de la sous-jacent d’un événement attaché <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> peuvent être plus facilement géré sur n’importe quel donné <xref:System.Windows.UIElement> à l’aide de <xref:System.Windows.UIElement.MouseDown> sur qui <xref:System.Windows.UIElement> plutôt que le traitement soit avec la syntaxe de l’événement attaché dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code. L’événement attaché a une fonction d’architecture, car il permet l’extension future des périphériques d’entrée. Le périphérique hypothétique suffit à déclencher <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> pour simuler l’entrée de la souris et ne doit pas dériver de <xref:System.Windows.Input.Mouse> à le faire. Toutefois, ce scénario implique une gestion du code des événements, et une gestion [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de l’événement attaché n’est pas pertinente dans ce cas.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Gestion d’un événement attaché dans WPF  
 La gestion d’un événement attaché et le code du gestionnaire que vous allez écrire sont essentiellement les mêmes que pour un événement routé.  
  
 En général, un événement attaché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’est pas très différent d’un événement routé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Les différences portent sur la provenance de l’événement et sur la façon dont il est exposé par une classe en tant que membre (ce qui affecte également la syntaxe du gestionnaire [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]).  
  
 Toutefois, comme indiqué précédemment, les événements attachés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants ne sont pas particulièrement destinés à être gérés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le plus souvent, le but de l’événement est de permettre à un élément composé de signaler un état à un élément parent au moment de la composition. Dans ce cas, l’événement est généralement déclenché dans du code et compte également sur une gestion de classe dans la classe parente appropriée. Par exemple, les éléments dans un <xref:System.Windows.Controls.Primitives.Selector> sont supposés déclencher le fichier joint <xref:System.Windows.Controls.Primitives.Selector.Selected> événement, qui est ensuite classe géré par le <xref:System.Windows.Controls.Primitives.Selector> classe et puis éventuellement converti en la <xref:System.Windows.Controls.Primitives.Selector> classe dans un événement routé différent, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Pour plus d’informations sur les événements routés et la gestion de classe, consultez [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Définition de vos propres événements attachés en tant qu’événements routés  
 Si vous effectuez une dérivation à partir de classes de base [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] communes, vous pouvez implémenter vos propres événements attachés en incluant certaines méthodes de modèle dans votre classe et en utilisant des méthodes utilitaires déjà présentes dans les classes de base.  
  
 Le modèle est le suivant :  
  
- Une méthode **ajouter*EventName*gestionnaire** avec deux paramètres. Le premier paramètre est l’instance à laquelle le Gestionnaire d’événements est ajouté. Le deuxième paramètre est le Gestionnaire d’événements à ajouter. La méthode doit être `public` et `static`, sans valeur de retour.  
  
- Une méthode **supprimer*EventName*gestionnaire** avec deux paramètres. Le premier paramètre est l’instance à partir de laquelle le Gestionnaire d’événements est supprimé. Le deuxième paramètre est le Gestionnaire d’événements à supprimer. La méthode doit être `public` et `static`, sans valeur de retour.  
  
 Le **ajouter*EventName*gestionnaire** facilite la méthode d’accesseur le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] traitement lorsque attaché de gestionnaire d’événements sont les attributs déclarés sur un élément. Le **ajouter*EventName*gestionnaire** et **supprimer*EventName*gestionnaire** méthodes permettent également d’accès du code dans le magasin de gestionnaire d’événements pour le événement attaché.  
  
 Ce modèle général n’est pas encore assez précis pour une implémentation pratique dans un framework, car toute implémentation d’un lecteur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] donné peut avoir des méthodes différentes pour identifier les événements sous-jacents dans le langage et l’architecture de prise en charge. Il s’agit d’une des raisons qui [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] événements implémente attaché en tant qu’événements routés ; l’identificateur à utiliser pour un événement (<xref:System.Windows.RoutedEvent>) est déjà définie par le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système d’événements. De plus, le routage d’un événement est une extension d’implémentation naturelle pour le concept de niveau de langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d’un événement attaché.  
  
 Le **ajouter*EventName*gestionnaire** implémentation pour un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] événement attaché consiste à appeler le <xref:System.Windows.UIElement.AddHandler%2A> avec l’événement routé et le gestionnaire en tant qu’arguments.  
  
 Cette stratégie d’implémentation et le système d’événement routé en général restreignent la gestion pour les événements attachés aux soit <xref:System.Windows.UIElement> classes dérivées ou <xref:System.Windows.ContentElement> les classes dérivées, car seules ces classes ont <xref:System.Windows.UIElement.AddHandler%2A> implémentations.  
  
 Par exemple, le code suivant définit l’événement attaché `NeedsCleaning` sur la classe propriétaire `Aquarium` à l’aide de la stratégie d’événement attaché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui consiste à déclarer l’événement attaché en tant qu’événement routé.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Notez que la méthode utilisée pour établir le champ d’identificateur de l’événement attaché, <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, est en fait la même méthode qui est utilisée pour inscrire un événement routé non attaché. Les événements attachés et les événements routés sont tous inscrits dans un magasin interne centralisé. Cette implémentation du magasin d’événements rend possible la considération conceptuelle des « événements en tant qu’interface » traitée dans [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Déclenchement d’un événement attaché WPF  
 En règle générale, vous n’avez pas besoin de déclencher les événements attachés définis par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir de votre code. Ces événements suivent le modèle conceptuel général « service » et comme les classes de service <xref:System.Windows.Input.InputManager> sont chargées de déclencher les événements.  
  
 Toutefois, si vous définissez un événement attaché personnalisé basé sur le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle de baser les événements attachés sur <xref:System.Windows.RoutedEvent>, vous pouvez utiliser <xref:System.Windows.UIElement.RaiseEvent%2A> pour déclencher un événement attaché à partir d’un <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement>. Le déclenchement d’un événement routé (attaché ou non) nécessite que vous déclarez un élément particulier dans l’arborescence d’éléments comme la source d’événements ; Cette source est signalée comme le <xref:System.Windows.UIElement.RaiseEvent%2A> appelant. Votre service est chargé de déterminer quel est l’élément signalé en tant que source dans l’arborescence  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des événements routés](routed-events-overview.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
- [XAML et classes personnalisées pour WPF](xaml-and-custom-classes-for-wpf.md)
