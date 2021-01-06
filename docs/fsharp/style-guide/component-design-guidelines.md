---
title: Indications de conception de composants F#
description: 'Découvrez les instructions relatives à l’écriture de composants F # destinés à être consommés par d’autres appelants.'
ms.date: 05/14/2018
ms.openlocfilehash: 24be2a422c97b9334f749e3d9dfcccd0feec219b
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856105"
---
# <a name="f-component-design-guidelines"></a>Indications de conception de composants F#

Ce document est un ensemble d’instructions de conception de composants pour la programmation F #, basée sur les instructions de conception de composant F #, v14, Microsoft Research et une version qui a été organisée et gérée à l’origine par la Fondation de logiciel F #.

Ce document suppose que vous êtes familiarisé avec la programmation F #. Un grand Merci à la communauté F # pour leurs contributions et des commentaires utiles sur les différentes versions de ce guide.

## <a name="overview"></a>Vue d’ensemble

Ce document examine certains des problèmes liés à la conception et au codage des composants F #. Un composant peut désigner l’un des éléments suivants :

* Couche dans votre projet F # qui a des consommateurs externes dans ce projet.
* Bibliothèque destinée à être consommée par du code F # dans les limites d’assembly.
* Bibliothèque destinée à être consommée par n’importe quel langage .NET au-delà des limites de l’assembly.
* Bibliothèque destinée à être distribuée via un référentiel de packages, tel que [NuGet](https://nuget.org).

Les techniques décrites dans cet article suivent les [cinq principes du bon code F #](index.md#five-principles-of-good-f-code)et, par conséquent, utilisent à la fois la programmation fonctionnelle et la programmation d’objets, le cas échéant.

Quelle que soit la méthodologie, le concepteur de composants et de bibliothèques rencontre un certain nombre de problèmes pratiques et prosaic quand il tente de concevoir une API qui est plus facilement utilisable par les développeurs. L’application conscientious des [instructions de conception de la bibliothèque .net](../../standard/design-guidelines/index.md) vous dirigera vers la création d’un ensemble cohérent d’API qui sont agréables à consommer.

## <a name="general-guidelines"></a>Recommandations générales

Il existe quelques recommandations universelles qui s’appliquent aux bibliothèques F #, quel que soit le public visé pour la bibliothèque.

### <a name="learn-the-net-library-design-guidelines"></a>Découvrez les instructions de conception de la bibliothèque .NET

Quel que soit le type de code F # que vous utilisez, il est utile d’avoir une connaissance pratique des [instructions de conception de la bibliothèque .net](../../standard/design-guidelines/index.md). La plupart des autres programmeurs F # et .NET sont familiarisés avec ces instructions et s’attendent à ce que le code .NET soit conforme.

Les instructions de conception de la bibliothèque .NET fournissent des indications générales sur l’affectation de noms, la conception des classes et des interfaces, la conception des membres (propriétés, méthodes, événements, etc.) et bien plus encore, et constituent un premier point de référence utile pour un large éventail de conseils en matière de conception.

### <a name="add-xml-documentation-comments-to-your-code"></a>Ajouter des commentaires de documentation XML à votre code

La documentation XML sur les API publiques permet de s’assurer que les utilisateurs peuvent obtenir des fonctionnalités IntelliSense et d’info-and Express exceptionnelles lors de l’utilisation de ces types et membres, et activer la génération de fichiers de documentation pour la bibliothèque. Consultez la [documentation XML](../language-reference/xml-documentation.md) sur les différentes balises XML qui peuvent être utilisées pour le balisage supplémentaire dans les commentaires xmlDoc par l’employé.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

Vous pouvez utiliser les commentaires XML de forme abrégée ( `/// comment` ) ou les commentaires XML standard ( `///<summary>comment</summary>` ).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Envisagez d’utiliser des fichiers de signature explicites (. FSI) pour les API de bibliothèque et de composant stables

L’utilisation de fichiers de signatures explicites dans une bibliothèque F # fournit un résumé succinct de l’API publique, qui vous permet de vous assurer que vous connaissez la surface publique complète de votre bibliothèque et fournit une séparation nette entre la documentation publique et les détails de l’implémentation interne. Les fichiers de signature ajoutent un frottement à la modification de l’API publique, en exigeant que les modifications soient apportées à la fois dans les fichiers d’implémentation et de signature. Par conséquent, les fichiers de signature ne doivent généralement être introduits que lorsqu’une API est devenue solidifiée et n’est plus censée changer de manière significative.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Suivre toujours les meilleures pratiques pour l’utilisation de chaînes dans .NET

Suivez [les meilleures pratiques pour l’utilisation de chaînes dans l’aide de .net](../../standard/base-types/best-practices-strings.md) . En particulier, indiquez toujours explicitement l' *intention culturelle* dans la conversion et la comparaison des chaînes (le cas échéant).

## <a name="guidelines-for-f-facing-libraries"></a>Instructions pour les bibliothèques en F #

Cette section présente les recommandations pour le développement de bibliothèques F # publiques. autrement dit, les bibliothèques exposent des API publiques qui sont destinées à être consommées par les développeurs F #. Il existe une variété de recommandations de conception de bibliothèque applicables spécifiquement à F #. En l’absence des recommandations spécifiques qui suivent, les règles de conception de la bibliothèque .NET sont des conseils de secours.

### <a name="naming-conventions"></a>Conventions d’affectation de noms

#### <a name="use-net-naming-and-capitalization-conventions"></a>Utiliser les conventions de nommage et de mise en majuscules de .NET

Le tableau suivant suit les conventions de nommage et de mise en majuscules de .NET. Il y a de petites additions pour inclure également des constructions F #.

| Construction | Cas | Élément | Exemples | Notes |
|-----------|------|------|----------|-------|
| Types concrets | Casse Pascal | Substantif/adjectif | Liste, double, complexe | Les types concrets sont les structs, les classes, les énumérations, les délégués, les enregistrements et les unions. Bien que les noms de types soient généralement en minuscules dans OCaml, F # a adopté le schéma de nommage .NET pour les types.
| DLL           | Casse Pascal |                 | Fabrikam.Core.dll |  |
| Étiquettes d’Union     | Casse Pascal | Nom | Some, ajouter, réussite | N’utilisez pas de préfixe dans les API publiques. Si vous le souhaitez, vous pouvez utiliser un préfixe en interne, par exemple `type Teams = TAlpha | TBeta | TDelta.` |
| Événement          | Casse Pascal | Verbe | ValueChanged/ValueChanging |  |
| Exceptions     | Casse Pascal |      | WebException | Le nom doit se terminer par « exception ». |
| Champ          | Casse Pascal | Nom | CurrentName  | |
| Types interface |  Casse Pascal | Substantif/adjectif | IDisposable | Le nom doit commencer par « I ». |
| Méthode |  Casse Pascal |  Verbe | ToString | |
| Espace de noms | Casse Pascal | | Microsoft. FSharp. Core | Utilisez généralement `<Organization>.<Technology>[.<Subnamespace>]` , bien que supprimer l’organisation si la technologie est indépendante de l’organisation. |
| Paramètres | La casse mixte | Nom |  typeName, Transform, plage | |
| valeurs Let (Internal) | La casse mixte ou casse Pascal | Substantif/verbe |  getValue, myTable |
| valeurs Let (externe) | La casse mixte ou casse Pascal | Substantif/verbe  | List. map, dates. Today | les valeurs à liaison limitée sont souvent publiques lorsque vous suivez les modèles de conception fonctionnelle traditionnels. Toutefois, utilisez généralement casse Pascal quand l’identificateur peut être utilisé à partir d’autres langages .NET. |
| Propriété  | Casse Pascal  | Substantif/adjectif  | IsEndOfFile, BackColor  | Les propriétés booléennes utilisent généralement et peuvent et doivent être positives, comme dans IsEndOfFile, et non IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Éviter les abréviations

Les instructions .NET découragent l’utilisation des abréviations (par exemple, « utiliser `OnButtonClick` plutôt que `OnBtnClick` »). Les abréviations courantes, telles que `Async` pour « asynchrone », sont tolérées. Cette instruction est parfois ignorée pour la programmation fonctionnelle. par exemple, `List.iter` utilise une abréviation pour « Iterate ». Pour cette raison, l’utilisation d’abréviations tend à être tolérée à un degré supérieur dans la programmation F # en F #, mais doit toujours être évitée dans la conception du composant public.

#### <a name="avoid-casing-name-collisions"></a>Éviter les collisions de nom de casse

Les instructions .NET indiquent que la casse seule ne peut pas être utilisée pour lever l’ambiguïté des collisions de noms, car certaines langues clientes (par exemple, Visual Basic) ne respectent pas la casse.

#### <a name="use-acronyms-where-appropriate"></a>Utiliser des acronymes quand cela est approprié

Les acronymes tels que XML ne sont pas des abréviations et sont largement utilisés dans les bibliothèques .NET dans une forme non capitalisée (XML). Seuls les acronymes bien connus et largement reconnus doivent être utilisés.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Utiliser casse Pascal pour les noms de paramètres génériques

Utilisez casse Pascal pour les noms de paramètres génériques dans les API publiques, y compris pour les bibliothèques en F #. En particulier, utilisez des noms comme `T` , `U` , `T1` , `T2` pour les paramètres génériques arbitraires, et quand des noms spécifiques sont significatifs, alors pour les bibliothèques en F #, utilisez des noms comme `Key` , `Value` , `Arg` (mais pas par exemple `TKey` ).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Utilisez casse Pascal ou la casse mixte pour les fonctions et valeurs publiques dans les modules F #

La casse mixte est utilisé pour les fonctions publiques qui sont conçues pour être utilisées non qualifiées (par exemple, `invalidArg` ) et pour les « fonctions de collection standard » (par exemple, List. Map). Dans ces deux cas, les noms de fonctions agissent comme des mots clés dans le langage.

### <a name="object-type-and-module-design"></a>Conception d’un objet, d’un type et d’un module

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Utiliser des espaces de noms ou des modules pour contenir vos types et modules

Chaque fichier F # dans un composant doit commencer par une déclaration d’espace de noms ou une déclaration de module.

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

or

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

Les différences entre l’utilisation de modules et d’espaces de noms pour organiser le code au niveau supérieur sont les suivantes :

* Les espaces de noms peuvent s’étendre sur plusieurs fichiers
* Les espaces de noms ne peuvent pas contenir de fonctions F #, sauf s’ils se trouvent dans un module interne
* Le code d’un module donné doit être contenu dans un seul fichier
* Les modules de niveau supérieur peuvent contenir des fonctions F # sans nécessiter de module interne

Le choix entre un espace de noms ou un module de niveau supérieur affecte la forme compilée du code et, par conséquent, affecte la vue d’autres langages .NET si votre API est finalement consommée en dehors du code F #.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Utiliser des méthodes et des propriétés pour des opérations intrinsèques à des types d’objet

Lorsque vous utilisez des objets, il est préférable de s’assurer que les fonctionnalités consommables sont implémentées en tant que méthodes et propriétés sur ce type.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

La majeure partie des fonctionnalités d’un membre donné ne doit pas nécessairement être implémentée dans ce membre, mais l’élément consommable de cette fonctionnalité doit être.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Utiliser des classes pour encapsuler un État mutable

En F #, cette opération ne doit être effectuée que si cet État n’est pas déjà encapsulé par une autre construction de langage, telle qu’une fermeture, une expression de séquence ou un calcul asynchrone.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Utiliser des interfaces pour regrouper des opérations connexes

Utilisez les types d’interface pour représenter un ensemble d’opérations. Cela est préférable à d’autres options, telles que des tuples de fonctions ou des enregistrements de fonctions.

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

Dans la préférence :

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

Les interfaces sont des concepts de première classe dans .NET, que vous pouvez utiliser pour obtenir ce que les functors vous procurent normalement. En outre, ils peuvent être utilisés pour encoder les types existentiel dans votre programme, ce qui ne peut pas être le signe des fonctions.

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a>Utiliser un module pour regrouper les fonctions qui agissent sur les collections

Lorsque vous définissez un type de collection, envisagez de fournir un ensemble standard d’opérations comme `CollectionType.map` et `CollectionType.iter` ) pour les nouveaux types de collections.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Si vous incluez un tel module, suivez les conventions d’affectation de noms standard pour les fonctions qui se trouvent dans FSharp. Core.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Utilisez un module pour regrouper des fonctions pour les fonctions canoniques courantes, en particulier dans les bibliothèques mathématiques et DSL

Par exemple, `Microsoft.FSharp.Core.Operators` est une collection ouverte automatiquement de fonctions de niveau supérieur (comme `abs` et `sin` ) fournies par FSharp.Core.dll.

De même, une bibliothèque de statistiques peut inclure un module avec des fonctions `erf` et `erfc` , où ce module est conçu pour être ouvert de manière explicite ou automatique.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Envisagez d’utiliser RequireQualifiedAccess et d’appliquer avec précaution les attributs AutoOpen

L’ajout `[<RequireQualifiedAccess>]` de l’attribut à un module indique que le module ne peut pas être ouvert et que les références aux éléments du module requièrent un accès qualifié explicite. Par exemple, le `Microsoft.FSharp.Collections.List` module a cet attribut.

Cela est utile lorsque les fonctions et valeurs du module ont des noms qui sont susceptibles d’entrer en conflit avec des noms dans d’autres modules. La nécessité d’un accès qualifié peut augmenter la maintenabilité à long terme et la évolutivité d’une bibliothèque.

L’ajout `[<AutoOpen>]` de l’attribut à un module signifie que le module s’ouvre lorsque l’espace de noms conteneur est ouvert. L' `[<AutoOpen>]` attribut peut également être appliqué à un assembly pour indiquer un module qui s’ouvre automatiquement lorsque l’assembly est référencé.

Par exemple, une bibliothèque de statistiques **MathsHeaven. Statistics** peut contenir des `module MathsHeaven.Statistics.Operators` fonctions contenantes `erf` et `erfc` . Il est raisonnable de marquer ce module comme `[<AutoOpen>]` . Cela `open MathsHeaven.Statistics` permet également d’ouvrir ce module et de placer les noms `erf` et l' `erfc` étendue. Une autre bonne utilisation de `[<AutoOpen>]` est pour les modules contenant des méthodes d’extension.

`[<AutoOpen>]`La surutilisation des déclencheurs à des espaces de noms pollués, et l’attribut doit être utilisé avec précaution. Pour des bibliothèques spécifiques dans des domaines spécifiques, l’utilisation judicieuse de `[<AutoOpen>]` peut aboutir à une meilleure convivialité.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Envisagez de définir des membres d’opérateur sur des classes pour lesquelles l’utilisation d’opérateurs connus est appropriée

Parfois, les classes sont utilisées pour modéliser des constructions mathématiques telles que des vecteurs. Lorsque le domaine modélisé a des opérateurs connus, il est utile de les définir en tant que membres intrinsèques à la classe.

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Ce guide correspond aux instructions .NET générales pour ces types. Toutefois, il peut également être important dans le codage F #, car cela permet d’utiliser ces types conjointement avec les fonctions et les méthodes F # avec des contraintes de membre, telles que List. sumBy.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Envisagez d’utiliser CompiledName pour fournir un. Nom convivial NET pour les autres consommateurs de langage .NET

Parfois, vous souhaiterez peut-être nommer un élément dans un style pour les consommateurs F # (par exemple, un membre statique en minuscules afin qu’il apparaisse comme s’il s’agissait d’une fonction liée à un module), mais avec un style différent pour le nom lorsqu’il est compilé dans un assembly. Vous pouvez utiliser l' `[<CompiledName>]` attribut pour fournir un style différent pour le code non F # consommant l’assembly.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

À l’aide de `[<CompiledName>]` , vous pouvez utiliser des conventions d’affectation de noms .net pour les consommateurs non F # de l’assembly.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Utilisez la surcharge de méthode pour les fonctions membres, si cela fournit une API plus simple

La surcharge de méthode est un outil puissant pour simplifier une API qui peut avoir besoin d’effectuer des fonctionnalités similaires, mais avec des options ou des arguments différents.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

En F #, il est plus courant de surcharger le nombre d’arguments que les types d’arguments.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Masquer les représentations des types d’enregistrement et d’Union si la conception de ces types est susceptible d’évoluer

Évitez de révéler des représentations concrètes d’objets. Par exemple, la représentation concrète des <xref:System.DateTime> valeurs n’est pas révélée par l’API externe publique de la conception de la bibliothèque .net. Au moment de l’exécution, le Common Language Runtime connaît l’implémentation validée qui sera utilisée tout au long de l’exécution. Toutefois, le code compilé ne récupère pas lui-même les dépendances sur la représentation concrète.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Éviter l’utilisation de l’héritage d’implémentation pour l’extensibilité

En F #, l’héritage d’implémentation est rarement utilisé. En outre, les hiérarchies d’héritage sont souvent complexes et difficiles à modifier lorsque de nouvelles exigences arrivent. L’implémentation de l’héritage existe toujours en F # à des fins de compatibilité et de rares cas où il s’agit de la meilleure solution à un problème, mais d’autres techniques doivent être recherchées dans vos programmes F # lors de la conception du polymorphisme, comme l’implémentation de l’interface.

### <a name="function-and-member-signatures"></a>Signatures des fonctions et des membres

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Utiliser des tuples pour les valeurs de retour lors du retour d’un petit nombre de valeurs non liées multiples

Voici un bon exemple d’utilisation d’un tuple dans un type de retour :

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

Pour les types de retour contenant de nombreux composants, ou où les composants sont associés à une seule entité identifiable, envisagez d’utiliser un type nommé au lieu d’un tuple.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Utilisation `Async<T>` pour la programmation asynchrone aux limites de l’API F #

S’il existe une opération synchrone correspondante nommée `Operation` qui retourne un `T` , alors l’opération asynchrone doit être nommée `AsyncOperation` si elle retourne `Async<T>` ou `OperationAsync` si elle retourne `Task<T>` . Pour les types .NET couramment utilisés qui exposent des méthodes Begin/End, envisagez `Async.FromBeginEnd` d’utiliser pour écrire des méthodes d’extension en tant que façade pour fournir le modèle de programmation F # Async à ces API .net.

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Exceptions

Consultez [gestion des erreurs](conventions.md#error-management) pour en savoir plus sur l’utilisation appropriée des exceptions, des résultats et des options.

### <a name="extension-members"></a>Membres d’extension

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Appliquez avec soin les membres d’extension F # dans les composants F #-to-F #

En général, les membres d’extension F # doivent être utilisés uniquement pour les opérations qui se trouvent dans la fermeture des opérations intrinsèques associées à un type dans la majorité de ses modes d’utilisation. Une utilisation courante consiste à fournir des API qui sont plus idiomatique à F # pour divers types .NET :

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>Types d’Union

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Utiliser des unions discriminées plutôt que des hiérarchies de classes pour les données structurées en arborescence

Les structures de type arborescence sont définies de manière récursive. Cela est délicat avec l’héritage, mais élégant avec des unions discriminées.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Le fait de représenter des données d’arborescence avec des unions discriminées vous permet également de tirer parti de l’exhaustivité dans les critères spéciaux.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Utilisez `[<RequireQualifiedAccess>]` sur les types d’Union dont les noms de cas ne sont pas suffisamment uniques

Vous pouvez vous trouver dans un domaine où le même nom est le meilleur nom pour différents éléments, tels que les cas d’union discriminée. Vous pouvez utiliser `[<RequireQualifiedAccess>]` pour lever l’ambiguïté des noms de cas afin d’éviter de déclencher des erreurs confuses en raison de l’occultation en fonction de l’ordre des `open` instructions.

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Masquer les représentations des unions discriminées pour les API compatibles binaires si la conception de ces types est susceptible d’évoluer

Les types unions reposent sur les formulaires de critères spéciaux F # pour un modèle de programmation succinct. Comme mentionné précédemment, vous devez éviter de révéler des représentations de données concrètes si la conception de ces types est susceptible d’évoluer.

Par exemple, la représentation d’une union discriminée peut être masquée à l’aide d’une déclaration privée ou interne, ou à l’aide d’un fichier de signature.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Si vous révélez des unions discriminées de façon non discriminatoire, il peut s’avérer difficile de créer une version de votre bibliothèque sans rompre le code utilisateur. Au lieu de cela, envisagez de révéler un ou plusieurs modèles actifs afin d’autoriser les critères spéciaux sur les valeurs de votre type.

Les modèles actifs fournissent un autre moyen de fournir aux consommateurs F # des critères spéciaux tout en évitant d’exposer directement les types d’Union F #.

### <a name="inline-functions-and-member-constraints"></a>Fonctions inline et contraintes de membre

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Définir des algorithmes numériques génériques à l’aide de fonctions inline avec des contraintes de membre implicites et des types génériques résolus statiquement

Les contraintes de membre arithmétiques et les contraintes de comparaison F # sont une norme pour la programmation F #. Considérons par exemple le code suivant :

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

Le type de cette fonction est le suivant :

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Il s’agit d’une fonction appropriée pour une API publique dans une bibliothèque mathématique.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Évitez d’utiliser des contraintes de membre pour simuler des classes de type et des types de canard

Il est possible de simuler un « typage de canard » à l’aide de contraintes de membre F #. Toutefois, les membres qui l’utilisent ne doivent pas en général être utilisés dans les conceptions de bibliothèque F # vers F #. Cela est dû au fait que les conceptions de bibliothèques basées sur des contraintes implicites inconnues ou non standard ont tendance à amener le code utilisateur à devenir rigide et à être lié à un modèle d’infrastructure particulier.

En outre, il y a de fortes chances pour que l’utilisation intensive de contraintes de membre de cette manière puisse entraîner des temps de compilation très longs.

### <a name="operator-definitions"></a>Définitions d’opérateur

#### <a name="avoid-defining-custom-symbolic-operators"></a>Évitez de définir des opérateurs symboliques personnalisés

Les opérateurs personnalisés sont essentiels dans certaines situations et sont des appareils notations très utiles dans un grand corps de code d’implémentation. Pour les nouveaux utilisateurs d’une bibliothèque, les fonctions nommées sont souvent plus faciles à utiliser. En outre, les opérateurs symboliques personnalisés peuvent être difficiles à documenter et les utilisateurs trouvent qu’il est plus difficile de rechercher de l’aide sur les opérateurs, en raison des limitations existantes de l’IDE et des moteurs de recherche.

Par conséquent, il est préférable de publier vos fonctionnalités en tant que fonctions et membres nommés, et d’exposer en outre des opérateurs pour cette fonctionnalité uniquement si les avantages en notation compensent la documentation et le coût cognitif de leur utilisation.

### <a name="units-of-measure"></a>Unités de mesure

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Utiliser avec soin les unités de mesure pour la sécurité de type ajoutée dans le code F #

Les informations de saisie supplémentaires pour les unités de mesure sont effacées lorsqu’elles sont affichées par d’autres langages .NET. N’oubliez pas que les composants, les outils et la réflexion .NET voient les types-sans unités. Par exemple, les consommateurs C# verront `float` plutôt que `float<kg>` .

### <a name="type-abbreviations"></a>Abréviations de types

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Utilisez avec soin les abréviations de type pour simplifier le code F #

Les composants, les outils et la réflexion .NET ne voient pas les noms abrégés pour les types. Une utilisation significative des abréviations de type peut également rendre un domaine plus complexe qu’il ne l’est, ce qui peut dérouter les consommateurs.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Évitez les abréviations de type pour les types publics dont les membres et les propriétés doivent être intrinsèquement différents de ceux disponibles sur le type en cours d’abréviation

Dans ce cas, le type en cours d’abréviation révèle trop d’informations sur la représentation du type réel en cours de définition. Envisagez plutôt d’encapsuler l’abréviation dans un type de classe ou une union discriminée à cas unique (ou, lorsque les performances sont essentielles, envisagez d’utiliser un type struct pour encapsuler l’abréviation).

Par exemple, il est tentant de définir un mappage multiple comme un cas spécial d’une carte F #, par exemple :

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Toutefois, les opérations logiques de pointage sur ce type ne sont pas les mêmes que les opérations sur une carte, par exemple, il est raisonnable que le mappage d’opérateur de recherche. [clé] retourne la liste vide si la clé n’est pas dans le dictionnaire, au lieu de lever une exception.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Instructions pour les bibliothèques à utiliser à partir d’autres langages .NET

Lorsque vous concevez des bibliothèques à utiliser à partir d’autres langages .NET, il est important de respecter les règles de conception de la [bibliothèque .net](../../standard/design-guidelines/index.md). Dans ce document, ces bibliothèques sont étiquetées en tant que bibliothèques .NET vanille, par opposition aux bibliothèques F # qui utilisent des constructions F # sans restriction. La conception de bibliothèques .NET vanille signifie que les API familières et idiomatique sont cohérentes avec le reste du .NET Framework en minimisant l’utilisation des constructions spécifiques à F # dans l’API publique. Les règles sont décrites dans les sections suivantes.

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Conception de l’espace de noms et du type (pour les bibliothèques à utiliser à partir d’autres langages .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Appliquer les conventions d’affectation de noms .NET à l’API publique de vos composants

Portez une attention particulière à l’utilisation des noms abrégés et des recommandations en matière de mise en majuscules .NET.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Utilisez les espaces de noms, les types et les membres comme structure d’organisation principale de vos composants

Tous les fichiers contenant des fonctionnalités publiques doivent commencer par une `namespace` déclaration, et les seules entités publiques dans les espaces de noms doivent être des types. N’utilisez pas de modules F #.

Utilisez des modules non publics pour stocker le code d’implémentation, les types d’utilitaire et les fonctions utilitaires.

Les types statiques doivent être préférés aux modules, car ils permettent une évolution future de l’API afin d’utiliser la surcharge et d’autres concepts de conception de l’API .NET qui ne peuvent pas être utilisés dans les modules F #.

Par exemple, à la place de l’API publique suivante :

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

À la place :

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Utilisez les types d’enregistrements F # dans les API .NET vanille Si la conception des types ne évoluera pas

Les types d’enregistrements F # sont compilés en une classe .NET simple. Celles-ci conviennent pour certains types simples et stables dans les API. Envisagez `[<NoEquality>]` d’utiliser les `[<NoComparison>]` attributs et pour supprimer la génération automatique des interfaces. Évitez également d’utiliser des champs d’enregistrement mutables dans des API .NET vanille, car celles-ci exposent un champ public. Déterminez toujours si une classe fournirait une option plus flexible pour l’évolution future de l’API.

Par exemple, le code F # suivant expose l’API publique à un consommateur C# :

F# :

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

C# :

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Masquer la représentation des types d’Union F # dans les API .NET vanille

Les types d’Union f # ne sont généralement pas utilisés dans les limites d’un composant, même pour le codage F # en F #. Ils constituent un excellent dispositif d’implémentation lorsqu’ils sont utilisés en interne dans les composants et les bibliothèques.

Lors de la conception d’une API .NET vanille, pensez à masquer la représentation d’un type d’Union à l’aide d’une déclaration privée ou d’un fichier de signature.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Vous pouvez également augmenter les types qui utilisent une représentation d’Union en interne avec des membres pour fournir un souhaité. API .net.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Concevoir une interface utilisateur graphique et d’autres composants à l’aide des modèles de conception de l’infrastructure

Il existe de nombreuses infrastructures différentes disponibles dans .NET, comme WinForms, WPF et ASP.NET. Les conventions de nommage et de conception de chaque doivent être utilisées si vous concevez des composants à utiliser dans ces infrastructures. Par exemple, pour la programmation WPF, adoptez des modèles de conception WPF pour les classes que vous concevez. Pour les modèles dans la programmation de l’interface utilisateur, utilisez des modèles de conception tels que les événements et les collections basées sur les notifications, tels que ceux qui se trouvent dans <xref:System.Collections.ObjectModel> .

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Conception d’objets et de membres (pour les bibliothèques à utiliser à partir d’autres langages .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Utiliser l’attribut CLIEvent pour exposer des événements .NET

Construit un `DelegateEvent` avec un type délégué .net spécifique qui prend un objet et `EventArgs` (plutôt qu’un `Event` , qui utilise simplement le `FSharpHandler` type par défaut) afin que les événements soient publiés de la manière familière vers d’autres langages .net.

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a>Exposer des opérations asynchrones en tant que méthodes qui retournent des tâches .NET

Les tâches sont utilisées dans .NET pour représenter des calculs asynchrones actifs. Les tâches sont en général moins compositionnels que `Async<T>` les objets F #, car elles représentent des tâches « déjà en cours d’exécution » et ne peuvent pas être composées de la même façon que pour effectuer une composition parallèle, ou qui masquent la propagation des signaux d’annulation et d’autres paramètres contextuels.

Toutefois, malgré cela, les méthodes qui retournent des tâches sont la représentation standard de la programmation asynchrone sur .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Vous souhaiterez souvent également accepter un jeton d’annulation explicite :

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Utiliser les types délégués .NET au lieu des types de fonctions F #

Ici « types de fonction F # » sont des types « flèche » comme `int -> int` .

Au lieu de :

```fsharp
member this.Transform(f: int->int) =
    ...
```

Procédez comme suit :

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

Le type de fonction F # apparaît comme `class FSharpFunc<T,U>` pour d’autres langages .net et est moins adapté aux fonctionnalités de langage et aux outils qui comprennent les types délégués. Lors de la création d’une méthode d’ordre supérieur ciblant .NET Framework 3,5 ou une version ultérieure, les `System.Func` `System.Action` délégués et sont les API appropriées à publier pour permettre aux développeurs .net d’utiliser ces API à des fins de faible frottement. (Lorsque vous ciblez .NET Framework 2,0, les types délégués définis par le système sont plus limités ; envisagez d’utiliser des types délégués prédéfinis tels que `System.Converter<T,U>` ou définissant un type délégué spécifique.)

À l’inverse, les délégués .NET ne sont pas naturels pour les bibliothèques F # (consultez la section suivante sur les bibliothèques en F #). Par conséquent, une stratégie d’implémentation courante lors du développement de méthodes d’ordre supérieur pour des bibliothèques .NET vanille consiste à créer toute l’implémentation à l’aide de types de fonction F #, puis à créer l’API publique à l’aide de délégués comme une façade fine au-dessus de l’implémentation réelle de F #.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Utilisez le modèle TryGetValue au lieu de retourner des valeurs d’option F #, et préférer la surcharge de méthode pour prendre des valeurs d’option F # comme arguments

Les modèles courants d’utilisation pour le type d’option F # dans les API sont mieux implémentés dans les API .NET vanille à l’aide des techniques de conception .NET standard. Au lieu de retourner une valeur d’option F #, envisagez d’utiliser le type de retour bool plus un paramètre out comme dans le modèle « TryGetValue ». Et au lieu de prendre des valeurs d’option F # comme paramètres, envisagez d’utiliser la surcharge de méthode ou des arguments facultatifs.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Utiliser les types d’interfaces de collection .NET IEnumerable \<T\> et IDictionary \<Key,Value\> pour les paramètres et les valeurs de retour

Évitez l’utilisation de types de collections concrets tels que les tableaux .NET `T[]` , les types F # `list<T>` , `Map<Key,Value>` et `Set<T>` , ainsi que les types de collections concrètes .NET tels que `Dictionary<Key,Value>` . Les règles de conception de la bibliothèque .NET ont de bons conseils quant à l’utilisation de différents types de collections comme `IEnumerable<T>` . Certaines utilisation de tableaux ( `T[]` ) sont acceptables dans certains cas, pour des raisons de performances. Notez surtout qu’il `seq<T>` s’agit simplement de l’alias F # pour `IEnumerable<T>` , et donc seq est souvent un type approprié pour une API .net vanille.

Au lieu de listes F # :

```fsharp
member this.PrintNames(names: string list) =
    ...
```

Utilisez des séquences F # :

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Utilisez le type d’unité comme seul type d’entrée d’une méthode pour définir une méthode de zéro argument ou comme type de retour unique pour définir une méthode qui retourne une valeur void

Évitez les autres utilisations du type d’unité. Ils sont corrects :

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

Ceci est incorrect :

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Rechercher les valeurs NULL sur les limites de l’API .NET vanille

Le code d’implémentation F # a tendance à avoir moins de valeurs NULL, en raison de modèles de conception immuables et de restrictions sur l’utilisation de littéraux NULL pour les types F #. D’autres langages .NET utilisent souvent la valeur null de manière plus fréquente. Pour cette raison, le code F # qui expose une API .NET vanille doit vérifier les paramètres pour la valeur null au niveau de la limite de l’API et éviter que ces valeurs circulent plus profondément dans le code d’implémentation F #. La `isNull` fonction ou le modèle correspondant au `null` modèle peut être utilisé.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Évitez d’utiliser des tuples comme valeurs de retour

Au lieu de cela, préférez retourner un type nommé contenant les données agrégées, ou utiliser des paramètres out pour retourner plusieurs valeurs. Bien que les tuples et les tuples de struct existent dans .NET (y compris la prise en charge du langage C# pour les tuples de struct), ils ne fournissent pas le plus souvent l’API idéale et attendue pour les développeurs .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Éviter l’utilisation de la curryfication des paramètres

Utilisez plutôt des conventions d’appel .NET `Method(arg1,arg2,…,argN)` .

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Conseil : Si vous concevez des bibliothèques en vue d’une utilisation à partir de n’importe quel langage .NET, il n’y a pas de substitut pour effectuer des tâches expérimentales C# et Visual Basic programmation pour vous assurer que vos bibliothèques ne sont pas correctes dans ces langues. Vous pouvez également utiliser des outils tels que .NET Reflector et l’Explorateur d’objets de Visual Studio pour vous assurer que les bibliothèques et leur documentation s’affichent comme prévu pour les développeurs.

## <a name="appendix"></a>Annexe

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Exemple de bout en bout de la conception de code F # pour une utilisation par d’autres langages .NET

Considérons la classe suivante :

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

Le type F # inféré de cette classe est le suivant :

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

Voyons comment ce type F # apparaît pour un programmeur qui utilise un autre langage .NET. Par exemple, la « signature » C# approximative est la suivante :

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Il y a quelques points importants à noter sur la façon dont F # représente les constructions ici. Par exemple :

* Les métadonnées telles que les noms d’arguments ont été conservées.

* Les méthodes F # qui acceptent deux arguments deviennent des méthodes C# qui acceptent deux arguments.

* Les fonctions et les listes deviennent des références aux types correspondants dans la bibliothèque F #.

Le code suivant montre comment ajuster ce code pour prendre en compte ces éléments.

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

Le type F # inféré du code est le suivant :

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

La signature C# est maintenant la suivante :

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Les correctifs effectués pour préparer ce type pour une utilisation dans le cadre d’une bibliothèque .NET vanille sont les suivants :

* Plusieurs noms modifiés : `Point1` , `n` , `l` et sont `f` devenus `RadialPoint` ,, `count` `factor` et `transform` , respectivement.

* Utilise un type de retour `seq<RadialPoint>` au lieu de `RadialPoint list` en modifiant une construction de liste à l’aide `[ ... ]` d’une construction de séquence à l’aide de `IEnumerable<RadialPoint>` .

* Utilisé le type délégué .NET `System.Func` au lieu d’un type de fonction F #.

Cela rend l’utilisation beaucoup plus intéressante dans le code C#.
