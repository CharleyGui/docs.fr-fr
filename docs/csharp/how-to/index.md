---
title: Articles de guide pratique (Guide C#)
description: Série de petits conseils et d’exemples de code spécifiques courts
ms.date: 12/20/2017
ms.openlocfilehash: 63410d687bd09f95a5ce7ce9304f2281b2f8d334
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859533"
---
# <a name="how-to-c"></a>Guides pratiques (C#)

Dans la section Guides pratiques du guide C#, vous trouverez rapidement des réponses à des questions courantes. Dans certains cas, les articles peuvent figurer dans plusieurs sections. Nous avons souhaité les rendre plus faciles à trouver via plusieurs voies de recherche. 

## <a name="general-c-concepts"></a>Concepts C# généraux

Plusieurs conseils et astuces sont des pratiques courantes des développeurs en C#.

- [Initialiser des objets à l’aide d’un initialiseur d’objet](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Découvrir les différences entre le passage d’un struct et d’une classe à une méthode](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Guide pratique pour utiliser des expressions lambda](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).
- [Résoudre les conflits de nom de type à l’aide de l’alias d’espace de noms global](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [Utiliser la surcharge d’opérateur](../language-reference/operators/operator-overloading.md).
- [Implémenter et appeler une méthode d’extension personnalisée](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Même les programmeurs en C# pourraient vouloir [utiliser l’espace de noms `My` de VB](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [Créer une méthode pour un type `enum` à l’aide des méthodes d’extension](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Membres de classe et de struct

Vous créez des classes et des structs pour implémenter votre programme. Ces techniques sont couramment utilisées lors de l’écriture de classes ou de structs.

- [Déclarer des propriétés implémentées automatiquement](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Déclarer et utiliser des propriétés en lecture-écriture](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Définir des constantes](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Remplacer la méthode `ToString` pour fournir la sortie de chaîne](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Définir des propriétés abstraites](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Utiliser les fonctionnalités de la documentation XML pour documenter votre code](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Implémenter de manière explicite des membres d’interface](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) pour conserver votre interface publique concise.
- [Implémenter de manière explicite des membres de deux interfaces](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Utilisation des collections

Ces articles vous permettent d’utiliser des collections de données.

- [Initialiser un dictionnaire avec un initialiseur de collection](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Utilisation de chaînes

Les chaînes constituent le type de données fondamental utilisé pour afficher ou manipuler du texte. Ces articles présentent les pratiques courantes avec des chaînes.

- [Comparer des chaînes](compare-strings.md).
- [Modifier le contenu d’une chaîne](modify-string-contents.md).
- [Déterminer si une chaîne représente un nombre](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Utiliser `String.Split` pour séparer les chaînes](parse-strings-using-split.md).
- [Combiner plusieurs chaînes en une seule](concatenate-multiple-strings.md).
- [Rechercher du texte dans une chaîne](search-strings.md).

## <a name="convert-between-types"></a>Conversion entre types

Vous aurez peut-être besoin de convertir un objet en un autre type.

- [Déterminer si une chaîne représente un nombre](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Convertir entre des chaînes qui représentent des nombres hexadécimaux et le nombre](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Convertir une chaîne en `DateTime`](../../standard/base-types/parsing-datetime.md).
- [Convertir un tableau d’octets en int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Convertir une chaîne en nombre ](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Utiliser les critères spéciaux et les opérateurs `as` et `is` pour caster sans risque en un autre type](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).
- [Définir des conversions de type personnalisé](../language-reference/operators/user-defined-conversion-operators.md).
- [Déterminer si un type est un type valeur nullable](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md).
- [Convertir entre des types valeur nullable et non nullable](../programming-guide/nullable-types/using-nullable-types.md#conversion-from-a-nullable-type-to-an-underlying-type).

## <a name="equality-and-ordering-comparisons"></a>Comparaisons d’égalité et de classement

Vous pouvez créer des types qui définissent leurs propres règles pour l’égalité ou qui définissent un classement naturel entre les objets de ce type.

- [Tester l’égalité basée sur les références](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Définir une égalité basée sur les valeurs pour un type](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Gestion des exceptions

Les programmes .NET signalent que des méthodes n’ont pas réussi à effectuer leur travail en levant des exceptions. Dans ces articles, vous allez apprendre à travailler avec les exceptions.

- [Gérer les exceptions avec `try` et `catch`](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Nettoyer les ressources avec les clauses `finally`](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Récupérer suite à des exceptions non-CLS (Common Language Specification)](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Délégués et événements

Les délégués et les événements fournissent une fonctionnalité pour les stratégies qui implique des blocs de code faiblement couplés.

- [Déclarer, instancier et utiliser des délégués](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Combiner des délégués multicast](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Les événements offrent un mécanisme permettant de publier des notifications ou de s’y abonner.

- [S’abonner à des événements et s’en désabonner](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Implémenter des événements déclarés dans des interfaces](../programming-guide/events/how-to-implement-interface-events.md).
- [Se conformer aux instructions du .NET Framework quand votre code publie des événements](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Déclencher des événements définis dans les classes de base de classes dérivées](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Implémenter des accesseurs d’événement personnalisés](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>Pratiques LINQ

LINQ vous permet d’écrire du code pour interroger une source de données qui prend en charge le modèle d’expression de requête LINQ. Ces articles vous permettent de comprendre le modèle et d’utiliser différentes sources de données.

- [Interroger une collection](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Utiliser des expressions lambda dans une requête](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Utiliser `var` dans des expressions de requête](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Retourner des sous-ensembles de propriétés d’éléments d’une requête](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Écrire des requêtes avec un filtrage complexe](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Trier les éléments d’une source de données](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Trier les éléments sur plusieurs clés](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Contrôler le type d’une projection](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Compter les occurrences d’une valeur dans une séquence source](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Calculer des valeurs intermédiaires](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Fusionner des données de plusieurs sources](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Trouver la différence définie entre deux séquences](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Déboguer des résultats de requête vides](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Ajouter des méthodes personnalisées dans des requêtes LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Traitement de plusieurs threads et traitement asynchrone

Les programmes récents utilisent souvent des opérations asynchrones. Les articles suivants vous apprennent à utiliser ces techniques.

- [Améliorer les performances asynchrones avec `System.Threading.Tasks.Task.WhenAll` ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Effectuer plusieurs requêtes web en parallèle en utilisant `async` et `await`](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Utiliser un pool de threads](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Arguments de ligne de commande dans votre programme

En règle générale, les programmes en C# ont des arguments de ligne de commande. Les articles suivants vous apprennent à accéder et à traiter ces arguments de ligne de commande.

- [Récupérer tous les arguments de ligne de commande avec `for`](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
