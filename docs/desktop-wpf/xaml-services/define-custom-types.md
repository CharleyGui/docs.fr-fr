---
title: Définition de types personnalisés pour les utiliser avec les services XAML .NET
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: ff7e4229450e801a6d618c5141efde8cdcbef03d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071856"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>Définir les types personnalisés pour une utilisation avec .NET XAML Services

Lorsque vous définissez des types personnalisés qui sont des objets d’affaires ou des types qui n’ont pas de dépendance à l’égard de cadres spécifiques, il existe certaines meilleures pratiques pour XAML que vous pouvez suivre. Si vous suivez ces pratiques, .NET XAML Services et ses lecteurs XAML et les écrivains XAML peuvent découvrir les caractéristiques XAML de votre type et lui donner une représentation appropriée dans un flux de nœuds XAML en utilisant le système de type XAML. Ce sujet décrit les meilleures pratiques pour les définitions de type, les définitions des membres et l’attribution clR des types ou des membres.

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Modèles de constructeurs et définitions de type pour XAML

Pour être instantanée comme élément objet dans XAML, une classe personnalisée doit répondre aux exigences suivantes :

- La classe personnalisée doit être publique et doit exposer un constructeur public sans paramètres. (Consultez la section suivante pour des remarques concernant les structures.)

- La classe personnalisée ne doit pas être une classe imbriquée. Le « point » supplémentaire dans le chemin de nom complet rend la division de classe-namespace ambigu, et interfère avec d’autres dispositifs XAML tels que les propriétés jointes.
Si un objet peut être instantané comme élément d’objet, l’objet créé peut remplir la forme d’élément de propriété de toutes les propriétés qui prennent l’objet comme leur type sous-jacent.

Vous pouvez toujours fournir des valeurs d’objet pour les types qui ne répondent pas à ces critères, si vous activez un convertisseur de valeur. Pour plus d’informations, voir [Type Converters et Markup Extensions pour XAML](type-converters-and-markup-extensions.md).

### <a name="structures"></a>Structures

Les structures sont toujours capables d’être construites en XAML, selon la définition clR. C’est parce qu’un compilateur CLR crée implicitement un constructeur sans paramètres pour une structure. Ce constructeur initialise toutes les valeurs de propriété à leurs défauts.

Dans certains cas, le comportement de construction par défaut pour une structure n’est pas souhaitable. C’est peut-être parce que la structure est destinée à remplir les valeurs et à fonctionner conceptuellement en tant que syndicat. En tant que syndicat, les valeurs contenues peuvent avoir des interprétations mutuellement exclusives et, par conséquent, aucune de ses propriétés n’est définie. Un exemple d’une telle structure <xref:System.Windows.GridLength>dans le vocabulaire WPF est . Ces structures devraient mettre en œuvre un convertisseur de type afin que les valeurs puissent s’exprimer sous forme d’attribut, en utilisant des conventions de chaîne qui créent les différentes interprétations ou modes des valeurs de la structure. La structure devrait également exposer un comportement similaire pour la construction de code par l’intermédiaire d’un constructeur non-paramètre.

### <a name="interfaces"></a>Interfaces

Les interfaces peuvent être utilisées comme types sous-jacents de membres. Le système de type XAML vérifie la liste assignable et s’attend à ce que l’objet qui est fourni comme valeur peut être attribué à l’interface. Il n’y a aucune idée de la façon dont l’interface doit être présentée comme un type XAML tant qu’un type assignable pertinent prend en charge les exigences de construction XAML.

### <a name="factory-methods"></a>Méthodes d’usine

Les méthodes d’usine sont une fonctionnalité XAML 2009. Ils modifient le principe XAML selon lequel les objets doivent avoir des constructeurs sans paramètres. Les méthodes d’usine ne sont pas documentées dans cet article. Voir [x:FactoryMethod Directive](xfactorymethod-directive.md).

## <a name="enumerations"></a>Énumérations

Les énumérations ont un comportement de conversion de type natif XAML. Les noms constants d’énumération spécifiés dans XAML sont résolus par rapport au type de recensement sous-jacent, et retournent la valeur de recensement à un auteur d’objets XAML.

XAML prend en charge une utilisation de <xref:System.FlagsAttribute> type pavillon pour les énumérations avec appliqué. Pour plus d’informations, voir [XAML Syntax In Detail](../../framework/wpf/advanced/xaml-syntax-in-detail.md). ([XAML Syntax In Detail](../../framework/wpf/advanced/xaml-syntax-in-detail.md) est écrit pour le public WPF, mais la plupart des informations dans ce sujet est pertinente pour XAML qui n’est pas spécifique à un cadre de mise en œuvre particulier.)

## <a name="member-definitions"></a>Définitions des membres

Les types peuvent définir les membres pour l’utilisation de XAML. Il est possible pour les types de définir les membres qui sont utilisables XAML, même si ce type spécifique n’est pas XAML-utilisable. Ceci est possible en raison de l’héritage CLR. Tant qu’un certain type qui hérite du membre prend en charge l’utilisation de XAML comme un type, et le membre prend en charge l’utilisation de XAML pour son type sous-jacent ou a une syntaxe XAML native disponible, ce membre est XAML-utilisable.

### <a name="properties"></a>Propriétés

Si vous définissez les propriétés comme une `get` `set` propriété PUBLIQUE CLR en utilisant les modèles typiques de CLR et d’accesseur et les mots clés de type langue-approprié, le système de type XAML peut déclarer la propriété en tant que membre avec des informations appropriées fournies pour <xref:System.Xaml.XamlMember> les propriétés, telles que <xref:System.Xaml.XamlMember.IsReadPublic%2A> et <xref:System.Xaml.XamlMember.IsWritePublic%2A>.

Des propriétés spécifiques peuvent activer une syntaxe textuelle en appliquant <xref:System.ComponentModel.TypeConverterAttribute>. Pour plus d’informations, voir [Type Converters et Markup Extensions pour XAML](type-converters-and-markup-extensions.md).

En l’absence d’une syntaxe textuelle ou d’une conversion native XAML et en l’absence d’indirection supplémentaire, comme l’utilisation d’une extension de balisage, le type de propriété (dans<xref:System.Xaml.XamlMember.TargetType%2A> le système de type XAML) doit être en mesure de retourner une instance à un auteur d’objets XAML en traitant le type cible comme un type CLR.

Si vous utilisez XAML 2009, [x:Reference Markup Extension](xreference-markup-extension.md) peut être utilisé pour fournir des valeurs si les considérations précédentes ne sont pas remplies; cependant, il s’agit plus d’un problème d’utilisation qu’d’un problème de définition de type.

### <a name="events"></a>Événements

Si vous définissez les événements comme un événement PUBLIC CLR, le <xref:System.Xaml.XamlMember.IsEvent%2A> système `true`de type XAML peut signaler l’événement en tant que membre avec comme . Le câblage des gestionnaires d’événements n’est pas dans le cadre des capacités .NET XAML Services; le câblage est laissé à des cadres et des implémentations spécifiques.

### <a name="methods"></a>Méthodes

Le code inline pour les méthodes n’est pas une capacité XAML par défaut. Dans la plupart des cas, vous ne référencez pas directement les membres de la méthode de XAML, et le rôle des méthodes dans XAML est seulement de fournir un soutien pour des modèles spécifiques XAML. [x:FactoryMethod Directive](xfactorymethod-directive.md) est une exception.

### <a name="fields"></a>Champs

Les lignes directrices en matière de conception de CLR découragent les champs nonstatiques. Pour les champs statiques, vous ne pouvez accéder aux valeurs statiques du champ que grâce à [x:Static Markup Extension](xstatic-markup-extension.md); dans ce cas, vous ne faites rien de spécial dans la définition CLR pour exposer un champ pour [x:Utilisations statiques.](xstatic-markup-extension.md)

## <a name="attachable-members"></a>Membres attachables

Les membres attachables sont exposés à XAML par le biais d’un modèle de méthode d’accesseur sur un type définissant. Le type définissant lui-même n’a pas besoin d’être XAML-utilisable comme un objet. En fait, un modèle commun est de déclarer une classe de service dont le rôle est de posséder le membre attachable et de mettre en œuvre les comportements connexes, mais ne servent aucune autre fonction telle qu’une représentation d’assurance-chômage. Pour les sections suivantes, le propriétaire de place *PropertyName* représente le nom de votre membre attachable. Ce nom doit être valable dans la [grammaire XamlName](xamlname-grammar.md).

Soyez prudent des collisions de nom entre ces modèles et d’autres méthodes d’un type. Si un membre existe qui correspond à l’un des modèles, il peut être interprété comme une voie d’utilisation des membres attachable par un processeur XAML, même si ce n’était pas votre intention.

#### <a name="the-getpropertyname-accessor"></a>L’accesseur GetPropertyName

La signature `GetPropertyName` pour l’accesseur doit être :

`public static object GetPropertyName(object target)`

- L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Vous pouvez l’utiliser pour établir la portée de l’utilisation de votre membre attachable; les utilisations en dehors de votre portée prévue jetteront des exceptions de casting invalides qui sont ensuite faites surface par une erreur d’analyse XAML. Le nom `target` du paramètre n’est pas une exigence, mais est nommé `target` par convention dans la plupart des implémentations.

- La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation.

Pour prendre <xref:System.ComponentModel.TypeConverter> en charge une syntaxe textuelle <xref:System.ComponentModel.TypeConverterAttribute> activée `GetPropertyName` pour l’utilisation d’attributs du membre attachable, appliquez-le à l’accesseur. S’appliquer `get` au `set` lieu de la peut sembler non-intuitif; toutefois, cette convention peut soutenir le concept de membres attachables qui sont sérialisants, ce qui est utile dans les scénarios de concepteur.

#### <a name="the-setpropertyname-accessor"></a>L’accesseur SetPropertyName

La signature `SetPropertyName` pour l’accesseur doit être :

`public static void SetPropertyName(object target, object value)`

- L’objet `target` peut être spécifié comme un type plus spécifique dans votre implémentation, avec la même logique et les mêmes conséquences que décrites dans la section précédente.

- L’objet `value` peut être défini comme un type plus spécifique dans votre implémentation.

Rappelez-vous que la valeur de cette méthode est l’entrée provenant de l’utilisation XAML, généralement sous forme d’attribut. De forme d’attribut il doit y avoir le support de `GetPropertyName`convertisseur de valeur pour une syntaxe de texte, et vous attribuez sur l’accesseur de s.

### <a name="attachable-member-stores"></a>Magasins membres attachables

Les méthodes d’accesseur ne sont généralement pas suffisantes pour fournir un moyen de placer les valeurs des membres attachables dans un graphique d’objet, ou pour récupérer des valeurs du graphique de l’objet et les sérialiser correctement. Pour fournir cette fonctionnalité, les `target` objets des signatures d’accesseur précédents doivent être capables de stocker des valeurs. Le mécanisme de stockage devrait être conforme au principe du membre attachable selon lequel le membre est attaché aux cibles lorsque le membre attachable ne fait pas partie de la liste des membres. .NET XAML Services fournit une technique de mise <xref:System.Xaml.IAttachedPropertyStore> en <xref:System.Xaml.AttachablePropertyServices>œuvre pour les magasins de membres attachables par le biais des API et . <xref:System.Xaml.IAttachedPropertyStore>est utilisé par les auteurs XAML pour découvrir la mise en `target` œuvre du magasin, et doit être mis en œuvre sur le type qui est le des accesseurs. Les <xref:System.Xaml.AttachablePropertyServices> API statiques sont utilisées dans le corps des accesseurs, <xref:System.Xaml.AttachableMemberIdentifier>et se réfèrent au membre attachable par son .

## <a name="xaml-related-clr-attributes"></a>Attributs CLR liés à XAML

Il est important d’attribuer correctement vos types, membres et assemblages afin de signaler les informations du système de type XAML à .NET XAML Services. La communication des informations du système de type XAML est pertinente si l’une ou l’autre des situations suivantes s’applique :

- Vous avez l’intention de vos types pour une utilisation avec les systèmes XAML qui sont directement basés sur .NET XAML Services lecteurs XAML et les écrivains XAML.
- Vous définissez ou utilisez un cadre d’utilisation XAML basé sur ces lecteurs XAML et les écrivains XAML.

Pour une liste de chaque attribut XAML qui est pertinent pour le support XAML de vos types [personnalisés, consultez XAML-Related CLR Attributes for Custom Types and Libraries](clr-attributes-with-custom-types-and-libraries.md).

## <a name="usage"></a>Usage

L’utilisation de types personnalisés exige que l’auteur de balisage doit cartographier un préfixe pour l’assemblage et l’espace de nom CLR qui contiennent le type personnalisé. Cette procédure n’est pas documentée dans ce sujet.

## <a name="access-level"></a>Niveau d’accès

XAML fournit un moyen de charger et `internal` d’instantanéiser les types qui ont un niveau d’accès. Cette capacité est fournie de sorte que le code utilisateur peut définir ses propres types, puis instantané les classes de balisage qui fait également partie de la même portée de code utilisateur.

Un exemple de WPF est chaque <xref:System.Windows.Controls.UserControl> fois que le code utilisateur définit un qui est destiné comme un moyen de refactorer un `public` comportement d’interface utilisateur, mais pas dans le cadre de tout mécanisme d’extension possible qui pourrait être implicite en déclarant la classe de support avec le niveau d’accès. Un <xref:System.Windows.Controls.UserControl> tel peut `internal` être déclaré avec accès si le code de sauvegarde est compilé dans la même assemblée à partir de laquelle il est référencé comme un type XAML.

Pour une application qui charge XAML <xref:System.Xaml.XamlObjectWriter>en pleine `internal` confiance et utilise, le chargement des classes avec niveau d’accès est toujours activé.

Pour une application qui charge XAML en fiducie partielle, vous <xref:System.Xaml.Permissions.XamlAccessLevel> pouvez contrôler les caractéristiques du niveau d’accès en utilisant l’API. En outre, les mécanismes de report (tels que le système de modèle WPF) doivent être en mesure de propager les autorisations de niveau d’accès et de les préserver pour les évaluations éventuelles du temps d’exécution; ceci est géré à <xref:System.Xaml.Permissions.XamlAccessLevel> l’interne en transmettant l’information.

### <a name="wpf-implementation"></a>Mise en œuvre du WPF

WPF XAML utilise un modèle d’accès à la fiducie partielle où si BAML est chargé en fiducie partielle, l’accès est limité à <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> l’assemblage qui est la source BAML. Pour le report, WPF utilise <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> comme mécanisme pour passer les informations de niveau d’accès.

Dans la terminologie WPF XAML, un *type interne* est un type qui est défini par le même assemblage qui comprend également le référencement XAML. Un tel type peut être cartographié à travers un espace de nom XAML qui `xmlns:local="clr-namespace:WPFApplication1"`omet délibérément la partie assemblage d’une cartographie, par exemple, . Si BAML fait référence à `internal` un type interne et `GeneratedInternalTypeHelper` que ce type a un niveau d’accès, cela génère une classe pour l’assemblage. Si vous voulez `GeneratedInternalTypeHelper`éviter, vous `public` devez soit utiliser le niveau d’accès, ou devez tenir compte de la classe concernée dans un assemblage séparé et rendre cet assemblage dépendant.

## <a name="see-also"></a>Voir aussi

- [Attributs CLR XAML pour les bibliothèques et types personnalisés](clr-attributes-with-custom-types-and-libraries.md)
- [Services XAML](../../../api/index.md)
