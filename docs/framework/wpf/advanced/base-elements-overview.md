---
title: Vue d'ensemble des éléments de base
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: f6519675ebf3624152e1077e7582f04e38b1dce9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644037"
---
# <a name="base-elements-overview"></a>Vue d'ensemble des éléments de base
Un pourcentage élevé [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de classes sont dérivées de quatre classes qui sont communément appelées dans la documentation SDK comme les classes d’éléments de base. Ces classes <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkElement>sont <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkContentElement>, , et . La <xref:System.Windows.DependencyObject> classe est également liée, parce qu’il s’agit d’une classe de base commune des deux <xref:System.Windows.UIElement> et<xref:System.Windows.ContentElement>  

<a name="base_apis"></a>
## <a name="base-element-apis-in-wpf-classes"></a>API d’élément de base dans les classes WPF  
 Les <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> deux et <xref:System.Windows.DependencyObject>sont dérivés de , à travers des voies quelque peu différentes. La scission à ce niveau <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> traite de la façon dont un ou sont utilisés dans une interface utilisateur et à quel but ils servent dans une application. <xref:System.Windows.UIElement>a <xref:System.Windows.Media.Visual> également dans sa hiérarchie de classe, qui est une classe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]qui expose le support graphique de niveau inférieur sous-jacent à la . <xref:System.Windows.Media.Visual>fournit un cadre de rendu en définissant des régions d’écran rectangulaires indépendantes. Dans la <xref:System.Windows.UIElement> pratique, est pour les éléments qui prennent en charge un modèle d’objet plus grand, sont destinés à rendre et à mettre en page dans les régions qui peuvent être décrites comme des régions d’écran rectangulaire, et où le modèle de contenu est délibérément plus ouvert, pour permettre différentes combinaisons d’éléments. <xref:System.Windows.ContentElement>ne dérive <xref:System.Windows.Media.Visual>pas de ; son modèle est <xref:System.Windows.ContentElement> qu’un serait consommé par autre chose, comme un lecteur ou <xref:System.Windows.Media.Visual> un [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] spectateur qui interpréterait alors les éléments et produirait le complet pour consommer. Certaines <xref:System.Windows.UIElement> classes sont destinées à être des hôtes de contenu: <xref:System.Windows.ContentElement> ils<xref:System.Windows.Controls.DocumentViewer> fournissent l’hébergement et le rendu pour une ou plusieurs classes (est un exemple d’une telle classe). <xref:System.Windows.ContentElement>est utilisé comme classe de base pour les éléments avec des modèles d’objets un peu <xref:System.Windows.UIElement>plus petits et que plus aborder le texte, l’information, ou le contenu de document qui pourrait être hébergé dans un .  
  
### <a name="framework-level-and-core-level"></a>Niveau de framework et niveau principal  
 <xref:System.Windows.UIElement>sert de classe <xref:System.Windows.FrameworkElement>de <xref:System.Windows.ContentElement> base pour , <xref:System.Windows.FrameworkContentElement>et sert de classe de base pour . La raison de ce prochain niveau de classes est de soutenir un niveau de base WPF qui est séparé d’un niveau cadre WPF, avec cette division existant également dans la façon dont les API sont divisés entre les assemblages PresentationCore et PresentationFramework. Le niveau de framework WPF représente une solution plus complète pour les besoins d’application de base, y compris l’implémentation du gestionnaire de présentation pour les présentations. Le niveau principal WPF offre un moyen d’utiliser la majeure partie de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sans utiliser la charge mémoire de l’assembly supplémentaire. La distinction entre ces niveaux est très rarement importante pour la plupart [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des scénarios typiques de développement d’applications, et en général vous devriez penser aux API dans leur ensemble et ne pas vous préoccuper de la différence entre le niveau de cadre WPF et le niveau de base WPF. Vous devez pouvoir être renseigné sur les distinctions de niveau si votre conception d’applications choisit de remplacer de nombreuses fonctionnalités au niveau framework WPF, par exemple si votre solution globale possède déjà ses propres implémentations de composition d’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] et de mise en page.  
  
<a name="subclassing_elements"></a>
## <a name="choosing-which-element-to-derive-from"></a>Choisir de quel élément dériver  
 La méthode la plus pratique pour créer une classe personnalisée qui étend [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à dériver de l’une des classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] où vous récupérez le plus de fonctionnalités possibles que vous désirez par le biais de la hiérarchie de classes existante. Cette section répertorie les fonctionnalités qui sont fournies avec trois des plus importantes classes d’élément pour vous aider à décider de quelle classe hériter.  
  
 Si vous mettez en œuvre un contrôle, qui est vraiment [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’une des raisons les plus courantes pour dériver d’une classe, vous <xref:System.Windows.Controls.Control> voulez probablement dériver d’une classe qui est un contrôle pratique, une classe de base familiale de contrôle, ou du moins de la classe de base. Pour obtenir de l’aide et des exemples pratiques, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).  
  
 Si vous ne créez pas de contrôle mais que vous avez besoin de dériver d’une classe plus haute dans la hiérarchie, les sections suivantes sont prévues pour vous servir de guide des caractéristiques définies dans chaque classe d’élément de base.  
  
 Si vous créez une classe <xref:System.Windows.DependencyObject>qui dérive, vous héritez de la fonctionnalité suivante :  
  
- <xref:System.Windows.DependencyObject.GetValue%2A>et <xref:System.Windows.DependencyObject.SetValue%2A> le soutien, et le soutien général du système de propriété.  
  
- Capacité d’utiliser les propriétés de dépendance et les propriétés jointes implémentées comme propriétés de dépendance.  
  
 Si vous créez une classe <xref:System.Windows.UIElement>qui dérive de , vous héritez de la fonctionnalité suivante en plus de celle fournie par <xref:System.Windows.DependencyObject>:  
  
- Prise en charge de base pour les valeurs de propriété animées. Pour plus d’informations, voir [Aperçu animation](../graphics-multimedia/animation-overview.md).  
  
- Prise en charge de base des événements d’entrée et prise en charge des commandes. Pour plus d’informations, consultez [Vue d’ensemble des entrées](input-overview.md) et [Vue d’ensemble des commandes](commanding-overview.md).  
  
- Méthodes virtuelles qui peuvent être substituées pour fournir des informations à un système de disposition.  
  
 Si vous créez une classe <xref:System.Windows.FrameworkElement>qui dérive de , vous héritez de la fonctionnalité suivante en plus de celle fournie par <xref:System.Windows.UIElement>:  
  
- Prise en charge des styles et des tables de montage séquentiel. Pour plus d’informations, voir <xref:System.Windows.Style> et [Storyboards Aperçu](../graphics-multimedia/storyboards-overview.md).  
  
- Prise en charge de la liaison de données. Pour plus d’informations, voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Prise en charge des références de ressource dynamique. Pour plus d’informations, consultez [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Prise en charge de l’héritage de la valeur de propriété, et d’autres indicateurs dans les métadonnées qui aident à faire part des conditions traitant des propriétés aux services de framework, comme la liaison de données, les styles ou l’implémentation du framework de disposition. Pour plus d’informations, consultez [Métadonnées de propriété de framework](framework-property-metadata.md).  
  
- Le concept de l’arborescence logique. Pour plus d’informations, consultez [Arborescences dans WPF](trees-in-wpf.md).  
  
- Prise en charge de la mise en œuvre <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> pratique au niveau du cadre WPF du système de mise en page, y compris une dérogation qui peut détecter les changements aux propriétés qui influencent la mise en page.  
  
 Si vous créez une classe <xref:System.Windows.ContentElement>qui dérive de , vous héritez de la fonctionnalité suivante en plus de celle fournie par <xref:System.Windows.DependencyObject>:  
  
- Prise en charge des animations. Pour plus d’informations, voir [Aperçu animation](../graphics-multimedia/animation-overview.md).  
  
- Prise en charge de base des événements d’entrée et prise en charge des commandes. Pour plus d’informations, consultez [Vue d’ensemble des entrées](input-overview.md) et [Vue d’ensemble des commandes](commanding-overview.md).  
  
 Si vous créez une classe <xref:System.Windows.FrameworkContentElement>qui dérive de , vous obtenez <xref:System.Windows.ContentElement>la fonctionnalité suivante en plus de celle fournie par :  
  
- Prise en charge des styles et des tables de montage séquentiel. Pour plus d’informations, voir <xref:System.Windows.Style> et Aperçu de [l’animation](../graphics-multimedia/animation-overview.md).  
  
- Prise en charge de la liaison de données. Pour plus d’informations, voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Prise en charge des références de ressource dynamique. Pour plus d’informations, consultez [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Prise en charge de l’héritage de la valeur de propriété, et d’autres indicateurs dans les métadonnées qui aident à faire part des conditions traitant des propriétés aux services de framework, comme la liaison de données, les styles ou l’implémentation du framework de disposition. Pour plus d’informations, consultez [Métadonnées de propriété de framework](framework-property-metadata.md).  
  
- Vous n’héritez pas de l’accès aux modifications du système de mise en page (comme <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Les implémentations <xref:System.Windows.FrameworkElement>du système de mise en page ne sont disponibles que sur . Cependant, vous <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> héritez d’un remplacement qui peut détecter les modifications apportées aux propriétés qui influencent la mise en page et les signaler à tous les hôtes de contenu.  
  
 Les modèles de contenu sont documentés pour diverses classes. Le modèle de contenu pour une classe est l’un des facteurs dont vous devez tenir compte si vous souhaitez rechercher une classe appropriée à partir de laquelle dériver. Pour plus d’informations, consultez [Modèle de contenu WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>
## <a name="other-base-classes"></a>Autres classes de base  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject>fournit une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prise en charge du modèle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de threading <xref:System.Windows.Threading.Dispatcher>et permet à tous les objets créés pour les applications d’être associés à un . Même si vous ne <xref:System.Windows.UIElement> <xref:System.Windows.DependencyObject>dérivez <xref:System.Windows.Media.Visual>pas de , , <xref:System.Windows.Threading.DispatcherObject> ou , vous devriez envisager deriving de afin d’obtenir ce support modèle de filetage. Pour plus d’informations, consultez [Modèle de thread](threading-model.md).  
  
### <a name="visual"></a>Élément visuel  
 <xref:System.Windows.Media.Visual>met en œuvre le concept d’un objet 2D qui nécessite généralement une présentation visuelle dans une région à peu près rectangulaire. Le rendu réel <xref:System.Windows.Media.Visual> d’un se produit dans d’autres <xref:System.Windows.Media.Visual> classes (il n’est pas autonome), mais la classe fournit un type connu qui est utilisé par les processus de rendu à différents niveaux. <xref:System.Windows.Media.Visual>met en œuvre les tests de frappe, mais il <xref:System.Windows.UIElement>n’expose pas les événements qui signalent des points positifs de hit-testing (ceux-ci sont en ). Pour plus d’informations, consultez [Programmation de la couche visuelle](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable>simule l’immuabilité d’un objet mutable en fournissant les moyens de générer des copies de l’objet lorsqu’un objet immuable est requis ou désiré pour des raisons de performance. Le <xref:System.Windows.Freezable> type fournit une base commune pour certains éléments graphiques tels que les géométries et les brosses, ainsi que les animations. Notamment, <xref:System.Windows.Freezable> a n’est pas un <xref:System.Windows.Media.Visual>; il peut contenir des propriétés qui <xref:System.Windows.Freezable> deviennent des sous-propriétés lorsque l’on l’applique pour remplir une valeur de propriété d’un autre objet, et ces sous-propositions peuvent affecter le rendu. Pour plus d’informations, consultez [Vue d’ensemble des objets Freezable](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>est <xref:System.Windows.Freezable> une classe dérivée qui ajoute spécifiquement la couche de contrôle d’animation et certains membres utilitaires de sorte que les propriétés actuellement animées peuvent être distinguées des propriétés non animées.  
  
### <a name="control"></a>Control  
 <xref:System.Windows.Controls.Control>est la classe de base prévue pour le type d’objet qui est diversement appelé un contrôle ou un composant, selon la technologie. En général, les classes de contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont des classes qui représentent directement un contrôle d’interface utilisateur ou qui participent étroitement à la composition de contrôle. La fonctionnalité principale <xref:System.Windows.Controls.Control> qui permet est le contrôle de la température.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Control>
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Architecture de WPF](wpf-architecture.md)
