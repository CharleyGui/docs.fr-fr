---
title: XAML et classes personnalisées
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 8dab7310826357d7fbe434002298032b8722e5b5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744428"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML et classes personnalisées pour WPF
XAML implémenté dans les infrastructures common language runtime (CLR) prend en charge la possibilité de définir une classe ou une structure personnalisée dans n’importe quel langage common language runtime (CLR), puis d’accéder à cette classe à l’aide du balisage XAML. Vous pouvez utiliser un mélange de types définis de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et de vos types personnalisés dans le même fichier de balisage, généralement en mappant les types personnalisés à un préfixe d’espace de noms XAML. Cette rubrique décrit les conditions que doit satisfaire une classe personnalisée pour pouvoir être utilisée comme élément XAML.  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Classes personnalisées dans les applications ou les assemblys  
 Les classes personnalisées qui sont utilisés dans XAML peuvent être définies de deux façons distinctes : dans le code-behind ou dans un autre code produisant l’application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] principale, ou comme une classe dans un assembly distinct, comme un fichier exécutable ou une DLL utilisée comme bibliothèque de classes. Chacune de ces approches a des avantages et des inconvénients spécifiques.  
  
- L’avantage de créer une bibliothèque de classes est que ces classes personnalisées peuvent être partagées entre de nombreuses applications différentes. Une bibliothèque distincte facilite également le contrôle des problèmes de gestion des versions des applications et simplifie la création d’une classe là où l’utilisation prévue de la classe est d’être un élément racine dans une page XAML.  
  
- L’avantage de définir les classes personnalisées dans l’application est que cette technique est relativement légère et réduit les problèmes de déploiement et de test rencontrés quand vous introduisez des assemblys distincts au-delà de l’exécutable principal de l’application.  
  
- Qu’elles soient définies dans le même assembly ou dans un autre, les classes personnalisées doivent être mappées entre l’espace de noms CLR et l’espace de noms XML pour pouvoir être utilisées dans XAML en tant qu’éléments. Consultez [Espaces de noms XAML et mappage d’espace de noms pour XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Spécifications pour une classe personnalisée comme élément XAML  
 Pour pouvoir être instanciée comme élément objet, votre classe doit répondre aux spécifications suivantes :  
  
- Votre classe personnalisée doit être publique et prendre en charge un constructeur public (sans paramètre). (Consultez la section suivante pour des remarques concernant les structures.)  
  
- Votre classe personnalisée ne doit pas être une classe imbriquée. Les classes imbriquées et le « point » dans leur syntaxe générale d’utilisation du CLR interfèrent avec d’autres fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et/ou XAML, comme les propriétés attachées.  
  
 En plus de permettre une syntaxe d’élément objet, votre définition d’objet permet également la syntaxe des éléments de propriété pour les autres propriétés publiques qui prennent cet objet comme type de valeur. La raison en est que l’objet peut maintenant être instancié comme un élément objet et qu’il peut remplir la valeur de l’élément propriété d’une telle propriété.  
  
### <a name="structures"></a>Structures  
 Les structures que vous définissez en tant que types personnalisés peuvent toujours être construites en XAML dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cela est dû au fait que les compilateurs CLR créent implicitement un constructeur sans paramètre pour une structure qui initialise toutes les valeurs de propriété à leurs valeurs par défaut. Dans certains cas, le comportement de construction et/ou l’utilisation de l’élément objet par défaut pour une structure ne sont pas souhaitables. La raison peut en être que la structure est destinée à remplir des valeurs et à fonctionner conceptuellement comme une union, où les valeurs contenues peuvent avoir des interprétations mutuellement exclusives, aucune de ses propriétés ne pouvant donc être définie. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exemple d’une telle structure est <xref:System.Windows.GridLength>. En règle générale, ces structures doivent implémenter un convertisseur de type, de sorte que les valeurs peuvent être exprimées sous forme d’attribut, en utilisant des conventions de chaîne qui créent les différents modes ou interprétations des valeurs de la structure. La structure doit également exposer un comportement similaire pour la construction de code via un constructeur sans paramètre.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Spécifications pour les propriétés d’une classe personnalisée en tant qu’attributs XAML  
 Les propriétés doivent référencer un type par valeur (tel qu’une primitive) ou utiliser une classe pour le type qui a un constructeur sans paramètre ou un convertisseur de type dédié auquel un processeur XAML peut accéder. Dans l’implémentation XAML CLR, les processeurs XAML trouvent ces convertisseurs via la prise en charge native des primitives de langage, ou via l’application de <xref:System.ComponentModel.TypeConverterAttribute> à un type ou un membre dans des définitions de type de stockage.  
  
 La propriété peut aussi référencer un type d’une classe abstraite ou une interface. Pour les classes abstraites ou les interfaces, l’analyse XAML nécessite que la valeur de propriété soit remplie avec des instances de classe pratiques qui implémentent l’interface, ou avec des instances des types qui dérivent de la classe abstraite.  
  
 Les propriétés peuvent être déclarées sur une classe abstraite, mais ne peuvent être définies sur des classes pratiques qui dérivent de la classe abstraite. Cela est dû au fait que la création de l’élément objet pour la classe requiert un constructeur sans paramètre public sur la classe.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Syntaxe d’attribut activée par TypeConverter  
 Si vous fournissez un convertisseur de type attribué dédié au niveau de la classe, la conversion de type appliquée permet la syntaxe d’attribut pour les propriétés qui doivent instancier ce type. Un convertisseur de type n’active pas l’utilisation d’élément objet du type ; seule la présence d’un constructeur sans paramètre pour ce type active l’utilisation de l’élément objet. Par conséquent, les propriétés qui sont activées par un convertisseur de type ne sont généralement pas utilisables dans la syntaxe de propriété, sauf si le type lui-même prend également en charge la syntaxe d’élément objet. L’exception à cela est que vous pouvez spécifier une syntaxe des éléments de propriété, mais que l’élément de propriété doit alors contenir une chaîne. Cette utilisation est essentiellement équivalente à l’utilisation d’une syntaxe d’attribut, et ce type d’utilisation n’est pas courant à moins qu’il soit nécessaire de gérer un espace blanc plus robuste de la valeur de l’attribut. Par exemple, voici une utilisation d’élément de propriété qui prend une chaîne et l’utilisation d’attribut équivalente :  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Les exemples de propriétés dans lesquelles la syntaxe d’attribut est autorisée, mais la syntaxe d’élément de propriété qui contient un élément objet n’est pas autorisée via XAML, sont différentes propriétés qui prennent le type <xref:System.Windows.Input.Cursor>. La classe <xref:System.Windows.Input.Cursor> possède un convertisseur de type dédié <xref:System.Windows.Input.CursorConverter>, mais n’expose pas de constructeur sans paramètre, de sorte que la propriété <xref:System.Windows.FrameworkElement.Cursor%2A> ne peut être définie qu’à l’aide de la syntaxe d’attribut, même si le type de <xref:System.Windows.Input.Cursor> réel est un type référence.  
  
### <a name="per-property-type-converters"></a>Convertisseurs de type par propriété  
 Une autre possibilité est que la propriété proprement dite puisse déclarer un convertisseur de type au niveau de la propriété. Cela active un « mini langage » qui instancie les objets du type de la propriété inline, en traitant les valeurs de chaîne entrantes de l’attribut comme entrée pour une opération de <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> en fonction du type approprié. En général, ceci vise à fournir un accesseur pratique, et non pas à être le seul moyen de permettre la définition d’une propriété dans XAML. Toutefois, il est également possible d’utiliser des convertisseurs de type pour les attributs où vous souhaitez utiliser des types CLR existants qui ne fournissent pas de constructeur sans paramètre ou de convertisseur de type attribué. Les exemples de l’API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont certaines propriétés qui prennent le type <xref:System.Globalization.CultureInfo>. Dans ce cas, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisé le type de <xref:System.Globalization.CultureInfo> de Microsoft .NET Framework existant pour mieux résoudre les scénarios de compatibilité et de migration utilisés dans les versions antérieures des frameworks, mais le type de <xref:System.Globalization.CultureInfo> ne prenait pas en charge les constructeurs nécessaires ou la conversion de type au niveau du type pour être utilisables directement en tant que valeur de propriété XAML.  
  
 Quand vous exposez une propriété qui a une utilisation XAML, en particulier si vous êtes un créateur de contrôles, vous devez absolument envisager de stocker cette propriété avec une propriété de dépendance. Cela est particulièrement vrai si vous utilisez l’implémentation [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] existante du processeur XAML, car vous pouvez améliorer les performances à l’aide de la sauvegarde de <xref:System.Windows.DependencyProperty>. Une propriété de dépendance exposera des fonctionnalités du système de propriétés pour votre propriété, que les utilisateurs viendront à attendre pour une propriété accessible de XAML. Ceci inclut des fonctionnalités comme l’animation, la liaison de données et la prise en charge des styles. Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md) et [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Écriture et attribution d’un convertisseur de type  
 Vous devrez parfois écrire une classe dérivée <xref:System.ComponentModel.TypeConverter> personnalisée pour fournir la conversion de type pour votre type de propriété. Pour obtenir des instructions sur la façon de dériver de et de créer un convertisseur de type qui peut prendre en charge les utilisations XAML, et comment appliquer le <xref:System.ComponentModel.TypeConverterAttribute>, consultez [TypeConverters et XAML](typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Spécifications pour la syntaxe d’attribut de gestionnaire d’événements XAML sur les événements d’une classe personnalisée  
 Pour être utilisable comme un événement CLR, l’événement doit être exposé comme un événement public sur une classe qui prend en charge un constructeur sans paramètre, ou sur une classe abstraite où l’événement est accessible sur les classes dérivées. Pour pouvoir être utilisé de manière pratique comme un événement routé, votre événement CLR doit implémenter des méthodes explicites de `add` et de `remove`, qui ajoutent et suppriment des gestionnaires pour la signature d’événement CLR et transfèrent ces gestionnaires aux méthodes <xref:System.Windows.UIElement.AddHandler%2A> et <xref:System.Windows.UIElement.RemoveHandler%2A>. Ces méthodes ajoutent ou suppriment les gestionnaires dans le magasin de gestionnaires d’événements routés sur l’instance à laquelle l’événement est attaché.  
  
> [!NOTE]
> Il est possible d’inscrire directement des gestionnaires pour les événements routés à l’aide d' <xref:System.Windows.UIElement.AddHandler%2A>, et de ne pas définir délibérément un événement CLR qui expose l’événement routé. Ceci est généralement non recommandé, car l’événement n’activera pas la syntaxe d’attribut XAML pour attacher des gestionnaires, et votre classe résultante offrira une vue XAML moins transparente des fonctionnalités de ce type.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Écriture de propriétés de collection  
 Les propriétés qui prennent un type collection ont une syntaxe XAML qui vous permet de spécifier les objets qui sont ajoutés à la collection. Cette syntaxe a deux fonctions importantes.  
  
- L’objet qui est l’objet collection n’a pas besoin d’être spécifié dans la syntaxe d’élément objet. La présence de ce type de collection est implicite quand vous spécifiez une propriété dans XAML qui prend un type collection.  
  
- Les éléments enfants de la propriété de collection dans le balisage sont traités pour devenir membres de la collection. Normalement, l’accès du code aux membres d’une collection est effectué via des méthodes de liste/dictionnaire,comme `Add`, ou via un indexeur. La syntaxe XAML ne prend cependant pas en charge les méthodes ou les indexeurs (exception : XAML 2009 peut prendre en charge des méthodes, mais l’utilisation de XAML 2009 restreint les utilisations possibles de WPF ; consultez [Fonctionnalités du langage XAML 2009](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md)). Les collections sont à l’évidence une spécification très courante pour générer une arborescence d’éléments, et vous devez disposer d’un moyen de remplir ces collections dans du XAML déclaratif. Par conséquent, les éléments enfants d’une propriété de collection sont traités en les ajoutant à la collection qui est la valeur du type de propriété de collection.  
  
 L’implémentation des services XAML .NET Framework, et donc le processeur XAML WPF, utilisent la définition suivante pour ce qui constitue une propriété de collection. Le type de propriété de la propriété doit répondre à une des conditions suivantes :  
  
- Implémente <xref:System.Collections.IList>.  
  
- Implémente <xref:System.Collections.IDictionary> ou l’équivalent générique (<xref:System.Collections.Generic.IDictionary%602>).  
  
- Dérive de <xref:System.Array> (pour plus d’informations sur les tableaux en XAML, consultez [X :Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
- Implémente <xref:System.Windows.Markup.IAddChild> (une interface définie par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Chacun de ces types dans CLR a une méthode `Add`, qui est utilisée par le processeur XAML pour ajouter des éléments à la collection sous-jacente lors de la création du graphe d’objets.  
  
> [!NOTE]
> Les interfaces `List` et `Dictionary` génériques (<xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IDictionary%602>) ne sont pas prises en charge pour la détection de collection par le processeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML. Toutefois, vous pouvez utiliser la classe <xref:System.Collections.Generic.List%601> comme classe de base, car elle implémente <xref:System.Collections.IList> directement, ou <xref:System.Collections.Generic.Dictionary%602> comme classe de base, car elle implémente <xref:System.Collections.IDictionary> directement.  
  
 Quand vous déclarez une propriété qui prend une collection, soyez attentif à la façon dont cette valeur de propriété est initialisée dans les nouvelles instances du type. Si vous n’implémentez pas la propriété en tant que propriété de dépendance, il convient que la propriété utilise un champ de stockage qui appelle le constructeur du type collection. Si votre propriété est une propriété de dépendance, vous devez initialiser la propriété de collection dans le cadre du constructeur de type par défaut. La raison en est qu’une propriété de dépendance prend sa valeur par défaut à partir des métadonnées, et vous ne voulez généralement pas que la valeur initiale d’une propriété de collection soit une collection statique et partagée. Il doit exister une instance de la collection pour chaque instance de type conteneur. Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md).  
  
 Vous pouvez implémenter un type de collection personnalisé pour votre propriété de collection. En raison du traitement implicite des propriétés de collection, le type de collection personnalisé n’a pas besoin de fournir un constructeur sans paramètre pour pouvoir être utilisé implicitement en XAML. Toutefois, vous pouvez éventuellement fournir un constructeur sans paramètre pour le type de collection. Cette pratique peut être utile. À moins que vous ne fournissiez un constructeur sans paramètre, vous ne pouvez pas déclarer explicitement la collection en tant qu’élément objet. Certains créateurs de balisage peuvent préférer voir la collection explicite comme une question de style de balisage. En outre, un constructeur sans paramètre peut simplifier les spécifications d’initialisation lorsque vous créez des objets qui utilisent votre type de collection en tant que valeur de propriété.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Déclaration de propriétés de contenu XAML  
 Le langage XAML définit le concept de propriété de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Chaque classe utilisable dans la syntaxe d’objet peut avoir une et une seule propriété de contenu XAML. Pour déclarer une propriété comme étant la propriété de contenu XAML pour votre classe, appliquez la <xref:System.Windows.Markup.ContentPropertyAttribute> dans le cadre de la définition de classe. Spécifiez le nom de la propriété de contenu XAML prévue en tant que <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> dans l’attribut. La propriété est spécifiée sous la forme d’une chaîne par son nom, et non comme une construction de réflexion comme <xref:System.Reflection.PropertyInfo>.  
  
 Vous pouvez spécifier qu’une propriété de collection doit être la propriété de contenu XAML. Ceci aboutit à une utilisation de cette propriété où l’élément objet peut avoir un ou plusieurs éléments enfants, sans éléments objet de collection intermédiaires ou de balises d’élément de propriété. Ces éléments sont ensuite traités comme étant la valeur pour la propriété de contenu XAML et ajoutés à l’instance de collection de stockage.  
  
 Certaines propriétés de contenu XAML existantes utilisent le type de propriété `Object`. Cela active une propriété de contenu XAML qui peut prendre des valeurs primitives telles qu’une <xref:System.String>, ainsi qu’une valeur d’objet de référence unique. Si vous suivez ce modèle, votre type est responsable de la détermination du type, ainsi que de la gestion des types possibles. La raison courante d’un type de contenu <xref:System.Object> est de prendre en charge à la fois un moyen simple d’ajouter du contenu d’objet sous forme de chaîne (qui reçoit un traitement de présentation par défaut), ou un moyen avancé d’ajouter du contenu d’objet qui spécifie une présentation non définie par défaut ou des données supplémentaires.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Sérialisation du XAML  
 Dans certains cas, par exemple si vous êtes créateur de contrôles, vous voulez aussi garantir qu’une représentation d’objet qui peut être instanciée en XAML peut également être sérialisée dans un balisage XAML équivalent. Les spécifications de la sérialisation ne sont pas décrites dans cette rubrique. Consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md) et [Sérialisation et arborescence d’éléments](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Vue d’ensemble des éléments de base](base-elements-overview.md)
- [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md)
