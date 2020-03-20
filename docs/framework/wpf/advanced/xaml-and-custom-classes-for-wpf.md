---
title: XAML et classes personnalisées
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 4cd0ba7fa03d2578f4477c3ccf53188fbbea2dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186260"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML et classes personnalisées pour WPF
XAML tel qu’il est mis en œuvre dans les cadres de l’heure courante (CLR) appuie la capacité de définir une classe ou une structure personnalisée dans n’importe quelle langue courante commune (CLR), puis d’accéder à cette classe en utilisant la balisage XAML. Vous pouvez utiliser un mélange de types définis de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et de vos types personnalisés dans le même fichier de balisage, généralement en mappant les types personnalisés à un préfixe d’espace de noms XAML. Cette rubrique décrit les conditions que doit satisfaire une classe personnalisée pour pouvoir être utilisée comme élément XAML.  

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
 Structures que vous définissez comme types personnalisés sont [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] toujours en mesure d’être construit en XAML dans . C’est parce que les compilateurs CLR créent implicitement un constructeur sans paramètres pour une structure qui initialise toutes les valeurs de propriété à leurs défauts. Dans certains cas, le comportement de construction et/ou l’utilisation de l’élément objet par défaut pour une structure ne sont pas souhaitables. La raison peut en être que la structure est destinée à remplir des valeurs et à fonctionner conceptuellement comme une union, où les valeurs contenues peuvent avoir des interprétations mutuellement exclusives, aucune de ses propriétés ne pouvant donc être définie. Un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exemple d’une <xref:System.Windows.GridLength>telle structure est . En règle générale, ces structures doivent implémenter un convertisseur de type, de sorte que les valeurs peuvent être exprimées sous forme d’attribut, en utilisant des conventions de chaîne qui créent les différents modes ou interprétations des valeurs de la structure. La structure devrait également exposer un comportement similaire pour la construction de code par l’intermédiaire d’un constructeur non-paramètre.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Spécifications pour les propriétés d’une classe personnalisée en tant qu’attributs XAML  
 Les propriétés doivent faire référence à un type de valeur par rapport (comme un primitif), ou utiliser une classe pour un type qui a soit un constructeur sans paramètres ou un convertisseur de type dédié à laquelle un processeur XAML peut accéder. Dans la mise en œuvre de CLR XAML, les processeurs XAML <xref:System.ComponentModel.TypeConverterAttribute> trouvent de tels convertisseurs par le biais d’un support autochtone pour les primitifs linguistiques, soit par l’application à un type ou à un membre dans des définitions de type de support  
  
 La propriété peut aussi référencer un type d’une classe abstraite ou une interface. Pour les classes abstraites ou les interfaces, l’analyse XAML nécessite que la valeur de propriété soit remplie avec des instances de classe pratiques qui implémentent l’interface, ou avec des instances des types qui dérivent de la classe abstraite.  
  
 Les propriétés peuvent être déclarées sur une classe abstraite, mais ne peuvent être définies sur des classes pratiques qui dérivent de la classe abstraite. C’est parce que la création de l’élément objet pour la classe à tous nécessite un constructeur public sans paramètres sur la classe.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Syntaxe d’attribut activée par TypeConverter  
 Si vous fournissez un convertisseur de type attribué dédié au niveau de la classe, la conversion de type appliquée permet la syntaxe d’attribut pour les propriétés qui doivent instancier ce type. Un convertisseur de type ne permet pas l’utilisation d’élément objet du type ; seule la présence d’un constructeur sans paramètres pour ce type permet l’utilisation de l’élément objet. Par conséquent, les propriétés qui sont activées par un convertisseur de type ne sont généralement pas utilisables dans la syntaxe de propriété, sauf si le type lui-même prend également en charge la syntaxe d’élément objet. L’exception à cela est que vous pouvez spécifier une syntaxe des éléments de propriété, mais que l’élément de propriété doit alors contenir une chaîne. Cette utilisation est vraiment essentiellement équivalente à une utilisation de syntaxe d’attribut, et une telle utilisation n’est pas commune à moins qu’il y ait un besoin pour la manipulation plus robuste de l’espace blanc de la valeur d’attribut. Par exemple, voici une utilisation d’élément de propriété qui prend une chaîne et l’utilisation d’attribut équivalente :  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Des exemples de propriétés où la syntaxe d’attribut est permise mais la syntaxe d’élément de propriété qui contient un élément d’objet est refusée par XAML sont diverses propriétés qui prennent le <xref:System.Windows.Input.Cursor> type. La <xref:System.Windows.Input.Cursor> classe a un <xref:System.Windows.Input.CursorConverter>convertisseur de type dédié, mais n’expose pas un constructeur sans paramètres, de sorte que la <xref:System.Windows.FrameworkElement.Cursor%2A> propriété ne peut être définie par syntaxe d’attribut même si le type réel <xref:System.Windows.Input.Cursor> est un type de référence.  
  
### <a name="per-property-type-converters"></a>Convertisseurs de type par propriété  
 Une autre possibilité est que la propriété proprement dite puisse déclarer un convertisseur de type au niveau de la propriété. Cela permet un "mini langage" qui instantanéise les objets du type de propriété en ligne, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> en traitant les valeurs de chaîne entrantes de l’attribut comme entrée pour une opération basée sur le type approprié. En général, ceci vise à fournir un accesseur pratique, et non pas à être le seul moyen de permettre la définition d’une propriété dans XAML. Cependant, il est également possible d’utiliser des convertisseurs de type pour les attributs où vous souhaitez utiliser les types CLR existants qui ne fournissent pas soit un constructeur sans paramètres ou un convertisseur de type attribué. Les exemples de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’API <xref:System.Globalization.CultureInfo> sont certaines propriétés qui prennent le type. Dans ce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cas, a utilisé <xref:System.Globalization.CultureInfo> le type cadre Microsoft .NET existant pour mieux aborder les scénarios de <xref:System.Globalization.CultureInfo> compatibilité et de migration qui ont été utilisés dans les versions antérieures des cadres, mais le type n’a pas soutenu les constructeurs nécessaires ou la conversion de type de type pour être utilisable comme une valeur de propriété XAML directement.  
  
 Quand vous exposez une propriété qui a une utilisation XAML, en particulier si vous êtes un créateur de contrôles, vous devez absolument envisager de stocker cette propriété avec une propriété de dépendance. Cela est particulièrement vrai [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] si vous utilisez la mise en œuvre <xref:System.Windows.DependencyProperty> existante du processeur XAML, car vous pouvez améliorer les performances en utilisant le support. Une propriété de dépendance exposera des fonctionnalités du système de propriétés pour votre propriété, que les utilisateurs viendront à attendre pour une propriété accessible de XAML. Ceci inclut des fonctionnalités comme l’animation, la liaison de données et la prise en charge des styles. Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md) et [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Écriture et attribution d’un convertisseur de type  
 Vous devrez parfois écrire <xref:System.ComponentModel.TypeConverter> une classe dérivée personnalisée pour fournir la conversion de type pour votre type de propriété. Pour des instructions sur la façon de dériver et de créer un convertisseur <xref:System.ComponentModel.TypeConverterAttribute>de type qui peut prendre en charge les utilisations XAML, et comment appliquer le , voir [TypeConverters et XAML](typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Spécifications pour la syntaxe d’attribut de gestionnaire d’événements XAML sur les événements d’une classe personnalisée  
 Pour être utilisable en tant qu’événement CLR, l’événement doit être exposé comme un événement public sur une classe qui prend en charge un constructeur sans paramètres, ou sur une classe abstraite où l’événement peut être consulté sur des classes dérivées. Afin d’être utilisé commodément comme un événement routé, votre événement CLR devrait mettre en œuvre `add` explicite et <xref:System.Windows.UIElement.RemoveHandler%2A> `remove` les méthodes, qui ajoutent et suppriment les gestionnaires pour la signature de l’événement CLR et transmettre ces gestionnaires à la et les <xref:System.Windows.UIElement.AddHandler%2A> méthodes. Ces méthodes ajoutent ou suppriment les gestionnaires dans le magasin de gestionnaires d’événements routés sur l’instance à laquelle l’événement est attaché.  
  
> [!NOTE]
> Il est possible d’enregistrer directement les <xref:System.Windows.UIElement.AddHandler%2A>gestionnaires pour les événements acheminés à l’aide de , et de ne pas définir délibérément un événement CLR qui expose l’événement acheminé. Ceci est généralement non recommandé, car l’événement n’activera pas la syntaxe d’attribut XAML pour attacher des gestionnaires, et votre classe résultante offrira une vue XAML moins transparente des fonctionnalités de ce type.  
  
<a name="Collection_Properties"></a>
## <a name="writing-collection-properties"></a>Écriture de propriétés de collection  
 Les propriétés qui prennent un type collection ont une syntaxe XAML qui vous permet de spécifier les objets qui sont ajoutés à la collection. Cette syntaxe a deux fonctions importantes.  
  
- L’objet qui est l’objet collection n’a pas besoin d’être spécifié dans la syntaxe d’élément objet. La présence de ce type de collection est implicite quand vous spécifiez une propriété dans XAML qui prend un type collection.  
  
- Les éléments enfants de la propriété de collection dans le balisage sont traités pour devenir membres de la collection. Normalement, l’accès du code aux membres d’une collection est effectué via des méthodes de liste/dictionnaire,comme `Add`, ou via un indexeur. La syntaxe XAML ne prend cependant pas en charge les méthodes ou les indexeurs (exception : XAML 2009 peut prendre en charge des méthodes, mais l’utilisation de XAML 2009 restreint les utilisations possibles de WPF ; consultez [Fonctionnalités du langage XAML 2009](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md)). Les collections sont à l’évidence une spécification très courante pour générer une arborescence d’éléments, et vous devez disposer d’un moyen de remplir ces collections dans du XAML déclaratif. Par conséquent, les éléments enfants d’une propriété de collection sont traités en les ajoutant à la collection qui est la valeur du type de propriété de collection.  
  
 L’implémentation des services XAML .NET Framework, et donc le processeur XAML WPF, utilisent la définition suivante pour ce qui constitue une propriété de collection. Le type de propriété de la propriété doit répondre à une des conditions suivantes :  
  
- Implémente <xref:System.Collections.IList>.  
  
- Impléments <xref:System.Collections.IDictionary> ou<xref:System.Collections.Generic.IDictionary%602>l’équivalent générique ( ).  
  
- Dérive de <xref:System.Array> (pour plus d’informations sur les tableaux dans XAML, voir [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
- Implémente <xref:System.Windows.Markup.IAddChild> (une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]interface définie par ).  
  
 Chacun de ces types dans CLR a une méthode `Add`, qui est utilisée par le processeur XAML pour ajouter des éléments à la collection sous-jacente lors de la création du graphe d’objets.  
  
> [!NOTE]
> Les `List` génériques `Dictionary` et<xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IDictionary%602>les interfaces ( et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ) ne sont pas pris en charge pour la détection de la collecte par le processeur XAML. Cependant, vous pouvez <xref:System.Collections.Generic.List%601> utiliser la classe comme une <xref:System.Collections.IList> classe <xref:System.Collections.Generic.Dictionary%602> de base, parce qu’elle implémente directement, ou comme classe de base, parce qu’elle implémente <xref:System.Collections.IDictionary> directement.  
  
 Quand vous déclarez une propriété qui prend une collection, soyez attentif à la façon dont cette valeur de propriété est initialisée dans les nouvelles instances du type. Si vous n’implémentez pas la propriété en tant que propriété de dépendance, il convient que la propriété utilise un champ de stockage qui appelle le constructeur du type collection. Si votre propriété est une propriété de dépendance, vous devez initialiser la propriété de collection dans le cadre du constructeur de type par défaut. La raison en est qu’une propriété de dépendance prend sa valeur par défaut à partir des métadonnées, et vous ne voulez généralement pas que la valeur initiale d’une propriété de collection soit une collection statique et partagée. Il doit exister une instance de la collection pour chaque instance de type conteneur. Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md).  
  
 Vous pouvez implémenter un type de collection personnalisé pour votre propriété de collection. En raison du traitement implicite de la propriété de collecte, le type de collecte personnalisé n’a pas besoin de fournir un constructeur sans paramètres afin d’être employé dans XAML implicitement. Cependant, vous pouvez fournir en option un constructeur sans paramètres pour le type de collecte. Cette pratique peut être utile. Sauf si vous fournissez un constructeur sans paramètres, vous ne pouvez pas déclarer explicitement la collection comme un élément d’objet. Certains créateurs de balisage peuvent préférer voir la collection explicite comme une question de style de balisage. En outre, un constructeur sans paramètres peut simplifier les exigences d’initialisation lorsque vous créez de nouveaux objets qui utilisent votre type de collection comme valeur de propriété.  
  
<a name="XAMLCONtent"></a>
## <a name="declaring-xaml-content-properties"></a>Déclaration de propriétés de contenu XAML  
 Le langage XAML définit le concept de propriété de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Chaque classe utilisable dans la syntaxe d’objet peut avoir une et une seule propriété de contenu XAML. Pour déclarer une propriété comme propriété de contenu XAML pour votre classe, appliquez-la dans le <xref:System.Windows.Markup.ContentPropertyAttribute> cadre de la définition de classe. Spécifier le nom de la <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> propriété de contenu XAML prévue comme l’attribut dans l’attribut. La propriété est spécifiée comme une chaîne par <xref:System.Reflection.PropertyInfo>nom, pas comme une construction de réflexion comme .  
  
 Vous pouvez spécifier qu’une propriété de collection doit être la propriété de contenu XAML. Ceci aboutit à une utilisation de cette propriété où l’élément objet peut avoir un ou plusieurs éléments enfants, sans éléments objet de collection intermédiaires ou de balises d’élément de propriété. Ces éléments sont ensuite traités comme étant la valeur pour la propriété de contenu XAML et ajoutés à l’instance de collection de stockage.  
  
 Certaines propriétés de contenu XAML existantes utilisent le type de propriété `Object`. Cela permet une propriété de contenu XAML <xref:System.String> qui peut prendre des valeurs primitives telles que un ainsi que de prendre une valeur d’objet de référence unique. Si vous suivez ce modèle, votre type est responsable de la détermination du type, ainsi que de la gestion des types possibles. La raison typique <xref:System.Object> d’un type de contenu est de prendre en charge à la fois un moyen simple d’ajouter du contenu de l’objet comme une chaîne (qui reçoit un traitement de présentation par défaut), ou un moyen avancé d’ajouter du contenu de l’objet qui spécifie une présentation non par défaut ou des données supplémentaires.  
  
<a name="Serializing"></a>
## <a name="serializing-xaml"></a>Sérialisation du XAML  
 Dans certains cas, par exemple si vous êtes créateur de contrôles, vous voulez aussi garantir qu’une représentation d’objet qui peut être instanciée en XAML peut également être sérialisée dans un balisage XAML équivalent. Les spécifications de la sérialisation ne sont pas décrites dans cette rubrique. Consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md) et [Sérialisation et arborescence d’éléments](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Vue d’ensemble des éléments de base](base-elements-overview.md)
- [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md)
