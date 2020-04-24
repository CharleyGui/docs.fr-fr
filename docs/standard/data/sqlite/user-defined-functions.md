---
title: Fonctions définies par l’utilisateur
ms.date: 12/13/2019
description: Découvrez comment créer des fonctions scalaires et d’agrégation définies par l’utilisateur.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447173"
---
# <a name="user-defined-functions"></a>Fonctions définies par l’utilisateur

La plupart des bases de données ont un dialecte de procédure SQL que vous pouvez utiliser pour définir vos propres fonctions. SQLite Toutefois, s’exécute in-process avec votre application. Au lieu d’avoir à apprendre un nouveau dialecte SQL, vous pouvez simplement utiliser le langage de programmation de votre application.

## <a name="scalar-functions"></a>Fonctions scalaires

Les fonctions scalaires retournent une valeur scalaire unique pour chaque ligne d’une requête. Définissez de nouvelles fonctions scalaires et substituez les fonctions intégrées à <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>l’aide de.

Consultez [types de données](types.md) pour obtenir la liste des types de paramètres et de `func` retour pris en charge pour l’argument.

La spécification `state` de l’argument passera cette valeur dans chaque appel de la fonction. À utiliser pour éviter les fermetures.

Spécifiez `isDeterministic` si votre fonction est déterministe pour permettre à SQLite d’utiliser des optimisations supplémentaires lors de la compilation des requêtes.

L’exemple suivant montre comment ajouter une fonction scalaire pour calculer le rayon d’un cylindre.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a>Opérateurs

Les opérateurs SQLite suivants sont implémentés par les fonctions scalaires correspondantes. La définition de ces fonctions scalaires dans votre application remplacera le comportement de ces opérateurs.

| Opérateur          | Fonction      |
| ----------------- | ------------- |
| X GLOB Y          | glob (Y, X)    |
| X LIKE Y          | like (Y, X)    |
| X LIKE O ESCAPE Z | like (Y, X, Z) |
| X CORRESPOND À Y         | match (Y, X)   |
| X REGEXP Y        | RegExp (Y, X)  |

L’exemple suivant montre comment définir la fonction RegExp pour activer son opérateur correspondant. SQLite n’inclut pas d’implémentation par défaut de la fonction RegExp.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a>Fonctions d'agrégation

Les fonctions d’agrégation retournent une valeur agrégée unique pour toutes les lignes d’une requête. Définissez et remplacez les fonctions d’agrégation <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>à l’aide de.

L' `seed` argument spécifie l’état initial du contexte. Utilisez-le pour éviter également les fermetures.

L' `func` argument est appelé une fois par ligne. Utilisez le contexte pour accumuler un résultat final. Retourne le contexte. Ce modèle permet au contexte d’être un type valeur ou immuable.

Si aucun `resultSelector` n’est spécifié, l’état final du contexte est utilisé comme résultat. Cela peut simplifier la définition des fonctions telles que SUM et Count qui n’ont besoin d’incrémenter qu’un nombre pour chaque ligne et de la retourner.

Spécifiez `resultSelector` pour calculer le résultat final à partir du contexte après l’itération dans toutes les lignes.

Consultez [types de données](types.md) pour obtenir la liste des types de paramètres `func` pris en charge pour l' `resultSelector`argument et les types de retour pour.

Si votre fonction est déterministe, spécifiez `isDeterministic` pour autoriser SQLite à utiliser des optimisations supplémentaires lors de la compilation des requêtes.

L’exemple suivant définit une fonction d’agrégation pour calculer l’écart type d’une colonne.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a>Erreurs

Si une fonction définie par l’utilisateur lève une exception, le message est renvoyé à SQLite. SQLite déclenchera alors une erreur et Microsoft. Data. sqlite lèvera un SqliteException. Pour plus d’informations, consultez [Erreurs de base de données](database-errors.md).

Par défaut, l’erreur SQLite code d’erreur est SQLITE_ERROR (ou 1). Toutefois, vous pouvez le modifier en levant un <xref:Microsoft.Data.Sqlite.SqliteException> dans votre fonction avec le souhaité <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> spécifié.

## <a name="debugging"></a>Débogage

SQLite appelle votre implémentation directement. Cela vous permet d’ajouter des points d’arrêt qui se déclenchent quand SQLite évalue des requêtes. L’expérience de débogage .NET complète est disponible pour vous aider à créer vos fonctions définies par l’utilisateur.

## <a name="see-also"></a>Voir aussi

* [Types de données](types.md)
* [SQLite fonctions principales](https://www.sqlite.org/lang_corefunc.html)
* [Fonctions d’agrégation SQLite](https://www.sqlite.org/lang_aggfunc.html)
