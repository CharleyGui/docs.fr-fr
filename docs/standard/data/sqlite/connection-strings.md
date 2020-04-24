---
title: Chaînes de connexion
ms.date: 12/13/2019
description: Les mots clés et les valeurs de chaîne de connexion pris en charge.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400448"
---
# <a name="connection-strings"></a>Chaînes de connexion

Une chaîne de connexion est utilisée pour spécifier la manière de se connecter à la base de données. Les chaînes de connexion dans Microsoft. Data. sqlite suivent la [syntaxe ADO.net](../../../framework/data/adonet/connection-strings.md) standard sous la forme d’une liste de mots clés et de valeurs séparées par des points-virgules.

## <a name="keywords"></a>Mots clés

Les mots clés de chaîne de connexion suivants peuvent être utilisés avec Microsoft. Data. sqlite :

### <a name="data-source"></a>Source de données

Chemin d'accès au fichier de base de données. *DataSource* (sans espace) et *filename* sont des alias de ce mot clé.

SQLite traite les chemins d’accès par rapport au répertoire de travail actuel. Vous pouvez également spécifier des chemins d’accès absolus.

S’il est **vide**, SQLite crée une base de données sur disque temporaire qui est supprimée lorsque la connexion est fermée.

Si `:memory:`, une base de données en mémoire est utilisée. Pour plus d’informations, consultez [bases de données en mémoire](in-memory-databases.md).

Les chemins d’accès qui `|DataDirectory|` commencent par la chaîne de substitution sont traités de la même façon que les chemins d’accès relatifs. Si cette valeur est définie, les chemins d’accès sont définis par rapport à la valeur de la propriété de domaine d’application DataDirectory.

Ce mot clé prend également en charge les noms de fichiers [URI](https://www.sqlite.org/uri.html).

### <a name="mode"></a>Mode

Mode de connexion.

| Value           | Description                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | Ouvre la base de données pour la lecture et l’écriture, et la crée si elle n’existe pas. Il s’agit de la valeur par défaut. |
| Lecture/écriture       | Ouvre la base de données pour la lecture et l’écriture.                                                        |
| Lecture seule        | Ouvre la base de données en mode lecture seule.                                                              |
| Mémoire          | Ouvre une base de données en mémoire.                                                                       |

### <a name="cache"></a>Cache

Mode de mise en cache utilisé par la connexion.

| Value   | Description                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Default | Utilise le mode par défaut de la bibliothèque SQLite sous-jacente. Il s’agit de la valeur par défaut.                   |
| Privé | Chaque connexion utilise un cache privé.                                                          |
| Partagé  | Les connexions partagent un cache. Ce mode peut modifier le comportement du verrouillage de la transaction et de la table. |

### <a name="password"></a>Mot de passe

Clé de chiffrement. Lorsqu’il est `PRAGMA key` spécifié, est envoyé immédiatement après l’ouverture de la connexion.

> [!WARNING]
> Le mot de passe n’a aucun effet lorsque le chiffrement n’est pas pris en charge par la bibliothèque SQLite native.

### <a name="foreign-keys"></a>Clés étrangères

Valeur indiquant s’il faut activer les contraintes de clé étrangère.

| Value   | Description
| ------- | --- |
| True    | Envoie `PRAGMA foreign_keys = 1` immédiatement après l’ouverture de la connexion.
| False   | Envoie `PRAGMA foreign_keys = 0` immédiatement après l’ouverture de la connexion.
| (empty) | N’envoie `PRAGMA foreign_keys`pas. Il s’agit de la valeur par défaut. |

Il n’est pas nécessaire d’activer les clés étrangères si, comme dans e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS a été utilisé pour compiler la bibliothèque SQLite native.

### <a name="recursive-triggers"></a>Déclencheurs récursifs

Valeur qui indique s’il faut activer les déclencheurs récursifs.

| Value | Description                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Envoie `PRAGMA recursive_triggers` immédiatement après l’ouverture de la connexion. |
| False | N’envoie `PRAGMA recursive_triggers`pas. Il s’agit de la valeur par défaut.              |

## <a name="connection-string-builder"></a>Générateur de chaînes de connexion

Vous pouvez utiliser <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> comme un moyen fortement typé de créer des chaînes de connexion. Il peut également être utilisé pour empêcher les attaques par injection de chaîne de connexion.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Exemples

### <a name="basic"></a>De base

Chaîne de connexion de base avec un cache partagé pour améliorer la concurrence.

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Chiffré

Base de données chiffrée.

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>Lecture seule

Base de données en lecture seule qui ne peut pas être modifiée par l’application.

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>En mémoire

Base de données en mémoire privée.

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>Partage en mémoire

Base de données en mémoire partageable identifiée par le nom *partageable*.

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Voir aussi

* [Chaînes de connexion dans ADO.NET](../../../framework/data/adonet/connection-strings.md)
* [Bases de données en mémoire](in-memory-databases.md)
* [Transactions](transactions.md)
