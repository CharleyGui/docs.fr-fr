---
title: Concepts de base des expressions de requête (LINQ en C#)
description: Présente les concepts liés aux expressions de requête
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 83beaa82d4b4b42ff9da5230edddd391b33a0717
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173352"
---
# <a name="query-expression-basics"></a>Concepts de base des expressions de requête

Cet article présente les concepts fondamentaux liés aux expressions de requête en C#.

## <a name="what-is-a-query-and-what-does-it-do"></a>Qu’est-ce qu’une requête et quel est son rôle ?

Une *requête* est un jeu d’instructions qui décrit quelles données doivent être récupérées à partir d’une source (ou de sources) de données fournie, et quelles forme et organisation les données retournées doivent avoir. Une requête est distincte des résultats qu’elle génère.

De manière générale, les données sources sont organisées logiquement comme une séquence d’éléments du même type. Par exemple, une table de base de données SQL contient une séquence de lignes. Un fichier XML contient une « séquence » d’éléments XML (bien que ceux-ci soient organisés hiérarchiquement dans une arborescence). Une collection en mémoire contient une séquence d’objets.

Du point de vue d’une application, le type et la structure spécifiques des données sources d’origine ne sont pas importants. L’application voit toujours les données sources comme une collection <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>. Par exemple, dans LINQ to XML, les données sources sont rendues visibles sous la forme d’un `IEnumerable`\<<xref:System.Xml.Linq.XElement>.

Compte tenu de cette séquence source, une requête peut effectuer l’une des trois actions suivantes :

- Récupérer un sous-ensemble des éléments pour générer une nouvelle séquence sans modifier les éléments individuels. La requête peut alors trier ou regrouper la séquence retournée de plusieurs façons, comme indiqué dans l’exemple suivant (supposons que `scores` est un `int[]`) :

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Récupérer une séquence d’éléments comme dans l’exemple précédent, mais les transformer en un nouveau type d’objet. Par exemple, une requête peut récupérer uniquement les noms de certains enregistrements de clients dans une source de données. Elle peut aussi récupérer l’enregistrement complet, puis l’utiliser pour construire un autre type d’objet en mémoire, voire des données XML, avant de générer la séquence de résultat final. L’exemple suivant affiche une projection d’un `int` en `string`. Notez le nouveau type de `highScoresQuery`.

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Récupérer une valeur singleton sur les données sources, par exemple :

  - Nombre d’éléments qui correspondent à une certaine condition.

  - Élément qui a la valeur la plus grande ou la plus petite.

  - Premier élément qui correspond à une condition, ou somme de valeurs particulières dans un jeu d’éléments spécifié. Par exemple, la requête suivante retourne le nombre de notes supérieures à 80 à partir du tableau d’entiers `scores` :

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    Dans l’exemple précédent, notez l’utilisation de parenthèses autour de l’expression de requête avant l’appel à la méthode `Count`. Vous pouvez également exprimer ceci en utilisant une nouvelle variable pour stocker le résultat concret. Cette technique est plus explicite, car elle conserve la variable qui stocke la requête à un emplacement distinct de la requête qui stocke un résultat.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

Dans l’exemple précédent, la requête est exécutée dans l’appel à `Count`, car `Count` doit effectuer une itération sur les résultats afin de déterminer le nombre d’éléments retournés par `highScoresQuery`.

## <a name="what-is-a-query-expression"></a>Qu’est-ce qu’une expression de requête ?

Une *expression de requête* est une requête exprimée dans la syntaxe de la requête. Une expression de requête est une construction de langage de premier ordre. Elle est similaire à toute autre expression et peut être utilisée dans tous les contextes dans lesquels une expression C# est valide. Une expression de requête se compose d’un jeu de clauses écrit dans une syntaxe déclarative semblable à du SQL ou du XQuery. Chaque clause contient à son tour une ou plusieurs expressions C#, et ces expressions peuvent elles-mêmes être une expression de requête ou contenir une expression de requête.

Une expression de requête doit commencer par une clause [from](../language-reference/keywords/from-clause.md) et doit se terminer par une clause [select](../language-reference/keywords/select-clause.md) ou [group](../language-reference/keywords/group-clause.md). Entre la première clause `from` et la dernière clause `select` ou `group`, elle peut contenir une ou plusieurs clauses facultatives : [where](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [join](../language-reference/keywords/join-clause.md), [let](../language-reference/keywords/let-clause.md) et même d’autres clauses [from](../language-reference/keywords/from-clause.md). Vous pouvez également utiliser le mot clé [into](../language-reference/keywords/into.md) pour que le résultat d’une clause `join` ou `group` puisse servir de source pour des clauses de requête supplémentaires dans la même expression de requête.

### <a name="query-variable"></a>Variable de requête

Dans LINQ, une variable de requête correspond à n’importe quelle variable qui stocke une *requête* au lieu des *résultats* d’une requête. Plus spécifiquement, une variable de requête est toujours un type énumérable qui produit une séquence d’éléments quand elle est itérée dans une instruction `foreach` ou un appel direct à sa méthode `IEnumerator.MoveNext`.

L’exemple de code suivant montre une expression de requête simple avec une source de données, une clause de filtrage, une clause de classement et aucune transformation des éléments sources. La clause `select` termine la requête.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

Dans l’exemple précédent, `scoreQuery` est une *variable de requête* qui est parfois désignée simplement sous le nom de *requête*. La variable de requête ne stocke aucune donnée de résultat réelle, générée dans la boucle `foreach`. De plus, quand l’instruction `foreach` s’exécute, les résultats de la requête ne sont pas retournés via la variable de requête `scoreQuery`. Au lieu de cela, ils sont retournés via la variable d’itération `testScore`. La variable `scoreQuery` peut être itérée dans une deuxième boucle `foreach`. Elle générera les mêmes résultats tant que ni elle ni la source de données ne sont modifiées.

Une variable de requête peut stocker une requête exprimée dans la syntaxe de requête ou dans la syntaxe de méthode, ou dans une combinaison des deux. Dans les exemples suivants, `queryMajorCities` et `queryMajorCities2` sont des variables de requête :

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

En revanche, les deux exemples suivants affichent des variables qui ne sont pas des variables de requête, même si chacune d’entre elles est initialisée avec une requête. Il ne s’agit pas de variables de requête, car elles stockent des résultats :

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Pour plus d’informations sur les différents modes d’expression de requêtes, consultez [Syntaxe de requête et syntaxe de méthode dans LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Types explicites et implicites de variables de requête

Cette documentation fournit généralement le type explicite de la variable de requête pour afficher la relation de type entre la variable de requête et la [clause select](../language-reference/keywords/select-clause.md). Toutefois, vous pouvez également utiliser le mot clé [var](../language-reference/keywords/var.md) pour indiquer au compilateur de déduire le type d’une variable de requête (ou toute autre variable locale) au moment de la compilation. Par exemple, l’exemple de requête expliqué précédemment dans cette rubrique peut également être exprimé à l’aide de types implicites :

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Pour plus d’informations, consultez [Variables locales implicitement typées](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) et [Relations des types dans des opérations de requête LINQ](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

### <a name="starting-a-query-expression"></a>Démarrage d’une expression de requête

Une expression de requête doit commencer par une clause `from`. Elle spécifie une source de données avec une variable de portée. La variable de portée représente chaque élément consécutif dans la séquence source comme la séquence source parcourue. La variable de portée est fortement typée selon le type d’éléments dans la source de données. Dans l’exemple suivant, comme `countries` est un tableau d’objets `Country`, la variable de portée est également de type `Country`. Étant donné que la variable de portée est fortement typée, vous pouvez utiliser l’opérateur point pour accéder à tous les membres disponibles du type.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

La variable de portée est dans la portée tant que la requête n’est pas quittée avec un point-virgule ou une clause *continuation*.

Une expression de requête peut contenir plusieurs clauses `from`. Utilisez des clauses `from` supplémentaires quand chaque élément de la séquence source est lui-même une collection ou contient une collection. Par exemple, supposons que vous avez une collection d’objets `Country` et que chacun d’entre eux contient une collection d’objets `City` nommés `Cities`. Pour interroger les objets `City` dans chaque `Country`, utilisez deux clauses `from` comme indiqué ici :

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Pour plus d’informations, consultez [from, clause](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Fin d’une expression de requête

Une expression de requête doit se terminer par une clause `group` ou une clause `select`.

#### <a name="group-clause"></a>group, clause

Utilisez la clause `group` pour générer une séquence de groupes organisée par une clé que vous spécifiez. La clé peut correspondre à tout type de données. Par exemple, la requête suivante crée une séquence de groupes qui contient un ou plusieurs objets `Country` dont la clé est une valeur `char`.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Pour plus d’informations sur le regroupement, consultez [group, clause](../language-reference/keywords/group-clause.md).

#### <a name="select-clause"></a>select, clause

Utilisez la clause `select` pour générer tous les autres types de séquences. Une clause `select` simple génère simplement une séquence du même type d’objets que les objets contenus dans la source de données. Dans cet exemple, la source de données contient des objets `Country`. La clause `orderby` trie simplement les éléments dans un nouvel ordre et la clause `select` génère une séquence des objets `Country` réorganisés.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

La clause `select` peut être utilisée pour transformer des données sources en séquences de nouveaux types. Cette transformation est également appelée *projection*. Dans l’exemple suivant, la clause `select`*projette* une séquence de types anonymes qui contient uniquement un sous-ensemble des champs dans l’élément d’origine. Notez que les nouveaux objets sont initialisés à l’aide d’un initialiseur d’objet.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Pour plus d’informations sur toutes les façons d’utiliser une clause `select` pour transformer des données sources, consultez [select, clause](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>Continuations avec « into »

Vous pouvez utiliser le mot clé `into` dans une clause `select` ou `group` pour créer un identificateur temporaire qui stocke une requête. Procédez ainsi quand vous devez effectuer des opérations de requête supplémentaires sur une requête après une opération de regroupement ou de sélection. Dans l’exemple suivant, les `countries` sont regroupés en fonction du remplissage, par plages de 10 millions. Une fois ces groupes créés, des clauses supplémentaires éliminent des groupes par filtrage, puis trient les groupes par ordre croissant. Pour effectuer ces opérations supplémentaires, la continuation représentée par `countryGroup` est requise.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Pour plus d’informations, consultez [into](../language-reference/keywords/into.md).

### <a name="filtering-ordering-and-joining"></a>Filtrage, classement et jointure

Entre la clause `from` initiale et la clause `select` ou `group` finale, toutes les autres clauses (`where`, `join`, `orderby`, `from`, `let`) sont facultatives. Chacune des clauses facultatives peut être utilisée zéro fois ou plusieurs fois dans un corps de requête.

#### <a name="where-clause"></a>where, clause

Utilisez la clause `where` pour éliminer par filtrage des éléments des données sources selon une ou plusieurs expressions de prédicat. La clause `where` de l’exemple suivant a un prédicat avec deux conditions.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Pour plus d’informations, consultez [where, clause](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>orderby, clause

Utilisez la clause `orderby` pour trier les résultats par ordre croissant ou décroissant. Vous pouvez également spécifier des ordres de tri secondaires. L’exemple suivant effectue un tri principal sur les objets `country` en utilisant la propriété `Area`. Il effectue ensuite un tri secondaire en utilisant la propriété `Population`.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

Le mot clé `ascending` est facultatif ; il s’agit de l’ordre de tri par défaut si aucun ordre n’est spécifié. Pour plus d’informations, voir [clause d’ordre](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>join, clause

Utilisez la clause `join` pour associer et/ou combiner des éléments d’une source de données avec des éléments d’une autre source de données en fonction d’une comparaison d’égalité entre des clés spécifiées dans chaque élément. Dans LINQ, les opérations de jointure sont effectuées sur les séquences des objets dont les éléments sont des types différents. Après avoir joint deux séquences, vous devez utiliser une instruction `select` ou `group` pour spécifier quel élément stocker dans la séquence de sortie. Vous pouvez également utiliser un type anonyme pour combiner des propriétés de chaque jeu d’éléments associés dans un nouveau type pour la séquence de sortie. L’exemple suivant associe des objets `prod` dont la propriété `Category` correspond à l’une des catégories dans le tableau de chaînes `categories`. Les `Category` produits qui ne `categories` correspondent à aucune chaîne sont filtrés. L’énoncé `select` projette un nouveau type `cat` `prod`dont les propriétés sont prises à la fois et .

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Vous pouvez également effectuer une jointure groupée en stockant les résultats de l’opération `join` dans une variable temporaire à l’aide du mot clé [into](../language-reference/keywords/into.md). Pour plus d’informations, voir [clause d’adhésion](../language-reference/keywords/join-clause.md).

#### <a name="let-clause"></a>clause let

Utilisez la clause `let` pour stocker le résultat d’une expression telle qu’un appel de méthode dans une nouvelle variable de portée. Dans l’exemple suivant, la variable de portée `firstName` stocke le premier élément du tableau de chaînes retourné par `Split`.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Pour plus d’informations, consultez [let, clause](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Sous-requêtes dans une expression de requête

Une clause de requête peut elle-même contenir une expression de requête, qui est parfois connue sous le nom de *sous-requête*. Chaque sous-requête démarre avec sa propre clause `from` qui ne pointe pas nécessairement vers la même source de données dans la première clause `from`. Par exemple, la requête suivante montre une expression de requête utilisée dans l’instruction select pour récupérer les résultats d’une opération de regroupement.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Pour plus d’informations, voir [Effectuer une sous-querie sur une opération de regroupement](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation CMD](../programming-guide/index.md)
- [Requête intégrée linguistique (LINQ)](index.md)
- [Mots clés de requête (LINQ)](../language-reference/keywords/query-keywords.md)
- [Aperçu standard des opérateurs de requêtes](../programming-guide/concepts/linq/standard-query-operators-overview.md)
