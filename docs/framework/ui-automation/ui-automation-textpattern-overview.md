---
title: Vue d'ensemble de TextPattern d'UI Automation
description: Lisez une vue d’ensemble du modèle de contrôle TextPattern dans UI Automation. Ce modèle de contrôle expose le contenu textuel d’un contrôle, notamment le format et le style.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: 986b601bbd212582c09c559a9bb22983ba59fa17
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924667"
---
# <a name="ui-automation-textpattern-overview"></a>Vue d'ensemble de TextPattern d'UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).

Cette présentation décrit comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour exposer le contenu textuel, y compris les attributs de mise en forme et de style, des contrôles de texte dans les plateformes prises en charge par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Ces contrôles incluent, mais ne sont pas limités à, l’infrastructure Microsoft .NET et, ainsi <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> que leurs équivalents Win32.

L’exposition du contenu textuel d’un contrôle s’effectue via l’utilisation du modèle de contrôle <xref:System.Windows.Automation.TextPattern> , qui représente le contenu d’un conteneur de texte sous forme d’un flux de texte. En retour, <xref:System.Windows.Automation.TextPattern> requiert la prise en charge de la classe <xref:System.Windows.Automation.Text.TextPatternRange> pour exposer les attributs de mise en forme et de style. <xref:System.Windows.Automation.Text.TextPatternRange> prend en charge <xref:System.Windows.Automation.TextPattern> en représentant les étendues de texte disjointes contiguës ou multiples dans un conteneur de texte par une collection de points de terminaison <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> et <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> . <xref:System.Windows.Automation.Text.TextPatternRange> prend en charge des fonctionnalités telles que la sélection, la comparaison, la récupération et la traversée.

> [!NOTE]
> Les classes <xref:System.Windows.Automation.TextPattern> ne permettent pas d'insérer ou de modifier du texte. Toutefois, selon le contrôle, cette opération peut être effectuée par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> ou via une entrée directe au clavier. Pour obtenir un exemple, consultez [TextPattern Insert Text Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) .

Les fonctionnalités décrites dans cette vue d'ensemble sont indispensables aux fournisseurs de technologie d'assistance et à leurs utilisateurs finaux. Les technologies d'assistance peuvent utiliser [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] afin de collecter des informations complètes sur la mise en forme du texte pour l'utilisateur et offrir une navigation par programmation et une sélection de texte par <xref:System.Windows.Automation.Text.TextUnit> (caractère, mot, ligne ou paragraphe).

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>Différences entre TextPattern d'UI Automation et Text Services Framework

Text Services Framework (TSF) est une infrastructure système simple et évolutive qui permet les services de langage naturel et l’entrée de texte avancée sur le bureau et dans les applications. En plus de fournir aux applications des interfaces à l'aide desquelles elles peuvent exposer leur magasin de texte, TSF prend en charge les métadonnées de ce magasin de texte.

Toutefois, TSF a été conçu pour les applications qui doivent injecter des entrées dans des scénarios contextuels, tandis que <xref:System.Windows.Automation.TextPattern> est une solution en lecture seule (avec la solution de contournement limitée indiquée ci-dessus) destinée à fournir un accès optimisé à un magasin de texte pour les lecteurs d’écran et les appareils en braille.

En résumé, les technologies accessibles qui requièrent un accès en lecture seule à un magasin de texte peuvent utiliser <xref:System.Windows.Automation.TextPattern> , mais elles ont besoin des fonctionnalités plus complexes de TSF pour les entrées contextuelles.

<a name="Control_Types"></a>

## <a name="control-types"></a>Types de contrôles

### <a name="text"></a>Texte

Le contrôle Text est l'élément de base représentant une partie du texte à l'écran.

Un contrôle de texte autonome peut être utilisé comme étiquette ou texte statique sur un formulaire. Les contrôles Text peuvent également être intégrés à la structure d'un élément <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> ou <xref:System.Windows.Automation.ControlType.DataItem>.

> [!NOTE]
> Il est possible que les contrôles de texte n’apparaissent pas dans l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (consultez [UI Automation Tree Overview](ui-automation-tree-overview.md)). En effet, les contrôles Text sont souvent affichés via la propriété Name d'un autre contrôle. Par exemple, le texte utilisé pour étiqueter un contrôle Edit est exposé via la propriété Name du contrôle Edit. Étant donné que le contrôle Edit figure dans l'affichage du contenu de l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , il est inutile que l'élément Text soit présent dans cet affichage de l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Le seul texte qui apparaît dans l'affichage du contenu est le texte qui ne présente pas d'informations redondantes. Cela permet aux technologies d'assistance de filtrer rapidement les informations dont leurs utilisateurs ont besoin.

### <a name="edit"></a>Modifier

Les contrôles Edit permettent à un utilisateur d'afficher et de modifier une seule ligne de texte.

> [!NOTE]
> Dans certains scénarios de disposition, le texte peut faire l'objet d'un retour automatique à la ligne.

### <a name="document"></a>Document

Les contrôles Document permettent à l'utilisateur de parcourir plusieurs pages de texte et d'obtenir des informations à partir de celles-ci.

<a name="TextPattern_Client_API_s"></a>

## <a name="textpattern-client-apis"></a>API client TextPattern

|||
|-|-|
|`System.Windows.Automation.TextPattern Class`|Point d'entrée pour le modèle de texte [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .<br /><br /> Cette classe contient également les deux écouteurs d'événements <xref:System.Windows.Automation.TextPattern> : <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> et <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|
|`System.Windows.Automation.Text.TextPatternRange Class`|Représentation d'une étendue de texte dans un conteneur de texte qui prend en charge <xref:System.Windows.Automation.TextPattern>.<br /><br /> Les clients UI Automation doivent faire attention à la validité actuelle d’une plage de texte créée à l’aide de <xref:System.Windows.Automation.Text.TextPatternRange>. Si le texte d'origine dans le contrôle de texte est complètement remplacé par un nouveau texte, la plage de texte actuelle devient non valide. Toutefois, la plage de texte peut rester viable si seule une partie du texte d'origine est modifiée et que le contrôle de texte sous-jacent gère son « pointeur » de texte avec des points d'ancrage (ou points de terminaison) plutôt qu'avec un positionnement de caractère absolu.<br /><br /> Les clients peuvent écouter un <xref:System.Windows.Automation.TextPattern.TextChangedEvent> pour être avertis de toute modification apportée au contenu textuel qu'ils utilisent.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Utilisé pour identifier les attributs de mise en forme d'une plage de texte.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>API du fournisseur TextPattern

Les contrôles ou éléments d'interface utilisateur qui prennent en charge <xref:System.Windows.Automation.TextPattern> en implémentant les interfaces <xref:System.Windows.Automation.Provider.ITextProvider> et <xref:System.Windows.Automation.Provider.ITextRangeProvider> , soit en mode natif soit par l'intermédiaire de proxys [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , sont à même d'exposer des informations d'attribut détaillées pour tout texte qu'ils contiennent, en plus de fournir des fonctionnalités de navigation fiables.

Un fournisseur <xref:System.Windows.Automation.TextPattern> n'a pas à prendre en charge tous les attributs de texte si certains attributs ne sont pas pris en charge par le contrôle.

Un fournisseur <xref:System.Windows.Automation.TextPattern> doit prendre en charge les fonctions <xref:System.Windows.Automation.TextPattern.GetSelection%2A> et <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> si le contrôle prend en charge la sélection de texte ou le positionnement du curseur de texte (ou signe insertion) dans la zone de texte. Si le contrôle ne prend pas en charge ces fonctionnalités, il n'a pas besoin de prendre en charge ces méthodes. Par contre, le contrôle doit exposer le type de sélection de texte qu'il prend en charge en implémentant la propriété <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> .

Un fournisseur <xref:System.Windows.Automation.TextPattern> doit toujours prendre en charge les constantes <xref:System.Windows.Automation.Text.TextUnit><xref:System.Windows.Automation.Text.TextUnit.Character> et <xref:System.Windows.Automation.Text.TextUnit.Document> , ainsi que toutes les autres constantes <xref:System.Windows.Automation.Text.TextUnit> dans la mesure du possible.

> [!NOTE]
> Le fournisseur peut ignorer la prise en charge d'un <xref:System.Windows.Automation.Text.TextUnit> spécifique en passant au deuxième <xref:System.Windows.Automation.Text.TextUnit> le plus long pris en charge dans l'ordre suivant : <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>et <xref:System.Windows.Automation.Text.TextUnit.Document>.

|||
|-|-|
|`ITextProvider Interface`|Expose les méthodes, propriétés et attributs qui prennent en charge <xref:System.Windows.Automation.TextPattern> dans les applications clientes (consultez <xref:System.Windows.Automation.Provider.ITextProvider>).|
|`ITextRangeProvider Interface`|Représente une plage de texte dans un fournisseur de texte (consultez <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Contient les valeurs utilisées comme identificateurs pour les fournisseurs de texte (consultez <xref:System.Windows.Automation.TextPatternIdentifiers>).|

<a name="Security"></a>

## <a name="security"></a>Sécurité

Les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a été conçue pour garantir la sécurité (consultez [UI Automation Security Overview](ui-automation-security-overview.md)). Toutefois, les classes TextPattern décrites dans cette vue d'ensemble ont des exigences spécifiques en matière de sécurité.

- Les fournisseurs de texte[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proposent des interfaces en lecture seule et ne permettent pas de modifier le texte existant dans un contrôle.

- Les clients UI Automation ne peuvent utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] que s’ils sont entièrement « fiables ». Par exemple, pour le bureau d'ouverture de session protégé, seules les applications connues et approuvées peuvent être exécutées.

- Les développeurs de fournisseurs UI Automation doivent savoir que toutes les informations qu’ils choisissent d’exposer dans leurs contrôles via [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sont par nature publiques et entièrement accessibles à un autre code. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ne fait rien de particulier pour déterminer la crédibilité d’un client UI Automation. Ainsi, le fournisseur UI Automation ne doit pas exposer de contenu protégé ou d’informations textuelles sensibles (telles que des champs de mot de passe).

- L’une des modifications les plus significatives de la sécurité pour Windows Vista est connue sous le terme d' « entrée sécurisée », qui englobe des technologies telles que les comptes d’utilisateur à faible privilège (ou limité) et l’isolation de niveau de privilège de l’interface utilisateur (UIPI).

  - UIPI empêche un programme de contrôler et/ou de surveiller un autre programme ayant davantage de privilèges, évitant les attaques de message de fenêtre interprocessus qui usurpent l'entrée de l'utilisateur.

  - LUA définit des limites sur les privilèges des applications exécutées par les utilisateurs du groupe Administrateurs. Les applications n'ont pas forcément de privilèges d'administrateur, mais elles sont exécutées avec les privilèges minimum nécessaires. Par conséquent, certaines restrictions peuvent être appliquées dans les scénarios LUA, en particulier la troncation de chaîne (notamment les chaînes TextPattern). Dans ce cas, il peut être nécessaire de limiter la taille des chaînes récupérées à partir d'applications de niveau administrateur afin qu'elles ne soient pas contraintes d'allouer de la mémoire au point de désactiver l'application.

<a name="Performance"></a>

## <a name="performance"></a>Performances

Étant donné que TextPattern repose sur des appels interprocessus pour la plupart de ses fonctionnalités, il ne fournit pas de mécanisme de mise en cache pour améliorer les performances lors du traitement du contenu, contrairement à d’autres modèles de contrôle dans [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , qui sont accessibles à l’aide de la méthode <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> .

Pour améliorer les performances, assurez-vous que les clients UI Automation tentent de récupérer des blocs de texte de taille modérée à l’aide de <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Par exemple, des appels GetText(1) impliquent des résultats interprocessus pour chaque caractère alors qu'un appel GetText(-1) implique un résultat interprocessus, mais peut présenter une latence élevée selon la taille du fournisseur de texte.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>Terminologie de TextPattern

**Attribut**\
Caractéristique de mise en forme d'une plage de texte (par exemple, <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> ou <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).

**Plage dégénérée**\
Une plage dégénérée est une plage de texte vide ou sans caractère. Pour les besoins du modèle de contrôle TextPattern, le point d'insertion de texte (ou signe insertion) est considéré comme une plage dégénérée. Si aucun texte n'est sélectionné, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> retourne une plage dégénérée au niveau du point d'insertion de texte et <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> retourne une plage dégénérée en tant que point de terminaison initial. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> et <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> peuvent retourner des plages dégénérées quand le fournisseur de texte ne peut pas trouver de plages de texte correspondant à la condition donnée. Cette plage dégénérée peut être utilisée en tant que point de terminaison initial dans le fournisseur de texte. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A>et <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> retournent une référence null ( `Nothing` dans Microsoft Visual Basic .net) pour éviter toute confusion entre une plage découverte et une plage dégénérée.

**Objet incorporé**\
Il existe deux types d'objets incorporés dans le modèle de texte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Il s'agit des éléments de contenu de type texte tels que les liens hypertexte ou les tables, et des éléments de contrôle tels que les images et les boutons. Pour obtenir des informations détaillées, consultez [Access Embedded Objects Using UI Automation](access-embedded-objects-using-ui-automation.md).

**Poste**\
Point <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ou <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> absolu d'une plage de texte dans un conteneur de texte.

![TextPatternRangeEndpoints &#40;&#41; de début et de fin.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")
L'exemple suivant illustre un ensemble de points de début et de terminaison.

**TextRange**\
Représentation d'une étendue de texte, avec des points de départ et de terminaison, dans un conteneur de texte incluant tous les attributs et fonctionnalités associés.

<xref:System.Windows.Automation.Text.TextUnit>\
Unité de texte prédéfinie (caractère, mot, ligne ou paragraphe) utilisée pour naviguer dans les segments logiques d'une plage de texte.

## <a name="see-also"></a>Voir aussi

- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [Vue d'ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Vue d’ensemble de l’arborescence UI Automation](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [Mappage de modèle de contrôle pour les clients UI Automation](control-pattern-mapping-for-ui-automation-clients.md)
- [Text Services Framework](/windows/desktop/api/_tsf/)
