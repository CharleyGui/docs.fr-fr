---
title: Comparaison avec System. Data. SQLite
ms.date: 12/13/2019
description: Décrit quelques-unes des différences entre les bibliothèques Microsoft. Data. sqlite et System. Data. SQLite.
ms.openlocfilehash: 076bbc6f746cf9296c96ec73047397a21a3b2558
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900709"
---
# <a name="comparison-to-systemdatasqlite"></a>Comparaison avec System. Data. SQLite

Dans 2005, Robert Simpson a créé System. Data. SQLite, un fournisseur SQLite pour ADO.NET 2,0. Dans 2010, l’équipe SQLite a pris en charge la maintenance et le développement du projet. Il est également intéressant de noter que l’équipe mono a fait la duplication du code dans 2007 en tant que mono. Data. sqlite. System. Data. SQLite a un long historique et a évolué vers un fournisseur ADO.NET entièrement stable et complet avec les outils Visual Studio. Les nouvelles versions continuent à expédier les assemblys compatibles avec chaque version de .NET Framework à la version 2,0 et même .NET Compact Framework 3,5.

La première version de .NET Core (publiée dans 2016) était une implémentation unique, légère, moderne et multiplateforme de .NET. Les API obsolètes et les API avec d’autres alternatives modernes ont été supprimées intentionnellement. ADO.NET n’incluait aucune API de DataSet (y compris DataTable et DataAdapter).

L’équipe Entity Framework a été très familiarisé avec le code base System. Data. SQLite. Brice Lambson, membre de l’équipe EF, avait auparavant aidé l’équipe SQLite à ajouter la prise en charge des versions 5 et 6 de Entity Framework. Brice a également fait l’expérience de sa propre implémentation d’un fournisseur SQLite ADO.NET en même temps que .NET Core était planifié. Après une longue discussion, l’équipe Entity Framework a décidé de créer Microsoft. Data. sqlite en fonction du prototype de brice. Cela leur permettrait de créer une nouvelle implémentation légère et moderne qui s’alignerait sur les objectifs de .NET Core.

À titre d’exemple de ce que nous entendons par plus moderne, voici le code permettant de créer une [fonction définie](user-defined-functions.md) par l’utilisateur dans System. Data. sqlite et Microsoft. Data. sqlite.

```csharp
// System.Data.SQLite
connection.BindFunction(
    new SQLiteFunctionAttribute("ceiling", 1, FunctionType.Scalar),
    (Func<object[], object>)((object[] args) => Math.Ceiling((double)((object[])args[1])[0])),
    null);

// Microsoft.Data.Sqlite
connection.CreateFunction(
    "ceiling",
    (double arg) => Math.Ceiling(arg));
```

Dans 2017, .NET Core 2,0 a subi un changement de stratégie. Il a été décidé que la compatibilité avec .NET Framework était vitale pour la réussite de .NET Core. La plupart des API supprimées, y compris les API de jeu de données, ont été rajoutées. Comme c’était le cas pour de nombreux autres, cette valeur de System. Data. SQLite débloquée, ce qui lui permet de porter également sur .NET Core. L’objectif initial de Microsoft. Data. sqlite à être léger et moderne, toutefois, reste toujours. Pour plus d’informations sur les API ADO.NET non implémentées par Microsoft. Data. sqlite, consultez [limitations de ADO.net](adonet-limitations.md) .

Lorsque de nouvelles fonctionnalités sont ajoutées à Microsoft. Data. sqlite, la conception de System. Data. SQLite est prise en compte. Nous essayons, dans la mesure du possible, de réduire les modifications entre les deux pour faciliter la transition entre eux.

## <a name="data-types"></a>Types de données

La plus grande différence entre Microsoft. Data. sqlite et System. Data. SQLite est la manière dont les types de données sont gérés. Comme décrit dans [types de données](types.md), Microsoft. Data. sqlite ne tente pas de masquer le quirkiness sous-jacent de SQLite, ce qui permet de spécifier n’importe quelle chaîne arbitraire comme type de colonne et possède uniquement quatre types primitifs : entier, réel, texte et objet BLOB.

System. Data. SQLite applique une sémantique supplémentaire aux types de colonne qui les mappent directement aux types .NET. Cela donne au fournisseur une sensation plus fortement typée, mais il a des bords approximatifs. Par exemple, ils devaient introduire une nouvelle instruction SQL (TYPES) pour spécifier les types de colonne des expressions dans les instructions SELECT.

## <a name="connection-strings"></a>Chaînes de connexion

Microsoft. Data. sqlite a beaucoup moins de mots clés de [chaîne de connexion](connection-strings.md) . Le tableau suivant présente des alternatives qui peuvent être utilisées à la place.

| Mot clé          | Alternative                                         |
| ---------------- | --------------------------------------------------- |
| Taille de cache       | Envoyer`PRAGMA cache_size = <pages>`                  |
| Délai d’expiration par défaut  | Utiliser la propriété DefaultTimeout sur SqliteConnection |
| FailIfMissing    | Utilisez `Mode=ReadWrite`.                                |
| FullUri          | Utiliser le mot clé de source de données                         |
| Mode Journal     | Envoyer`PRAGMA journal_mode = <mode>`                 |
| Format hérité    | Envoyer`PRAGMA legacy_file_format = 1`                |
| Nombre maximal de pages   | Envoyer`PRAGMA max_page_count = <pages>`              |
| Taille de la page        | Envoyer`PRAGMA page_size = <bytes>`                   |
| Lecture seule        | Utilisez `Mode=ReadOnly`.                                 |
| Synchrone      | Envoyer`PRAGMA synchronous = <mode>`                  |
| Uri              | Utiliser le mot clé de source de données                         |
| UseUTF16Encoding | Envoyer`PRAGMA encoding = 'UTF-16'`                   |

## <a name="authorization"></a>Autorisation

Microsoft. Data. sqlite ne dispose d’aucune API exposant le rappel d’autorisation de SQLite. Utilisez [#13835](https://github.com/dotnet/efcore/issues/13835) de problème pour fournir des commentaires sur cette fonctionnalité.

## <a name="data-change-notifications"></a>Notifications de modification de données

Microsoft. Data. sqlite ne dispose d’aucune API exposant les notifications de modification de données de SQLite. Utilisez [#13827](https://github.com/dotnet/efcore/issues/13827) de problème pour fournir des commentaires sur cette fonctionnalité.

## <a name="virtual-table-modules"></a>Modules de table virtuelle

Microsoft. Data. sqlite ne dispose d’aucune API pour la création de modules de table virtuelle. Utilisez [#13823](https://github.com/dotnet/efcore/issues/13823) de problème pour fournir des commentaires sur cette fonctionnalité.

## <a name="see-also"></a>Voir aussi

* [Types de données](types.md)
* [Chaînes de connexion](connection-strings.md)
* [Chiffrement](encryption.md)
* [Limitations de ADO.NET](adonet-limitations.md)
* [Limitations de dapper](dapper-limitations.md)
