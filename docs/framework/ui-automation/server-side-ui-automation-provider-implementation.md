---
title: Implémentation de fournisseur UI Automation côté serveur
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: 8a52d84f7152b9cb431ad0aa97c88b143463be2d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789621"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Implémentation de fournisseur UI Automation côté serveur

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).

Cette section explique comment implémenter un fournisseur UI Automation côté serveur pour un contrôle personnalisé.

L’implémentation pour les éléments Windows Presentation Foundation (WPF) et les éléments non WPF (tels que ceux conçus pour Windows Forms) est fondamentalement différente. Les éléments WPF assurent la prise en charge de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] par le biais d’une classe dérivée de <xref:System.Windows.Automation.Peers.AutomationPeer>. Les éléments non-WPF assurent la prise en charge via des implémentations d’interfaces de fournisseur.

<a name="Security_Considerations"></a>

## <a name="security-considerations"></a>Considérations sur la sécurité

Les fournisseurs doivent être écrits de manière à pouvoir travailler dans un environnement de confiance partielle. Étant donné qu'UIAutomationClient.dll n'est pas configuré pour s'exécuter avec un niveau de confiance partielle, le code de votre fournisseur ne doit pas référencer cet assembly. S'il le fait, le code risque de s'exécuter dans un environnement de confiance totale mais d'échouer dans un environnement de confiance partielle.

En particulier, n'utilisez pas de champs provenant de classes d'UIAutomationClient.dll, tels que ceux d' <xref:System.Windows.Automation.AutomationElement>. Utilisez plutôt les champs de classes équivalents, tels que les <xref:System.Windows.Automation.AutomationElementIdentifiers>, dans UIAutomationTypes.dll.

<a name="Provider_Implementation_by_WPF_Elements"></a>

## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Implémentation de fournisseur par les éléments Windows Presentation Foundation

Pour plus d'informations sur ce sujet, consultez [UI Automation d'un contrôle personnalisé WPF](../wpf/controls/ui-automation-of-a-wpf-custom-control.md).

<a name="Provider_Implementation_by_non_WPF_Elements"></a>

## <a name="provider-implementation-by-non-wpf-elements"></a>Implémentation de fournisseur par des éléments non-WPF

Les contrôles personnalisés qui ne font pas partie de l’infrastructure WPF, mais qui sont écrits en code managé (le plus souvent, il s’agit de contrôles Windows Forms), assurent la prise en charge de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] en implémentant des interfaces. Chaque élément doit implémenter au moins une des interfaces répertoriées dans le premier tableau de la section suivante. De plus, si l'élément prend en charge un ou plusieurs modèles de contrôle, il doit implémenter l'interface appropriée pour chaque modèle de contrôle.

Le projet de votre fournisseur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doit référencer les assemblys suivants :

- UIAutomationProviders.dll

- UIAutomationTypes.dll

- WindowsBase.dll

<a name="Provider_Interfaces"></a>

### <a name="provider-interfaces"></a>Interfaces de fournisseur

Chaque fournisseur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doit implémenter l'une des interfaces suivantes.

|Interface|Description|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Fournit les fonctionnalités pour un contrôle simple hébergé dans une fenêtre, y compris une prise en charge pour les modèles de contrôle et les propriétés.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Hérite de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Ajoute des fonctionnalités pour un élément d'un contrôle complexe, y compris celles permettant de naviguer dans le fragment, de définir le focus et de retourner le rectangle englobant de l'élément.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Hérite de <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Ajoute des fonctionnalités pour l'élément racine d'un contrôle complexe, y compris la localisation d'un élément enfant à des coordonnées spécifiées et la définition de l'état du focus pour l'ensemble du contrôle.|

Les interfaces suivantes fournissent des fonctionnalités supplémentaires, mais leur implémentation n'est pas obligatoire.

|Interface|Description|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Permet au fournisseur de suivre des demandes pour des événements.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Active le repositionnement d’éléments basés sur une fenêtre dans l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] d’un fragment.|

Toutes les autres interfaces de l’espace de noms <xref:System.Windows.Automation.Provider> concernent la prise en charge du modèle de contrôle.

<a name="Requirements_for_Non_WPF_Providers"></a>

### <a name="requirements-for-non-wpf-providers"></a>Spécifications pour les fournisseurs non-WPF

Pour communiquer avec [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], votre contrôle doit implémenter les principaux domaines de fonctionnalités suivants :

|Fonctionnalité|Implémentation|
|-------------------|--------------------|
|Exposer le fournisseur à [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|En réponse à un message WM_GETOBJECT envoyé à la fenêtre de contrôle, retournez l'objet qui implémente <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (ou une interface dérivée). Pour les fragments, il doit s'agir du fournisseur pour la racine du fragment.|
|Fournir des valeurs de propriété|Implémentez <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> pour fournir ou substituer des valeurs.|
|Permettre au client d'interagir avec le contrôle|Implémentez des interfaces qui prennent en charge des modèles de contrôle, tels qu’ <xref:System.Windows.Automation.Provider.IInvokeProvider>. Retournez ces fournisseurs de modèles dans votre implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|
|Déclencher des événements|Appelez une des méthodes statiques d' <xref:System.Windows.Automation.Provider.AutomationInteropProvider> pour déclencher un événement que le client pourra écouter.|
|Activer la navigation et le focus dans un fragment|Implémentez <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> pour chaque élément du fragment (sauf pour les éléments qui ne font pas partie d'un fragment).|
|Activer le focus et l'emplacement d'un élément enfant dans un fragment|Implémentez <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Sauf pour les éléments qui ne sont pas des racines de fragment.)|

<a name="Property_Values_in_Non_WPF_Providers"></a>

### <a name="property-values-in-non-wpf-providers"></a>Valeurs de la propriété dans les fournisseurs non-WPF

Les fournisseurs[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour les contrôles personnalisés doivent prendre en charge certaines propriétés qui peuvent être utilisées aussi bien par le système d'automatisation que par les applications clientes. Pour les éléments hébergés dans des fenêtres (HWND), [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] peut récupérer certaines propriétés depuis un fournisseur de fenêtre par défaut, mais doit en obtenir d'autres du fournisseur personnalisé.

Habituellement, les fournisseurs de contrôles basés sur HWND n'ont pas besoin de fournir les propriétés suivantes (identifiées par des valeurs de champ) :

- <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>

> [!NOTE]
> La <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> d'un simple élément ou d'une racine de fragment hébergé dans une fenêtre est obtenue depuis la fenêtre ; toutefois, les éléments fragments sous la racine (tels que des éléments de liste dans une zone de liste) doivent fournir leurs propres identificateurs. Pour plus d'informations, consultez <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.
>
> Le <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> doit être retourné pour les fournisseurs hébergés dans un contrôle Windows Forms. Dans ce cas, le fournisseur de fenêtre par défaut ne pourra peut-être pas récupérer la bonne valeur.
>
> La <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> est généralement fournie par le fournisseur hôte. Par exemple, si un contrôle personnalisé est dérivé de <xref:System.Windows.Forms.Control>, le nom est dérivé de la propriété `Text` du contrôle.

Pour obtenir un exemple de code, consultez [Return Properties from a UI Automation Provider](return-properties-from-a-ui-automation-provider.md).

<a name="Events_in_Non_WPF_Providers"></a>

### <a name="events-in-non-wpf-providers"></a>Événements dans les fournisseurs non-WPF

Les fournisseurs[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doivent déclencher des événements pour informer les applications clientes des modifications de l'état de l'interface utilisateur. Les méthodes suivantes sont utilisées pour déclencher des événements.

|Méthode|Description|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Déclenche différents événements, y compris les événements déclenchés par les modèles de contrôle.|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Déclenche un événement quand une propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a été modifiée.|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Déclenche un événement quand la structure de l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a été modifiée ; par exemple, à l'occasion de la suppression ou de l'ajout d'un élément.|

Le but d'un événement est d'informer le client que quelque chose est en train de se passer dans l' [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], que l'activité soit ou non déclenchée par le système [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lui-même. Par exemple, l'événement identifié par <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> doit être déclenché chaque fois que le contrôle est appelé, via l'entrée d'utilisateur directe ou par l'application cliente appelant <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.

Pour optimiser les performances, un fournisseur peut déclencher des événements de manière sélective ou ne pas en déclencher du tout si aucune application cliente n'est enregistrée pour les recevoir. Les méthodes suivantes sont utilisées pour l'optimisation.

|Méthode|Description|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Cette propriété statique spécifie si des applications clientes se sont abonnées à des événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|L'implémentation de cette interface par le fournisseur sur une racine de fragment lui permet d'être avertie quand des clients enregistrent et annulent l'enregistrement de gestionnaires d'événements pour les événements situés sur le fragment.|

<a name="Non_WPF_Provider_Navigation"></a>

### <a name="non-wpf-provider-navigation"></a>Navigation d'un fournisseur non-WPF

Les fournisseurs de simples contrôles tels qu'un bouton personnalisé hébergé dans une fenêtre (HWND) n'ont pas besoin de prendre en charge la navigation dans l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . La navigation vers et depuis l'élément est contrôlée par le fournisseur par défaut de la fenêtre hôte, ce qui est spécifié dans l'implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. Quand vous implémentez un fournisseur pour un contrôle personnalisé complexe, vous devez toutefois prendre en charge la navigation entre le nœud racine du fragment et ses descendants, et entre nœuds frères.

> [!NOTE]
> Les éléments d'un fragment autre que la racine doivent retourner une référence `null` depuis <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, car ils ne sont pas hébergés directement dans une fenêtre et aucun fournisseur par défaut ne peut prendre en charge la navigation vers et depuis ces éléments.

La structure du fragment est déterminée par votre implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. Pour chaque direction possible à partir de chaque fragment, cette méthode retourne l'objet fournisseur de l'élément dans cette direction. S'il n'y a aucun élément dans cette direction, la méthode retourne une référence `null` .

La racine du fragment ne prend en charge la navigation que vers les éléments enfants. Par exemple, une zone de liste retourne le premier élément de la liste quand la direction est <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>, et le dernier élément quand la direction est <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. La racine du fragment ne prend pas en charge la navigation vers un parent ou des frères ; cela est géré par le fournisseur de fenêtre hôte.

Les éléments d'un fragment qui ne sont pas la racine doivent prendre en charge la navigation vers le parent et tous leurs frères et enfants.

<a name="Non_WPF_Provider_Reparenting"></a>

### <a name="non-wpf-provider-reparenting"></a>Définition de l'état de parent d'un fournisseur non-WPF

Les fenêtres indépendantes sont en fait des fenêtres de niveau supérieur ; elles apparaissent donc par défaut dans l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] en tant qu'enfants du bureau. Dans de nombreux cas, toutefois, les fenêtres indépendantes sont logiquement des enfants d'autres contrôles. Par exemple, la liste déroulante d'une zone de liste modifiable est logiquement un enfant de la zone de liste modifiable. De la même façon, une fenêtre indépendante de menu est logiquement un enfant du menu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] assure la prise en charge permettant de définir un nouveau parent pour les fenêtres indépendantes afin qu'elles apparaissent en tant qu'enfants du contrôle associé.

Pour définir l'état de changement de parent d'une fenêtre indépendante :

1. Créez un fournisseur pour la fenêtre indépendante. Pour cela, il faut que la classe de la fenêtre indépendante soit connue à l'avance.

2. Implémentez toutes les propriétés et tous les modèles habituels pour cette fenêtre, comme s'il s'agissait d'un contrôle.

3. Implémentez la propriété <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> pour qu'elle retourne la valeur obtenue depuis <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, où le paramètre est le handle de fenêtre de la fenêtre indépendante.

4. Implémentez <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pour la fenêtre indépendante et son parent afin que la navigation soit correctement contrôlée du parent logique aux enfants logiques, et entre enfants de mêmes parents.

Quand [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rencontre la fenêtre indépendante, il reconnaît que cette navigation est substituée à la valeur par défaut et il ignore la fenêtre indépendante quand elle est rencontrée en tant qu'enfant du bureau. À la place, le nœud sera accessible uniquement via le fragment.

La définition de l'état de parent n'est pas appropriée quand un contrôle peut héberger une fenêtre de n'importe quelle classe. Par exemple, un contrôle rebar peut héberger n'importe quel type de HWND dans ses bandes. Pour gérer ces cas, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prend en charge une autre forme de réadressage HWND, comme décrit dans la section suivante.

<a name="Non_WPF_Provider_Repositioning"></a>

### <a name="non-wpf-provider-repositioning"></a>Repositionnement d'un fournisseur non-WPF

Les fragments[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] peuvent contenir deux éléments ou plus, tous contenus dans une fenêtre (HWND). Comme chaque HWND possède son propre fournisseur par défaut qui considère le HWND comme un enfant d’un HWND contenant, l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] affiche, par défaut, les HWND dans le fragment en tant qu’enfants de la fenêtre parente. Dans la plupart des cas, ce comportement est conseillé, mais il peut parfois porter à confusion, car il ne correspond pas à la structure logique de l' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].

Le contrôle rebar en est un bon exemple. Un rebar contient des bandes, qui peuvent, elles aussi, contenir un contrôle basé sur HWND, tel qu'une barre d'outils, une zone d'édition ou une zone de liste modifiable. Le fournisseur de fenêtre par défaut du HWND rebar considère les HWND du contrôle de bandes comme des enfants, tandis que le fournisseur rebar considère les bandes comme des enfants. Étant donné que le fournisseur HWND et le fournisseur rebar travaillent en tandem et qu'ils combinent leurs enfants, les bandes et les contrôles basés sur HWND apparaissent comme les enfants du rebar. Toutefois, seules les bandes devraient logiquement apparaître comme les enfants du rebar et chaque fournisseur de bandes devrait être associé au fournisseur HWND par défaut pour le contrôle qu'il contient.

Pour cela, le fournisseur de la racine du fragment pour le rebar expose un jeu d'enfants représentant les bandes. Chaque bande possède un seul fournisseur qui peut exposer des propriétés et des modèles. Dans son implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, le fournisseur de bandes retourne le fournisseur de fenêtre par défaut pour le HWND de contrôle qu'il obtient en appelant <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, en passant le handle de fenêtre du contrôle. Enfin, le fournisseur de la racine du fragment pour le rebar implémente l'interface <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> et, dans son implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> , il retourne le fournisseur de bandes approprié pour le contrôle contenu dans le HWND spécifié.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des fournisseurs UI Automation](ui-automation-providers-overview.md)
- [Exposer un fournisseur UI Automation côté serveur](expose-a-server-side-ui-automation-provider.md)
- [Retourner les propriétés d’un fournisseur UI Automation](return-properties-from-a-ui-automation-provider.md)
- [Déclencher des événements à partir d’un fournisseur UI Automation](raise-events-from-a-ui-automation-provider.md)
- [Activer la navigation dans un fournisseur de fragment UI Automation](enable-navigation-in-a-ui-automation-fragment-provider.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
