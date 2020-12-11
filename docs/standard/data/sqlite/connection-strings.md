---
title: Chaînes de connexion
ms.date: 12/08/2020
description: Les mots clés et les valeurs de chaîne de connexion pris en charge.
ms.openlocfilehash: 35283664c4ac3985d4f517fde77644ab2a891120
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110739"
---
# <a name="connection-strings"></a>Chaînes de connexion

Une chaîne de connexion est utilisée pour spécifier la manière de se connecter à la base de données. Les chaînes de connexion dans Microsoft. Data. sqlite suivent la [syntaxe ADO.net](../../../framework/data/adonet/connection-strings.md) standard sous la forme d’une liste de mots clés et de valeurs séparées par des points-virgules.

## <a name="keywords"></a>Mots clés

Les mots clés de chaîne de connexion suivants peuvent être utilisés avec Microsoft. Data. sqlite :

### <a name="data-source"></a>Source de données

Chemin d'accès au fichier de base de données. *DataSource* (sans espace) et *filename* sont des alias de ce mot clé.

SQLite traite les chemins d’accès par rapport au répertoire de travail actuel. Vous pouvez également spécifier des chemins d’accès absolus.

S’il est **vide**, SQLite crée une base de données sur disque temporaire qui est supprimée lorsque la connexion est fermée.

Si `:memory:` , une base de données en mémoire est utilisée. Pour plus d’informations, consultez [bases de données en mémoire](in-memory-databases.md).

Les chemins d’accès qui commencent par la `|DataDirectory|` chaîne de substitution sont traités de la même façon que les chemins d’accès relatifs. Si cette valeur est définie, les chemins d’accès sont définis par rapport à la valeur de la propriété de domaine d’application DataDirectory.

Ce mot clé prend également en charge les noms de fichiers [URI](https://www.sqlite.org/uri.html).

### <a name="mode"></a>Mode

Mode de connexion.

| Valeur           | Description                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | Ouvre la base de données pour la lecture et l’écriture, et la crée si elle n’existe pas. Il s’agit de la valeur par défaut. |
| Lecture/écriture       | Ouvre la base de données pour la lecture et l’écriture.                                                        |
| Lecture seule        | Ouvre la base de données en mode lecture seule.                                                              |
| Mémoire          | Ouvre une base de données en mémoire.                                                                       |

### <a name="cache"></a>Cache

Mode de mise en cache utilisé par la connexion.

| Valeur   | Description                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Default | Utilise le mode par défaut de la bibliothèque SQLite sous-jacente. Il s’agit de la valeur par défaut.                   |
| Privé | Chaque connexion utilise un cache privé.                                                          |
| Partagé  | Les connexions partagent un cache. Ce mode peut modifier le comportement du verrouillage de la transaction et de la table. |

### <a name="password"></a>Mot de passe

Clé de chiffrement. Lorsqu' `PRAGMA key` il est spécifié, est envoyé immédiatement après l’ouverture de la connexion.

> [!WARNING]
> Le mot de passe n’a aucun effet lorsque le chiffrement n’est pas pris en charge par la bibliothèque SQLite native.

> [!NOTE]
> Le mot clé Password a été ajouté dans la version 3,0.

### <a name="foreign-keys"></a>Clés étrangères

Valeur indiquant s’il faut activer les contraintes de clé étrangère.

> [!NOTE]
> Le mot clé Foreign Keys a été ajouté dans la version 3,0.

| Valeur   | Description
| ------- | --- |
| True    | Envoie `PRAGMA foreign_keys = 1` immédiatement après l’ouverture de la connexion.
| False   | Envoie `PRAGMA foreign_keys = 0` immédiatement après l’ouverture de la connexion.
| (empty) | N’envoie pas `PRAGMA foreign_keys` . Il s’agit de la valeur par défaut. |

Il n’est pas nécessaire d’activer les clés étrangères si, comme dans e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS a été utilisé pour compiler la bibliothèque SQLite native.

### <a name="recursive-triggers"></a>Déclencheurs récursifs

Valeur qui indique s’il faut activer les déclencheurs récursifs.

> [!NOTE]
> Le mot clé déclencheurs récursifs a été ajouté dans la version 3,0.

| Valeur | Description                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Envoie `PRAGMA recursive_triggers` immédiatement après l’ouverture de la connexion. |
| False | N’envoie pas `PRAGMA recursive_triggers` . Il s’agit de la valeur par défaut.              |

## <a name="connection-string-builder"></a>Générateur de chaînes de connexion

Vous pouvez utiliser <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> comme un moyen fortement typé de créer des chaînes de connexion. Il peut également être utilisé pour empêcher les attaques par injection de chaîne de connexion.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Exemples

### <a name="basic"></a>De base

Chaîne de connexion de base avec un cache partagé pour améliorer la concurrence.

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Chiffré

Base de données chiffrée.

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>Lecture seule

Base de données en lecture seule qui ne peut pas être modifiée par l’application.

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>En mémoire

Base de données en mémoire privée.

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>Partage en mémoire

Base de données en mémoire partageable identifiée par le nom *partageable*.

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Voir aussi

* [Chaînes de connexion dans ADO.NET](../../../framework/data/adonet/connection-strings.md)
* [Bases de données en mémoire](in-memory-databases.md)
* [Transactions](transactions.md)
