---
title: Vue d'ensemble des éléments de base
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 823c81bf6b21b88d719503387a68ce6e7d643d61
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740912"
---
# <a name="base-elements-overview"></a>Vue d'ensemble des éléments de base
Un pourcentage élevé de classes dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sont dérivés de quatre classes qui sont communément appelées dans la documentation du kit de développement logiciel (SDK) comme classes d’éléments de base. Ces classes sont <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>et <xref:System.Windows.FrameworkContentElement>. La classe <xref:System.Windows.DependencyObject> est également associée, car il s’agit d’une classe de base commune des <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>API d’élément de base dans les classes WPF  
 Les <xref:System.Windows.UIElement> et les <xref:System.Windows.ContentElement> sont dérivés de <xref:System.Windows.DependencyObject>, par le biais de chemins différents. Le fractionnement à ce niveau traite de la façon dont un <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> sont utilisés dans une interface utilisateur et de leur finalité dans une application. <xref:System.Windows.UIElement> a également <xref:System.Windows.Media.Visual> dans sa hiérarchie de classes, qui est une classe qui expose la prise en charge des graphiques de niveau inférieur sous-jacent du [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> fournit une infrastructure de rendu en définissant des régions d’écran rectangulaires indépendantes. Dans la pratique, <xref:System.Windows.UIElement> concerne les éléments qui prennent en charge un modèle d’objet plus volumineux, qui sont destinés à être restitués et présentés dans des régions qui peuvent être décrites comme zones d’écran rectangulaires, et où le modèle de contenu est délibérément plus ouvert, afin d’autoriser différentes combinaisons d’éléments. <xref:System.Windows.ContentElement> ne dérive pas de <xref:System.Windows.Media.Visual>; son modèle est qu’une <xref:System.Windows.ContentElement> serait consommée par un autre élément, tel qu’un lecteur ou une visionneuse qui interpréterait ensuite les éléments et produirait l' <xref:System.Windows.Media.Visual> complet pour [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] à consommer. Certaines classes <xref:System.Windows.UIElement> sont destinées à être des hôtes de contenu : elles fournissent l’hébergement et le rendu pour une ou plusieurs classes <xref:System.Windows.ContentElement> (<xref:System.Windows.Controls.DocumentViewer> est un exemple d’une telle classe). <xref:System.Windows.ContentElement> est utilisé comme classe de base pour les éléments avec des modèles objet un peu plus petits et qui adressent davantage le texte, les informations ou le contenu de document qui peuvent être hébergés dans un <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Niveau de framework et niveau principal  
 <xref:System.Windows.UIElement> sert de classe de base pour <xref:System.Windows.FrameworkElement>et <xref:System.Windows.ContentElement> sert de classe de base pour <xref:System.Windows.FrameworkContentElement>. La raison de ce niveau de classes suivant est de prendre en charge un niveau de noyau WPF distinct d’un niveau de Framework WPF, avec cette division également existante dans la manière dont les API sont réparties entre les assemblys PresentationCore et PresentationFramework. Le niveau de framework WPF représente une solution plus complète pour les besoins d’application de base, y compris l’implémentation du gestionnaire de présentation pour les présentations. Le niveau principal WPF offre un moyen d’utiliser la majeure partie de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sans utiliser la charge mémoire de l’assembly supplémentaire. La distinction entre ces niveaux est très rarement importante pour la plupart des scénarios de développement d’applications typiques, et en général, vous devez considérer les API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans leur ensemble et ne vous souciez pas de la différence entre le niveau de Framework WPF et le niveau de cœur WPF. Vous devez pouvoir être renseigné sur les distinctions de niveau si votre conception d’applications choisit de remplacer de nombreuses fonctionnalités au niveau framework WPF, par exemple si votre solution globale possède déjà ses propres implémentations de composition d’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] et de mise en page.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Choisir de quel élément dériver  
 La méthode la plus pratique pour créer une classe personnalisée qui étend [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à dériver de l’une des classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] où vous récupérez le plus de fonctionnalités possibles que vous désirez par le biais de la hiérarchie de classes existante. Cette section répertorie les fonctionnalités qui sont fournies avec trois des plus importantes classes d’élément pour vous aider à décider de quelle classe hériter.  
  
 Si vous implémentez un contrôle, qui est l’une des raisons les plus courantes de la dérivation à partir d’une classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous souhaiterez probablement dériver d’une classe qui est un contrôle pratique, une classe de base de famille de contrôle, ou au moins de la classe de base <xref:System.Windows.Controls.Control>. Pour obtenir de l’aide et des exemples pratiques, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).  
  
 Si vous ne créez pas de contrôle mais que vous avez besoin de dériver d’une classe plus haute dans la hiérarchie, les sections suivantes sont prévues pour vous servir de guide des caractéristiques définies dans chaque classe d’élément de base.  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.DependencyObject>, vous héritez des fonctionnalités suivantes :  
  
- la prise en charge des <xref:System.Windows.DependencyObject.GetValue%2A> et des <xref:System.Windows.DependencyObject.SetValue%2A>, ainsi que la prise en charge générale du système de propriétés.  
  
- Capacité d’utiliser les propriétés de dépendance et les propriétés jointes implémentées comme propriétés de dépendance.  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.UIElement>, vous héritez des fonctionnalités suivantes en plus de celles fournies par <xref:System.Windows.DependencyObject>:  
  
- Prise en charge de base pour les valeurs de propriété animées. Pour plus d’informations, consultez [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md).  
  
- Prise en charge de base des événements d’entrée et prise en charge des commandes. Pour plus d’informations, consultez [Vue d’ensemble des entrées](input-overview.md) et [Vue d’ensemble des commandes](commanding-overview.md).  
  
- Méthodes virtuelles qui peuvent être substituées pour fournir des informations à un système de disposition.  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.FrameworkElement>, vous héritez des fonctionnalités suivantes en plus de celles fournies par <xref:System.Windows.UIElement>:  
  
- Prise en charge des styles et des tables de montage séquentiel. Pour plus d’informations, consultez [vue d’ensemble](../graphics-multimedia/storyboards-overview.md)des <xref:System.Windows.Style> et des storyboards.  
  
- Prise en charge de la liaison de données. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md).  
  
- Prise en charge des références de ressource dynamique. Pour plus d’informations, consultez [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Prise en charge de l’héritage de la valeur de propriété, et d’autres indicateurs dans les métadonnées qui aident à faire part des conditions traitant des propriétés aux services de framework, comme la liaison de données, les styles ou l’implémentation du framework de disposition. Pour plus d’informations, consultez [Métadonnées de propriété de framework](framework-property-metadata.md).  
  
- Le concept de l’arborescence logique. Pour plus d’informations, consultez [Arborescences dans WPF](trees-in-wpf.md).  
  
- Prise en charge de l’implémentation pratique du système de disposition au niveau de l’infrastructure WPF, y compris une <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> substitution qui peut détecter les modifications apportées aux propriétés qui influencent la disposition.  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.ContentElement>, vous héritez des fonctionnalités suivantes en plus de celles fournies par <xref:System.Windows.DependencyObject>:  
  
- Prise en charge des animations. Pour plus d’informations, consultez [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md).  
  
- Prise en charge de base des événements d’entrée et prise en charge des commandes. Pour plus d’informations, consultez [Vue d’ensemble des entrées](input-overview.md) et [Vue d’ensemble des commandes](commanding-overview.md).  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.FrameworkContentElement>, vous obtenez les fonctionnalités suivantes en plus de celles fournies par <xref:System.Windows.ContentElement>:  
  
- Prise en charge des styles et des tables de montage séquentiel. Pour plus d’informations, consultez [vue d’ensemble](../graphics-multimedia/animation-overview.md)des <xref:System.Windows.Style> et des animations.  
  
- Prise en charge de la liaison de données. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md).  
  
- Prise en charge des références de ressource dynamique. Pour plus d’informations, consultez [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Prise en charge de l’héritage de la valeur de propriété, et d’autres indicateurs dans les métadonnées qui aident à faire part des conditions traitant des propriétés aux services de framework, comme la liaison de données, les styles ou l’implémentation du framework de disposition. Pour plus d’informations, consultez [Métadonnées de propriété de framework](framework-property-metadata.md).  
  
- Vous n’héritez pas de l’accès aux modifications du système de disposition (par exemple <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Les implémentations de système de disposition sont uniquement disponibles sur <xref:System.Windows.FrameworkElement>. Toutefois, vous héritez d’un <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> remplacement qui peut détecter les modifications apportées aux propriétés qui influencent la disposition et les signaler à n’importe quel hôte de contenu.  
  
 Les modèles de contenu sont documentés pour diverses classes. Le modèle de contenu pour une classe est l’un des facteurs dont vous devez tenir compte si vous souhaitez rechercher une classe appropriée à partir de laquelle dériver. Pour plus d’informations, consultez [Modèle de contenu WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Autres classes de base  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> prend en charge le modèle de thread [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et active tous les objets créés pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications à associer à un <xref:System.Windows.Threading.Dispatcher>. Même si vous ne dérivez pas de <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>ou <xref:System.Windows.Media.Visual>, vous devez envisager de dériver de <xref:System.Windows.Threading.DispatcherObject> afin d’obtenir la prise en charge de ce modèle de thread. Pour plus d’informations, consultez [Modèle de thread](threading-model.md).  
  
### <a name="visual"></a>Élément visuel  
 <xref:System.Windows.Media.Visual> implémente le concept d’un objet 2D qui requiert généralement une présentation visuelle dans une région à peu près rectangulaire. Le rendu réel d’un <xref:System.Windows.Media.Visual> se produit dans d’autres classes (il n’est pas autonome), mais la classe <xref:System.Windows.Media.Visual> fournit un type connu qui est utilisé par le rendu des processus à différents niveaux. <xref:System.Windows.Media.Visual> implémente le test de positionnement, mais il n’expose pas les événements qui signalent les tests de positionnement positifs (ils sont en <xref:System.Windows.UIElement>). Pour plus d’informations, consultez [Programmation de la couche visuelle](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> simule l’immuabilité dans un objet mutable en fournissant la possibilité de générer des copies de l’objet lorsqu’un objet immuable est requis ou souhaité pour des raisons de performances. Le type de <xref:System.Windows.Freezable> fournit une base commune pour certains éléments graphiques tels que les géométries et les pinceaux, ainsi que les animations. En particulier, un <xref:System.Windows.Freezable> n’est pas un <xref:System.Windows.Media.Visual>; elle peut contenir des propriétés qui deviennent des sous-propriétés lorsque le <xref:System.Windows.Freezable> est appliqué pour remplir une valeur de propriété d’un autre objet, et ces sous-propriétés peuvent affecter le rendu. Pour plus d’informations, consultez [Vue d’ensemble des objets Freezable](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> est une classe dérivée <xref:System.Windows.Freezable> qui ajoute spécifiquement la couche de contrôle de l’animation et certains membres de l’utilitaire afin que les propriétés animées puissent être distinguées des propriétés non animées.  
  
### <a name="control"></a>Contrôle  
 <xref:System.Windows.Controls.Control> est la classe de base prévue pour le type d’objet qui est à plusieurs termes un contrôle ou un composant, en fonction de la technologie. En général, les classes de contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont des classes qui représentent directement un contrôle d’interface utilisateur ou qui participent étroitement à la composition de contrôle. La fonctionnalité principale que <xref:System.Windows.Controls.Control> active est la création de modèles de contrôle.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Control>
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Architecture de WPF](wpf-architecture.md)
