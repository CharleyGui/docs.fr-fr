---
title: Vue d'ensemble des extensions de balisage pour XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: efb41f31a3baa895b5739021af5fa36e32aefeea
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556991"
---
# <a name="overview-of-markup-extensions-for-xaml"></a>Vue d’ensemble des extensions de balisage pour XAML

Les extensions de balisage sont une technique XAML permettant d’obtenir une valeur qui n’est ni une primitive ni un type XAML spécifique. Pour l'utilisation d'attributs, les extensions de balisage utilisent la séquence de caractères connue d'une accolade ouvrante `{` pour entrer la portée d'extension de balisage et d'une accolade fermante `}` pour quitter. Lorsque vous utilisez les services XAML .NET, vous pouvez utiliser certaines extensions de balisage de langage XAML prédéfinies à partir de l’assembly System. Xaml. Vous pouvez également créer une sous-classe à partir de la classe <xref:System.Windows.Markup.MarkupExtension> , définie dans System.Xaml, et définir vos propres extensions de balisage. Ou vous pouvez utiliser des extensions de balisage définies par une infrastructure particulière si vous référencez déjà cette infrastructure.

Lorsqu'une utilisation d'extension de balisage fait l'objet d'un accès, le writer d'objet XAML peut fournir des services à une classe <xref:System.Windows.Markup.MarkupExtension> personnalisée via un point de connexion de service dans la substitution <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> . Les services peuvent être utilisés pour obtenir le contexte concernant l'utilisation, les fonctions spécifiques du writer d'objet, le contexte de schéma XAML, etc.

## <a name="xaml-defined-markup-extensions"></a>Extensions de balisage définies en XAML

Plusieurs extensions de balisage sont implémentées par les services XAML .NET pour la prise en charge du langage XAML. Ces extensions de balisage font partie de la spécification de XAML en tant que langage. Elles sont généralement identifiables par le préfixe `x:` dans la syntaxe, comme observé dans l'utilisation courante. Les implémentations des services XAML .NET pour ces éléments de langage XAML dérivent toutes de la  <xref:System.Windows.Markup.MarkupExtension> classe de base.

> [!NOTE]
> Le préfixe `x:` est utilisé pour le mappage d'espace de noms XAML standard de l'espace de noms du langage XAML, dans l'élément racine d'une production XAML. Par exemple, les modèles de projet et de page Visual Studio pour différents frameworks spécifiques lancent un fichier XAML à l’aide de ce `x:` mappage. Vous pouvez choisir un autre jeton de préfixe pour votre propre mappage d'espace de noms XAML. Toutefois, dans cette documentation, le mappage `x:` par défaut est considéré comme un moyen d'identification des entités qui représentent une partie définie de l'espace de noms XAML du langage XAML, par opposition à l'espace de noms XAML par défaut d'une infrastructure spécifique ou à d'autres espaces de noms CLR ou XML arbitraires.

### <a name="xtype"></a>x:Type

`x:Type` fournit l'objet <xref:System.Type> pour le type nommé. Cette fonctionnalité est le plus souvent utilisée dans des mécanismes de différé qui utilisent le type CLR sous-jacent et la dérivation de type comme identificateur ou moniker de regroupement. Les styles et modèles WPF, ainsi que leur utilisation des propriétés `TargetType` , en sont un exemple spécifique. Pour plus d'informations, consultez [x:Type Markup Extension](xtype-markup-extension.md).

### <a name="xstatic"></a>x:Static

`x:Static` produit des valeurs statiques à partir des entités de code de type de valeur qui ne désignent pas directement le type de la valeur d'une propriété, mais qui peuvent être évaluées en ce type. Ce mécanisme s'avère utile pour la spécification de valeurs qui existent déjà en tant que constantes connues dans une définition de type. Pour plus d'informations, consultez [x:Static Markup Extension](xstatic-markup-extension.md).

### <a name="xnull"></a>x:Null

`x:Null` spécifie `null` en tant que valeur d'un membre XAML. Selon la conception de types spécifiques ou les concepts d'infrastructure à plus grande échelle, `null` n'est pas toujours la valeur par défaut d'une propriété ni la valeur implicite d'un attribut de chaîne vide. Pour plus d'informations, consultez [x:Null Markup Extension](xnull-markup-extension.md).

### <a name="xarray"></a>x:Array

`x:Array` prend en charge la création de tableaux généraux dans la syntaxe XAML dans le cas où la prise en charge des collections assurée par les éléments de base et les modèles de contrôle n'est délibérément pas utilisée. Pour plus d'informations, consultez [x:Array Markup Extension](xarray-markup-extension.md). Dans le cas de XAML 2009 en particulier, les tableaux sont accessibles en tant que primitives de langage et en tant qu'extension. Pour plus d'informations, consultez [XAML 2009 Language Features](xaml-2009-language-features.md).

### <a name="xreference"></a>x:Reference

`x:Reference` fait partie de XAML 2009, qui est une extension de l'ensemble de langages (2006) d'origine. `x:Reference` représente une référence à un autre objet existant dans un graphique d'objets. Cet objet est identifié par son `x:Name`. Pour plus d'informations, consultez [x:Reference Markup Extension](xreference-markup-extension.md).

### <a name="other-x-constructs"></a>Autres constructions x:

Il existe d'autres constructions `x:` permettant de prendre en charge des fonctionnalités de langage XAML, mais elles ne sont pas implémentées en tant qu'extensions de balisage. Pour plus d'informations, consultez [XAML Namespace (x:) Language Features](namespace-language-features.md).

## <a name="the-markupextension-base-class"></a>Classe de base MarkupExtension

Pour définir une extension de balisage personnalisée qui peut interagir avec les implémentations par défaut de lecteurs XAML et de writers XAML dans System.Xaml, vous dérivez une classe de la classe <xref:System.Windows.Markup.MarkupExtension> abstraite. Cette classe dispose d'une méthode à substituer, qui est <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Vous devrez peut-être également définir des constructeurs supplémentaires pour prendre en charge des arguments pour l'utilisation d'une extension de balisage, ainsi que les propriétés définissables correspondantes.

Via <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> , une extension de balisage personnalisée a accès à un contexte de service qui signale l’environnement dans lequel l’extension de balisage est appelée par un processeur XAML. Dans le chemin de chargement, il s’agit généralement d’un <xref:System.Xaml.XamlObjectWriter> . Dans le chemin d'enregistrement, il s'agit généralement d'un <xref:System.Xaml.XamlXmlWriter>. Chaque élément signale le contexte de service comme une classe de contexte du fournisseur de services XAML interne qui implémente un modèle de fournisseur de services. Pour plus d’informations sur les services disponibles et sur les éléments qu’ils représentent, consultez [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).

Votre classe d'extension de balisage doit utiliser un niveau d'accès public ; les processeurs XAML doivent toujours être en mesure d'instancier la classe de prise en charge de l'extension de balisage pour utiliser ses services.

## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Définition du type de prise en charge pour une extension de balisage personnalisée

Lorsque vous utilisez des services XAML .NET ou des infrastructures qui s’appuient sur les services XAML .NET, vous avez deux possibilités pour nommer le type de prise en charge de l’extension de balisage. Le nom de type se rapporte à la façon dont les writers d'objet XAML tentent d'accéder à un type de prise en charge d'extension de balisage et de l'appeler lorsqu'ils rencontrent une utilisation d'extension de balisage en XAML. Utilisez l'une des stratégies d'affectation de noms suivantes :

- Spécifiez le nom de type afin qu'il corresponde exactement au jeton d'utilisation du balisage XAML. Par exemple, pour prendre en charge l'utilisation d'une extension `{Collate ...}` , nommez le type de prise en charge `Collate`.
- Spécifiez le nom du type de façon à ce qu'il corresponde au jeton de la chaîne d'utilisation, suivi du suffixe `Extension`. Par exemple, pour prendre en charge l'utilisation d'une extension `{Collate ...}` , nommez le type de prise en charge `CollateExtension`.

L'ordre de recherche consiste à rechercher d'abord le nom de classe avec le suffixe `Extension`, puis le nom de classe sans le suffixe `Extension` .

Du point de vue de l'utilisation du balisage, le suffixe `Extension` peut tout à fait être inclus dans le cadre de l'utilisation. Toutefois, le système de comporte comme si `Extension` faisait réellement partie du nom de la classe et les writers d'objet XAML ne parviennent pas à résoudre une classe de prise en charge d'extension de balisage pour cette utilisation si cette classe ne comporte pas le suffixe `Extension` .

### <a name="the-parameterless-constructor"></a>Le constructeur sans paramètre

Pour tous les types de prise en charge d’extension de balisage, vous devez exposer un constructeur sans paramètre public. Un constructeur sans paramètre est requis pour tous les cas où un writer d’objet XAML instancie l’extension de balisage à partir d’une utilisation d’élément objet. La prise en charge de l'utilisation d'éléments objet correspond à une attente légitime concernant une extension de balisage, en particulier pour la sérialisation. Toutefois, vous pouvez implémenter une extension de balisage sans constructeur public si vous souhaitez seulement prendre en charge des utilisations d'attributs de l'extension de balisage.

Si votre utilisation d’extension de balisage n’a pas d’arguments, le constructeur sans paramètre est requis pour prendre en charge l’utilisation.

## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Modèles de constructeur et arguments de position pour une extension de balisage personnalisée

Pour une extension de balisage avec utilisation d'argument prévue, les constructeurs publics doivent correspondre aux modes de l'utilisation prévue. En d'autres termes, si votre extension de balisage est conçue pour exiger un argument de position en tant qu'utilisation valide, vous devez prendre en charge un constructeur public avec un paramètre d'entrée qui prend comme valeur l'argument de position.

Par exemple, supposons que l'extension de balisage `Collate` vise à ne prendre en charge qu'un mode dans lequel il existe un argument de position qui représente son mode, spécifié en tant que constante d'énumération `CollationMode` . Dans ce cas, un constructeur doit exister sous la forme suivante :

```csharp
public Collate(CollationMode collationMode) {...}
```

À un niveau de base, les arguments passés à une extension de balisage sont une chaîne car ils sont transférés à partir des valeurs d'attributs du balisage. Vous pouvez convertir tous vos arguments en chaînes et utiliser l'entrée à ce niveau. Toutefois, vous avez accès à un traitement qui se produit avant que les arguments d'extension de balisage ne soient passés à la classe de prise en charge.

Le traitement fonctionne de manière conceptuelle comme si l'extension de balisage était un objet à créer, puis ses valeurs de membre sont définies. Chaque propriété spécifiée à définir est évaluée de la même manière qu'un membre spécifié peut être défini sur un objet créé lorsque le code XAML est analysé. Il existe deux différences majeures :

- Comme indiqué précédemment, un type de prise en charge d’extension de balisage n’a pas besoin d’avoir un constructeur sans paramètre pour être instancié en XAML. Sa construction d'objet est différée jusqu'à ce que ses éventuels arguments dans la syntaxe de texte soient mis sous forme de jeton et évalués comme arguments de position ou nommés ; le constructeur approprié est appelé à ce moment-là.
- Les utilisations d'extensions de balisage peuvent être imbriquées. L'extension de balisage la plus profonde est évaluée en premier. Vous pouvez donc supposer une utilisation de ce type et déclarer l'un des paramètres de construction comme étant un type qui exige un convertisseur de valeurs (tel qu'une extension de balisage) à générer.

Un cas de dépendance d'un traitement de ce type se trouve dans l'exemple précédent. Le writer d’objet XAML des services XAML .NET traite les noms de constantes d’énumération en valeurs énumérées à un niveau natif.

Le traitement d'une syntaxe de texte d'un paramètre de position d'extension de balisage peut également reposer sur un convertisseur de type associé au type dans l'argument de construction.

Les arguments sont appelés « arguments de position » car l'ordre dans lequel les jetons de l'utilisation sont rencontrés correspond à l'ordre de position du paramètre de constructeur auquel ils sont assignés. Par exemple, considérez la signature de constructeur suivante :

```csharp
public Collate(CollationMode collationMode, object collateThis) {...}
```

Un processeur XAML attend deux arguments de position pour cette extension de balisage. S'il y avait une utilisation de `{Collate AlphaUp,{x:Reference circularFile}}`, le jeton `AlphaUp` est envoyé au premier paramètre et évalué en tant qu'énumération `CollationMode` nommée constante. Le résultat de la `x:Reference` interne est envoyé au deuxième paramètre et évalué en tant qu'objet.

Dans les règles spécifiées XAML concernant la syntaxe et le traitement des extensions de balisage, la virgule est le délimiteur qui sépare différents arguments, que ces arguments soient des arguments de position ou des arguments nommés.

### <a name="duplicate-arity-of-positional-arguments"></a>Arité en double des arguments positionnels

Si un writer d'objet XAML détecte l'utilisation d'une extension de balisage avec des arguments de position et que plusieurs arguments de constructeur acceptent ce nombre d'arguments (arité double), il ne s'agit pas nécessairement d'une erreur. Le comportement dépend d'un paramètre de contexte de schéma XAML personnalisable, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Si <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> a la valeur `true`, un writer d'objet XAML ne doit pas lever d'exception uniquement pour des raisons d'arité double. Le comportement au-delà de ce point n'est pas strictement défini. L'hypothèse de conception de base part du principe que le contexte de schéma comporte des informations de type disponibles pour les paramètres spécifiques et peut tenter d'effectuer des casts explicites correspondant aux candidats dupliqués pour déterminer la signature qui peut offrir la meilleure correspondance. Une exception peut tout de même être levée si aucune des signatures ne réussit les tests imposés par ce contexte de schéma particulier s'exécutant sur un writer d'objet XAML.

Par défaut, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> se trouve `false` dans le CLR <xref:System.Xaml.XamlSchemaContext> pour les services XAML .net. Par conséquent, le <xref:System.Xaml.XamlObjectWriter> par défaut lève des exceptions s'il détecte l'utilisation d'une extension de balisage pour laquelle il existe une arité double dans les constructeurs du type de stockage.

## <a name="named-arguments-for-a-custom-markup-extension"></a>Arguments nommés pour une extension de balisage personnalisée

Les extensions de balisage telles que spécifiées par XAML peuvent également utiliser une forme d'arguments nommés pour l'utilisation. Au premier niveau de la segmentation du texte en unités lexicales, la syntaxe de texte se divise en plusieurs arguments. La présence d'un signe égal (=) dans l'un des arguments identifie celui-ci comme étant un argument nommé. Un argument de ce type est également mis sous forme de jeton dans une paire nom/valeur. Dans ce cas, le nom nomme une propriété définissable publique du type de prise en charge de l'extension de balisage. Si vous avez l'intention de prendre en charge l'utilisation d'arguments nommés, vous devez fournir ces propriétés définissables publiques. Les propriétés peuvent être des propriétés héritées, à condition qu'elles restent publiques.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Accès au contexte de fournisseur de services à partir d'une implémentation de l'extension du balisage

Les services disponibles sont les mêmes pour tous les convertisseurs de valeurs. La seule différence réside dans le mode de réception du contexte de service par chaque convertisseur de valeurs. L’accès aux services et les services disponibles sont documentés dans la rubrique [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).

## <a name="property-element-usage-of-a-markup-extension"></a>Utilisation des éléments de propriété d’une extension de balisage

Les scénarios d'utilisation d'une extension de balisage consistent souvent à employer cette extension dans le cadre de l'utilisation d'attributs. Toutefois, il est également possible de définir la classe de stockage pour prend en charge l'utilisation des éléments de propriété.

Pour prendre en charge l’utilisation des éléments de propriété de votre extension de balisage, définissez un constructeur sans paramètre public. Il doit s'agir d'un constructeur d'instance, et non pas d'un constructeur statique. Cela est nécessaire car un processeur XAML doit généralement appeler le constructeur sans paramètre sur tout élément objet qu’il traite à partir du balisage, et cela comprend les classes d’extension de balisage en tant qu’éléments objet. Pour les scénarios avancés, vous pouvez définir des chemins de construction autres que ceux par défaut pour les classes. (Pour plus d’informations, consultez [directive x :FactoryMethod](xfactorymethod-directive.md).) Toutefois, vous ne devez pas utiliser ces modèles à des fins d’extension de balisage, car cela rend la découverte du modèle d’utilisation bien plus difficile, à la fois pour les concepteurs et pour les utilisateurs de balisage brut.

## <a name="attributing-for-a-custom-markup-extension"></a>Attribution d’une extension de balisage personnalisée

Pour prendre en charge des environnements de conception et certains scénarios de writer d'objet XAML, vous devez associer plusieurs attributs CLR à votre type de prise en charge d'extension de balisage. Ces attributs signalent l'utilisation prévue pour une extension de balisage.

 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> signale les informations <xref:System.Type> pour le type d'objet que <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> retourne. Par sa simple signature <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> retourne <xref:System.Object>. Toutefois, divers consommateurs peuvent souhaiter obtenir des informations de type de retour plus précises. notamment :

- des concepteurs et IDE qui peuvent être en mesure de fournir une prise en charge tenant compte du type pour les utilisations d'extensions de balisage ;
- des implémentations avancées de gestionnaires `SetMarkupExtension` sur les classes cibles, qui peuvent faire appel à la réflexion pour déterminer le type de retour d'une extension de balisage au lieu de se brancher sur des implémentations <xref:System.Windows.Markup.MarkupExtension> connues spécifiques via leur nom.

## <a name="serialization-of-markup-extension-usages"></a>Sérialisation des utilisations d’extensions de balisage

Lorsqu'un writer d'objet XAML traite une utilisation d'extension de balisage et appelle <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, son contexte, ayant déjà été une utilisation d'extension de balisage, persiste dans le flux de nœud XAML, et non dans le graphique d'objets. Dans le graphique d'objets, seule la valeur est conservée. Si vous disposez de scénarios de conception ou d'autres raisons de rendre persistante l'utilisation d'extension de balisage d'origine dans la sortie sérialisée, vous devez concevoir votre propre infrastructure permettant d'assurer le suivi des utilisations d'extensions de balisage à partir du flux de nœud XAML du chemin de chargement. Vous pouvez implémenter un comportement visant à recréer les éléments du flux de nœud à partir du chemin de chargement et à les lire sur des writers XAML pour la sérialisation dans le chemin d'enregistrement, substituant ainsi la valeur dans la position appropriée du flux de nœud.

## <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensions de balisage dans le flux de nœud XAML

Si vous travaillez avec un flux de nœud XAML dans le chemin de chargement, l'utilisation d'une extension de balisage est représentée dans le flux de nœud sous la forme d'un objet.

Si l'utilisation d'une extension de balisage fait appel à des arguments de position, elle est représentée sous la forme d'un objet de début avec une valeur d'initialisation. Selon une représentation textuelle approximative, le flux de nœud a l'apparence suivante :

`StartObject` (<xref:System.Xaml.XamlType> est le type de définition de l'extension de balisage, et non pas son type de retour)

`StartMember` (le nom de <xref:System.Xaml.XamlMember> est `_InitializationText`)

`Value` (la valeur correspond aux arguments de position spécifiés sous forme de chaîne, y compris les délimiteurs intermédiaires)

`EndMember`

`EndObject`

L'utilisation d'une extension de balisage avec des arguments nommés est représentée sous la forme d'un objet dont les membres ont les noms appropriés, chacun étant défini avec des valeurs de chaîne de texte.

L'appel réel de l'implémentation de `ProvideValue` d'une extension de balisage requiert le contexte de schéma XAML, car cette opération nécessite un mappage de type et la création d'une instance de type de prise en charge d'extension de balisage. C’est l’une des raisons pour lesquelles les utilisations d’extensions de balisage sont conservées de cette façon dans les flux de nœud des services XAML .NET par défaut : la partie lecteur d’un chemin de chargement ne dispose souvent pas du contexte de schéma XAML nécessaire.

Si vous travaillez avec un flux de nœud XAML dans le chemin d'enregistrement, la représentation du graphique d'objets ne contient généralement aucun élément pouvant vous indiquer que l'objet à sérialiser a été initialement fourni par une utilisation d'extension de balisage et un résultat `ProvideValue` . Les scénarios qui doivent rendre persistantes les utilisations des extensions de balisage pour les allers-retours tout en capturant d'autres modifications dans le graphique d'objets requièrent la conception de techniques spécifiques pour conserver les informations d'utilisation des extensions de balisage de l'entrée XAML d'origine. Par exemple, pour restaurer les utilisations d'extensions de balisage, vous devrez peut-être travailler avec le flux de nœud dans le chemin d'enregistrement ou effectuer un certain type de fusion entre le code XAML d'origine et le code XAML faisant l'objet d'allers-retours. Certaines infrastructures d'implémentation en XAML telles que WPF utilisent des types intermédiaires (expressions) pour faciliter la représentation des cas où les utilisations d'extensions de balisage ont fourni les valeurs.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Markup.MarkupExtension>
- [Convertisseurs de types et extensions de balisage pour XAML](type-converters-and-markup-extensions.md)
- [Extensions de balisage et XAML WPF](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
