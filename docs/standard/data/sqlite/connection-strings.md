---
title: Chaînes de connexion
ms.date: 12/13/2019
description: Les mots-clés pris en charge et les valeurs des chaînes de connexion.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400448"
---
# <a name="connection-strings"></a>Chaînes de connexion

Une chaîne de connexion est utilisée pour spécifier comment se connecter à la base de données. Les chaînes de connexion dans Microsoft.Data.Sqlite suivent la [syntaxe standard ADO.NET](../../../framework/data/adonet/connection-strings.md) comme une liste de mots clés et de valeurs séparées des semi-remorques.

## <a name="keywords"></a>Mots clés

Les mots clés suivants de la chaîne de connexion peuvent être utilisés avec Microsoft.Data.Sqlite :

### <a name="data-source"></a>Source de données

Chemin d'accès au fichier de base de données. *DataSource* (sans espace) et *Filename* sont des alias de ce mot clé.

SQLite traite les chemins par rapport à l’annuaire de travail actuel. Des chemins absolus peuvent également être spécifiés.

En **cas de vide,** SQLite crée une base de données temporaire sur disque qui est supprimée lorsque la connexion est fermée.

Si `:memory:`, une base de données en mémoire est utilisée. Pour plus d’informations, consultez [les bases de données In-Memory](in-memory-databases.md).

Les chemins qui `|DataDirectory|` commencent par la chaîne de substitution sont traités de la même façon que les chemins relatifs. Si vous êtes défini, des chemins sont réalisés par rapport à la valeur de propriété du domaine d’application DataDirectory.

Ce mot clé prend également en charge [URI Filenames](https://www.sqlite.org/uri.html).

### <a name="mode"></a>Mode

Le mode de connexion.

| Valeur           | Description                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| LireWriteCreate | Ouvre la base de données pour la lecture et l’écriture, et la crée si elle n’existe pas. Il s’agit de la valeur par défaut. |
| Lecture/écriture       | Ouvre la base de données pour la lecture et l’écriture.                                                        |
| Lecture seule        | Ouvre la base de données en mode lecture uniquement.                                                              |
| Mémoire          | Ouvre une base de données en mémoire.                                                                       |

### <a name="cache"></a>Cache

Le mode de mise en cache utilisé par la connexion.

| Valeur   | Description                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Default | Utilise le mode par défaut de la bibliothèque SQLite sous-jacente. Il s’agit de la valeur par défaut.                   |
| Privé | Chaque connexion utilise un cache privé.                                                          |
| Partagé  | Les connexions partagent un cache. Ce mode peut modifier le comportement des transactions et du verrouillage de la table. |

### <a name="password"></a>Mot de passe

Clé de chiffrement. Lorsqu’il `PRAGMA key` est spécifié, est envoyé immédiatement après l’ouverture de la connexion.

> [!WARNING]
> Mot de passe n’a aucun effet lorsque le chiffrement n’est pas pris en charge par la bibliothèque SQLite indigène.

### <a name="foreign-keys"></a>Clés étrangères

Une valeur indiquant s’il faut permettre des contraintes clés à l’étranger.

| Valeur   | Description
| ------- | --- |
| True    | Envoie `PRAGMA foreign_keys = 1` immédiatement après l’ouverture de la connexion.
| False   | Envoie `PRAGMA foreign_keys = 0` immédiatement après l’ouverture de la connexion.
| (empty) | N’envoie `PRAGMA foreign_keys`pas . Il s’agit de la valeur par défaut. |

Il n’est pas nécessaire de permettre des clés étrangères si, comme dans e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS a été utilisé pour compiler la bibliothèque SQLite indigène.

### <a name="recursive-triggers"></a>Déclencheurs récursifs

Une valeur qui indique s’il faut activer les déclencheurs récursifs.

| Valeur | Description                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Envoie `PRAGMA recursive_triggers` immédiatement après l’ouverture de la connexion. |
| False | N’envoie `PRAGMA recursive_triggers`pas . Il s’agit de la valeur par défaut.              |

## <a name="connection-string-builder"></a>Constructeur de cordes de connexion

Vous pouvez <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> utiliser comme un moyen fortement tapé de créer des chaînes de connexion. Il peut également être utilisé pour prévenir les attaques d’injection de chaîne de connexion.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Exemples

### <a name="basic"></a>De base

Une chaîne de connexion de base avec un cache partagé pour une concurrence améliorée.

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Chiffré

Une base de données cryptée.

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>Lecture seule

Une base de données de lecture uniquement qui ne peut pas être modifiée par l’application.

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>En mémoire

Une base de données privée et en mémoire.

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>Sharable dans la mémoire

Une base de données sharable, dans la mémoire identifiée par le nom *Sharable*.

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Voir aussi

* [Chaînes de connexion dans ADO.NET](../../../framework/data/adonet/connection-strings.md)
* [Bases de données in-Memory](in-memory-databases.md)
* [Transactions](transactions.md)
