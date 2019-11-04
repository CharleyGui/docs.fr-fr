---
title: Recommandations pour la conception de contrôles auxquels un style peut être appliqué
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 0fbb515afbeac05168ced6f0a99f50eb29a5c848
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459651"
---
# <a name="guidelines-for-designing-stylable-controls"></a>Recommandations pour la conception de contrôles auxquels un style peut être appliqué

Ce document récapitule un ensemble de meilleures pratiques à envisager lors de la conception d’un contrôle auquel vous souhaitez appliquer facilement un style et un modèle. Ces meilleures pratiques sont issues d’un long processus d’essais et d’erreurs lors de notre travail sur les styles de contrôles de thème pour le jeu de contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] intégré. Nous avons appris qu’un style réussi constitue tout autant une fonction d’un modèle d’objet bien conçu que du style lui-même. Ce document concerne l’auteur du contrôle et non l’auteur du style.

<a name="Terminology"></a>

## <a name="terminology"></a>Terminologie

« L’application d’un style et la création de modèles » font référence à la suite de technologies qui permettent à un auteur de contrôle de reporter les aspects visuels du contrôle sur le style et le modèle du contrôle. Cette suite de technologies inclut :

- Styles (notamment les accesseurs Set, les déclencheurs et les plans conceptuels).

- Ressources.

- Modèles de contrôle.

- Modèles de données.

Pour obtenir une présentation de l’application d’un style et la création de modèles, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

<a name="Before_You_Start__Understanding_Your_Control"></a>

## <a name="before-you-start-understanding-your-control"></a>Avant de commencer : bien comprendre le contrôle

Avant d’explorer ces recommandations, il est important que vous compreniez et que vous ayez défini l’utilisation courante de votre contrôle. L’application d’un style expose un ensemble de possibilités souvent non maîtrisé. Les contrôles qui sont écrits pour être utilisés globalement (dans de nombreuses applications, par de nombreux développeurs) sont confrontés au fait que l’application d’un style peut être utilisée pour apporter des modifications de grande envergure à l’apparence visuelle du contrôle. En fait, le contrôle stylé peut ne pas ressembler aux intentions premières de l’auteur du contrôle. La souplesse offerte par l’application d’un style étant infinie, vous pouvez utiliser la notion d’utilisation courante pour vous aider à cerner vos décisions.

Pour comprendre l’utilisation courante de votre contrôle, il est judicieux de réfléchir à la proposition de valeur du contrôle. Qu’est-ce qui rend votre contrôle unique par rapport à tous les autres contrôles ? L’utilisation courante n’implique pas une apparence visuelle spécifique, mais plutôt la philosophie du contrôle et un ensemble raisonnable d’attentes concernant son utilisation. Cette compréhension vous permet de formuler des hypothèses sur le modèle de composition et les comportements définis par le style du contrôle dans le cas courant. Dans le cas de <xref:System.Windows.Controls.ComboBox>, par exemple, la compréhension de l’utilisation courante ne vous donne aucune idée de savoir si un <xref:System.Windows.Controls.ComboBox> particulier a des angles arrondis, mais il vous donne un aperçu du fait que l' <xref:System.Windows.Controls.ComboBox> a probablement besoin d’une fenêtre contextuelle et d’une certaine façon de le basculement s’il est ouvert.

<a name="General_Guidelines"></a>

## <a name="general-guidelines"></a>Indications générales

- **N’appliquez pas les contrats de modèles de manière stricte.** Le contrat de modèle d’un contrôle peut comporter des éléments, commandes, liaisons, déclencheurs ou même des paramètres de propriété qui sont requis ou attendus afin qu’un contrôle fonctionne correctement.

  - Réduisez autant que possible les contrats.

  - Concevez en gardant à l’esprit que pendant la conception (autrement dit, lorsque vous utilisez un outil de conception), il est courant pour un modèle de contrôle de se trouver dans un état incomplet. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’offre pas une infrastructure d’état de « composition », donc les contrôles doivent être générés avec l’idée que cet état peut être valide.

  - Ne levez pas d’exception lorsqu’un aspect du contrat de modèle n’est pas respecté. Dans le même état d’esprit, les panneaux ne doivent pas lever d’exceptions s’ils ont trop ou trop peu d’enfants.

- **Prenez en compte les fonctionnalités périphériques dans les éléments de modèle d’assistance.** Chaque contrôle doit être axé sur sa fonctionnalité principale et sa proposition de valeur réelle et doit être défini par l’utilisation courante du contrôle. Pour ce faire, utilisez les éléments de composition et d’assistance au sein du modèle pour activer les comportements et visualisations périphériques, autrement dit, les comportements et les visualisations qui ne contribuent pas à la fonctionnalité principale du contrôle. Les éléments d’assistance se répartissent en trois catégories :

  - Les types d’assistance **autonomes** sont des contrôles publics et réutilisables ou des primitives utilisées de manière « anonyme » dans un modèle, ce qui signifie que ni l’élément d’assistance ni le contrôle stylé n’est conscient de l’autre. Techniquement, tout élément peut être un type anonyme, mais dans ce contexte, le terme décrit les types qui encapsulent des fonctionnalités spéciales pour activer des scénarios ciblés.

  - Les éléments d’assistance **basés sur le type** sont des nouveaux types qui encapsulent des fonctionnalités spéciales. Ces éléments sont généralement conçus avec une plage plus étroite de fonctionnalités par rapport aux primitives ou aux contrôles courants. Contrairement aux éléments d’assistance autonomes, les éléments d’assistance basés sur le type prennent en compte le contexte dans lequel ils sont utilisés et doivent généralement partager des données avec le contrôle du modèle auquel ils appartiennent.

  - Les éléments d’assistance **nommés** sont des contrôles ou des primitives courants qu’un contrôle s’attend à trouver (par leurs noms) dans son modèle. Ces éléments portent un nom connu dans le modèle, ce qui permet à un contrôle de rechercher l’élément et d’interagir avec celui-ci par programme. Il ne peut exister qu’un seul élément avec un nom donné dans un modèle.

  Le tableau suivant présente les éléments d’assistance utilisés par les styles de contrôle actuellement (cette liste n’est pas exhaustive) :

  |Élément|Tapez|Utilisé par|
  |-------------|----------|-------------|
  |<xref:System.Windows.Controls.ContentPresenter>|Basé sur le type|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>, etc. (tous les types de <xref:System.Windows.Controls.ContentControl>)|
  |<xref:System.Windows.Controls.ItemsPresenter>|Basé sur le type|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, etc. (tous les types de <xref:System.Windows.Controls.ItemsControl>)|
  |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nommé|<xref:System.Windows.Controls.ToolBar>|
  |<xref:System.Windows.Controls.Primitives.Popup>|Autonome|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>, etc.|
  |<xref:System.Windows.Controls.Primitives.RepeatButton>|Nommé|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>, etc.|
  |<xref:System.Windows.Controls.Primitives.ScrollBar>|Nommé|<xref:System.Windows.Controls.ScrollViewer>|
  |<xref:System.Windows.Controls.ScrollViewer>|Autonome|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>, etc.|
  |<xref:System.Windows.Controls.Primitives.TabPanel>|Autonome|<xref:System.Windows.Controls.TabControl>|
  |<xref:System.Windows.Controls.TextBox>|Nommé|<xref:System.Windows.Controls.ComboBox>|
  |<xref:System.Windows.Controls.Primitives.TickBar>|Basé sur le type|<xref:System.Windows.Controls.Slider>|

- **Réduisez les liaisons ou les paramètres de propriété spécifiés par l’utilisateur requis sur les éléments d’assistance**. Il est courant pour un élément d’assistance de nécessiter certaines liaisons ou certains paramètres de propriété pour fonctionner correctement dans le modèle du contrôle. L’élément d’assistance et le contrôle basé sur un modèle doivent, autant que possible, établir ces paramètres. Lors de la définition de propriétés ou l’établissement de liaisons, veillez à ne pas écraser les valeurs définies par l’utilisateur. Les meilleures pratiques spécifiques sont les suivantes :

  - Les éléments d’assistance nommés doivent être identifiés par le parent et le parent doit établir les paramètres requis sur l’élément d’assistance.

  - Les éléments d’assistance basés sur le type doivent établir les paramètres requis directement sur eux-mêmes. Pour ce faire, l’élément d’assistance peut demander des informations sur le contexte dans lequel il est utilisé, notamment son `TemplatedParent` (le type de contrôle du modèle dans lequel il est utilisé). Par exemple, <xref:System.Windows.Controls.ContentPresenter> lie automatiquement la propriété `Content` de son `TemplatedParent` à sa propriété <xref:System.Windows.Controls.ContentPresenter.Content%2A> lorsqu’il est utilisé dans un type dérivé <xref:System.Windows.Controls.ContentControl>.

  - Il est impossible d’optimiser les éléments d’assistance autonomes de cette façon car, par définition, ni l’élément d’assistance ni le parent n’ont conscience l’un de l’autre.

- **Utilisez la propriété Name pour marquer des éléments dans un modèle**. Un contrôle qui doit trouver un élément dans son style afin d’y accéder par programme doit, pour ce faire, utiliser la propriété `Name` et le paradigme `FindName`. Un contrôle ne doit pas lever une exception lorsqu’un élément est introuvable, mais il doit désactiver silencieusement et correctement la fonctionnalité qui requérait cet élément.

- **Utilisez les meilleures pratiques pour exprimer l’état du contrôle et le comportement dans un style.** Vous trouverez ci-dessous une liste des meilleures pratiques pour exprimer les changements d’état du contrôle et le comportement dans un style. Utilisez le premier élément dans la liste qui correspond à votre scénario.

  1. Liaison de propriété. Exemple : liaison entre <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.

  2. Déclenchement des modifications de propriété ou des animations de propriété. Exemple : état de survol d’un <xref:System.Windows.Controls.Button>.

  3. Commande. Exemple : <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand> / <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> dans <xref:System.Windows.Controls.Primitives.ScrollBar>.

  4. Éléments d’assistance autonomes. Exemple : <xref:System.Windows.Controls.Primitives.TabPanel> dans <xref:System.Windows.Controls.TabControl>.

  5. Types d’assistance basés sur le type. Exemple : <xref:System.Windows.Controls.ContentPresenter> dans <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> dans <xref:System.Windows.Controls.Slider>.

  6. Éléments d’assistance nommés. Exemple : <xref:System.Windows.Controls.TextBox> dans <xref:System.Windows.Controls.ComboBox>.

  7. Événements propagés à partir de types d’assistance nommés. Si vous écoutez des événements propagés à partir d’un élément de style, vous devez demander que l’élément générant l’événement puisse être identifié de manière unique. Exemple : <xref:System.Windows.Controls.Primitives.Thumb> dans <xref:System.Windows.Controls.ToolBar>.

  8. Comportement `OnRender` personnalisé. Exemple : <xref:Microsoft.Windows.Themes.ButtonChrome> dans <xref:System.Windows.Controls.Button>.

- **Utilisez des déclencheurs de style (par opposition aux déclencheurs de modèle) avec parcimonie**. Les déclencheurs qui affectent des propriétés sur les éléments dans le modèle doivent être déclarés dans le modèle. Les déclencheurs qui affectent des propriétés sur le contrôle (aucun `TargetName`) peuvent être déclarés dans le style, sauf si vous savez que la modification du modèle détruirait également le déclencheur.

- **Soyez cohérent avec les modèles de styles existants.** Il existe souvent plusieurs façons de résoudre un problème. Tenez compte et soyez cohérent, lorsque possible, concernant les modèles de styles existants. Cela est particulièrement important pour les contrôles qui dérivent du même type de base (par exemple, <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>, etc.).

- **Exposez des propriétés pour activer des scénarios de personnalisation courants sans recréer un modèle**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne prend pas en charge les composants enfichables/personnalisables, donc un utilisateur du contrôle dispose de seulement deux méthodes de personnalisation : définir des propriétés directement ou définir des propriétés à l’aide de styles. Dans cette optique, il convient d’exposer un nombre limité de propriétés destinées à des scénarios de personnalisation très courants, de priorité élevée, qui nécessiteraient sinon la recréation d’un modèle. Voici les meilleures pratiques pour savoir quand et comment activer des scénarios de personnalisation :

  - Les personnalisations très courantes doivent être exposées en tant que propriétés sur le contrôle et consommées par le modèle.

  - Les personnalisations moins courantes (mais pas rares) doivent être exposées en tant que propriétés jointes et consommées par le modèle.

  - Les personnalisations courantes mais rares peuvent exiger la recréation d’un modèle.

<a name="Theme_Considerations"></a>

## <a name="theme-considerations"></a>Considérations relatives au thème

- **Les styles de thème doivent, autant que possible, posséder une sémantique des propriétés cohérente entre tous les thèmes, sans aucune garantie**. Dans le cadre de sa documentation, votre contrôle doit posséder un document décrivant la sémantique des propriétés du contrôle, autrement dit, la « signification » d’une propriété pour un contrôle. Par exemple, le contrôle <xref:System.Windows.Controls.ComboBox> doit définir la signification de la propriété <xref:System.Windows.Controls.Control.Background%2A> dans <xref:System.Windows.Controls.ComboBox>. Les styles par défaut de votre contrôle doivent, autant que possible, respecter la sémantique définie dans ce document pour tous les thèmes. Les utilisateurs du contrôle, en revanche, doivent savoir que la sémantique des propriétés peut changer d’un thème à l’autre. Dans certains cas, une propriété donnée peut ne pas pouvoir être exprimée avec les contraintes visuelles imposées par un thème particulier. (Le thème Classique, par exemple, n’a pas de bordure simple à laquelle `Thickness` peut être appliqué pour de nombreux contrôles.)

- **Les styles de thème ne requièrent pas que la sémantique de déclencheur soit cohérente entre tous les thèmes**. Le comportement exposé par un style de contrôle par le biais de déclencheurs ou d’animations peut varier d’un thème à l’autre. Les utilisateurs du contrôle doivent savoir qu’un contrôle n’utilise pas nécessairement le même mécanisme dans tous les thèmes pour obtenir un comportement particulier. Un thème, par exemple, peut utiliser une animation pour exprimer le comportement de survol alors qu’un autre thème utilise un déclencheur. Cela peut entraîner des disparités dans la préservation du comportement au niveau des contrôles personnalisés. (La modification de la propriété d’arrière-plan, par exemple, peut ne pas affecter l’état de survol du contrôle si cet état est exprimé à l’aide d’un déclencheur. Toutefois, si l’état de survol est implémenté à l’aide d’une animation, la modification de l’arrière-plan pourrait altérer irrémédiablement l’animation et, par conséquent, la transition de l’état.)

- **Les styles de thème ne requièrent pas que la sémantique de « disposition » soit cohérente entre tous les thèmes**. Par exemple, le style par défaut n’a pas besoin de garantir qu’un contrôle occupera le même espace dans tous les thèmes ou qu’un contrôle aura les mêmes marges de contenu / marges intérieures dans tous les thèmes.

## <a name="see-also"></a>Voir aussi

- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble de la création de contrôles](control-authoring-overview.md)
