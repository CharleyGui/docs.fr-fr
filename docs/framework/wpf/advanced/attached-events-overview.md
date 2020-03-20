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
ms.openlocfilehash: e125c9a57090049f4319da96c7004f06606d0147
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141560"
---
# <a name="attached-events-overview"></a>Vue d'ensemble des événements attachés

Extensible Application Markup Language (XAML) définit un composant linguistique et un type d’événement appelé *un événement ci-joint*. Le concept d’un événement attaché vous permet d’ajouter un gestionnaire pour un événement particulier à un élément arbitraire plutôt qu’à un élément qui définit réellement l’événement ou qui en hérite. Dans ce cas, ni l’objet qui déclenche potentiellement l’événement, ni l’instance de gestion de destination ne définit ou ne « détient » l’événement.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique suppose que vous avez lu [Vue d’ensemble des événements routés](routed-events-overview.md) et [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Syntax"></a>
## <a name="attached-event-syntax"></a>Syntaxe d’un événement attaché  
 Les événements ci-joints ont une syntaxe XAML et un modèle de codage qui doit être utilisé par le code de sauvegarde afin de soutenir l’utilisation de l’événement ci-joint.  
  
 Dans la syntaxe XAML, l’événement ci-joint est spécifié non seulement par son nom d’événement, mais par son propre type plus le nom de l’événement, séparé par un point (.). Comme le nom de l’évènement est qualifié avec le nom de son type propriétaire, la syntaxe de l’événement attaché permet à celui-ci d’être attaché à tout élément pouvant être instancié.  
  
 Par exemple, ce qui suit est la syntaxe XAML pour attacher un gestionnaire pour un événement sur mesure `NeedsCleaning` ci-joint:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Notez le préfixe `aqua:`. Ce préfixe est nécessaire dans le cas présent, car l’événement attaché est un événement personnalisé qui provient d’un fichier xmlns mappé personnalisé.  
  
<a name="WPFImplements"></a>
## <a name="how-wpf-implements-attached-events"></a>Comment WPF implémente des événements attachés

Dans WPF, les événements <xref:System.Windows.RoutedEvent> attachés sont soutenus par un champ et sont acheminés à travers l’arbre après qu’ils sont soulevés. En général, la source de l’événement attaché (l’objet qui déclenche l’événement) est une source système ou de service. L’objet qui exécute le code qui déclenche l’événement ne fait donc pas directement partie de l’arborescence d’éléments.  
  
<a name="Scenarios"></a>
## <a name="scenarios-for-attached-events"></a>Scénarios pour les événements attachés  
 Dans WPF, des événements ci-joints sont présents dans certains domaines caractéristiques où <xref:System.Windows.Input.Mouse> il <xref:System.Windows.Controls.Validation> existe une abstraction au niveau du service, comme pour les événements activés par la classe statique ou la classe. Les classes qui interagissent avec le service, ou qui l’utilisent, peuvent employer l’événement dans la syntaxe de l’événement attaché ou choisir de surfacer l’événement attaché en tant qu’événement routé faisant partie de la façon dont la classe intègre les fonctionnalités du service.  
  
 Bien que WPF définisse un certain nombre d’événements ci-joints, les scénarios où vous utiliserez ou gérerez directement l’événement ci-joint sont très limités. En général, l’événement ci-joint sert un but d’architecture, mais est ensuite transmis à un événement non-attaché (soutenu par un événement CLR "wrapper") événement acheminé.  
  
 Par exemple, <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> l’événement sous-jacent ci-joint <xref:System.Windows.UIElement> peut <xref:System.Windows.UIElement.MouseDown> plus <xref:System.Windows.UIElement> facilement être géré sur n’importe quel donné en utilisant sur cela plutôt que de traiter avec la syntaxe d’événement ci-joint soit dans XAML ou code. L’événement attaché a une fonction d’architecture, car il permet l’extension future des périphériques d’entrée. L’appareil hypothétique n’aurait qu’à soulever <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> afin de simuler <xref:System.Windows.Input.Mouse> l’entrée de la souris, et n’aurait pas besoin de dériver de le faire. Toutefois, ce scénario implique le traitement du code des événements, et la gestion XAML de l’événement ci-joint n’est pas pertinente à ce scénario.  
  
<a name="Handling"></a>
## <a name="handling-an-attached-event-in-wpf"></a>Gestion d’un événement attaché dans WPF  
 La gestion d’un événement attaché et le code du gestionnaire que vous allez écrire sont essentiellement les mêmes que pour un événement routé.  
  
 En général, un événement joint WPF n’est pas très différent d’un événement Acheminé WPF. Les différences sont la façon dont l’événement est source et comment il est exposé par une classe en tant que membre (qui affecte également la syntaxe de gestionnaire XAML).  
  
 Toutefois, comme nous l’avons mentionné précédemment, les événements ci-joints WPF existants ne sont pas particulièrement destinés à la manipulation dans WPF. Le plus souvent, le but de l’événement est de permettre à un élément composé de signaler un état à un élément parent au moment de la composition. Dans ce cas, l’événement est généralement déclenché dans du code et compte également sur une gestion de classe dans la classe parente appropriée. Par exemple, les <xref:System.Windows.Controls.Primitives.Selector> éléments dans un <xref:System.Windows.Controls.Primitives.Selector.Selected> sont censés soulever l’événement ci-joint, qui est ensuite de classe gérée par la <xref:System.Windows.Controls.Primitives.Selector> classe, puis potentiellement converti par la <xref:System.Windows.Controls.Primitives.Selector> classe en un événement acheminé différent, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. Pour plus d’informations sur les événements routés et la gestion de classe, consultez [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>
## <a name="defining-your-own-attached-events-as-routed-events"></a>Définition de vos propres événements attachés en tant qu’événements routés  
 Si vous êtes dérivé de classes de base WPF communes, vous pouvez mettre en œuvre vos propres événements attachés en incluant certaines méthodes de modèle dans votre classe et en utilisant des méthodes d’utilité qui sont déjà présents sur les classes de base.  
  
 Le modèle est le suivant :  
  
- Une méthode __Ajouter*EventName*Handler__ avec deux paramètres. Le premier paramètre est l’instance à laquelle le gestionnaire d’événements est ajouté. Le deuxième paramètre est le gestionnaire d’événements à ajouter. La méthode `public` doit `static`être et , sans valeur de retour.  
  
- Une méthode __Supprimer*EventName*Handler__ avec deux paramètres. Le premier paramètre est l’instance à partir de laquelle le gestionnaire d’événements est supprimé. Le deuxième paramètre est le gestionnaire d’événements à supprimer. La méthode `public` doit `static`être et , sans valeur de retour.  
  
 La méthode __d’accesseur Add*EventName*Handler__ facilite le traitement XAML lorsque les attributs de gestionnaire d’événements ci-joints sont déclarés sur un élément. Les méthodes __Add*EventName*Handler__ et __Supprimer*EventName*Handler__ permettent également l’accès au code du magasin de gestionnaire d’événements pour l’événement ci-joint.  
  
 Ce modèle général n’est pas encore assez précis pour une mise en œuvre pratique dans un cadre, car toute mise en œuvre donnée de lecteur XAML pourrait avoir différents schémas pour identifier les événements sous-jacents dans le langage et l’architecture de soutien. C’est l’une des raisons pour lesquelles WPF met en œuvre des événements connexes comme des événements acheminés; l’identifiant à utiliser<xref:System.Windows.RoutedEvent>pour un événement ( ) est déjà défini par le système d’événements WPF. En outre, l’itinéraire d’un événement est une extension de mise en œuvre naturelle sur le concept de niveau linguistique XAML d’un événement ci-joint.  
  
 La mise en œuvre __add*EventName*__ Handler <xref:System.Windows.UIElement.AddHandler%2A> pour un événement joint WPF consiste à appeler l’événement acheminé et gestionnaire comme arguments.  
  
 Cette stratégie de mise en œuvre et le <xref:System.Windows.UIElement> système d’événements acheminés en général limitent la gestion des événements attachés aux classes dérivées ou <xref:System.Windows.ContentElement> aux classes dérivées, parce que seules ces classes ont des <xref:System.Windows.UIElement.AddHandler%2A> implémentations.  
  
 Par exemple, le code `NeedsCleaning` suivant définit l’événement ci-joint sur la classe `Aquarium`propriétaire, en utilisant la stratégie de l’événement ci-joint WPF de déclarer l’événement ci-joint comme un événement acheminé.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Notez que la méthode utilisée pour <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>établir le champ d’identification d’événement ci-joint, , est en fait la même méthode qui est utilisée pour enregistrer un événement acheminé non-attaché. Les événements attachés et les événements routés sont tous inscrits dans un magasin interne centralisé. Cette implémentation du magasin d’événements rend possible la considération conceptuelle des « événements en tant qu’interface » traitée dans [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
<a name="Raising"></a>
## <a name="raising-a-wpf-attached-event"></a>Déclenchement d’un événement attaché WPF  
 Vous n’avez généralement pas besoin de soulever les événements ci-joints définis par le WPF existants à partir de votre code. Ces événements suivent le modèle conceptuel général de <xref:System.Windows.Input.InputManager> « service », et les classes de service telles que sont responsables de soulever les événements.  
  
 Toutefois, si vous définissez un événement personnalisé ci-joint basé <xref:System.Windows.RoutedEvent>sur le <xref:System.Windows.UIElement.RaiseEvent%2A> modèle WPF de <xref:System.Windows.UIElement> baser les événements ci-joints sur , vous pouvez utiliser pour soulever un événement attaché de n’importe quel ou <xref:System.Windows.ContentElement>. L’élévation d’un événement acheminé (attaché ou non) exige que vous déclarez un élément particulier dans l’arbre d’élément comme source d’événement ; cette source est <xref:System.Windows.UIElement.RaiseEvent%2A> signalée comme l’appelant. Votre service est chargé de déterminer quel est l’élément signalé en tant que source dans l’arborescence  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des événements routés](routed-events-overview.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
- [XAML et les classes personnalisées pour WPF](xaml-and-custom-classes-for-wpf.md)
