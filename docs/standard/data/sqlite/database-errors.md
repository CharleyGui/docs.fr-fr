---
title: Erreurs de base de données
ms.date: 12/13/2019
description: Décrit comment les erreurs et les Retirements de la base de données sont gérés par la bibliothèque.
ms.openlocfilehash: 9a613b6f94a89dc40e627c14f46836be77080035
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447271"
---
# <a name="database-errors"></a>Erreurs de base de données

<xref:Microsoft.Data.Sqlite.SqliteException>est levée lorsqu’une erreur SQLite est rencontrée. Le message est fourni par SQLite. Les `SqliteErrorCode` propriétés `SqliteExtendedErrorCode` et contiennent le [Code de résultat](https://www.sqlite.org/rescode.html) SQLite de l’erreur.

Des erreurs peuvent se produire chaque fois que Microsoft. Data. sqlite interagit avec la bibliothèque SQLite native. La liste suivante présente les scénarios courants dans lesquels des erreurs peuvent se produire :

* Ouverture d’une connexion.
* Début d’une transaction.
* Exécution d'une commande.
* Appel de <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.

Réfléchissez à la manière dont votre application gère ces erreurs.

## <a name="locking-retries-and-timeouts"></a>Verrouillage, nouvelles tentatives et délais d’expiration

SQLite est agressif lorsqu’il s’agit de verrouiller des tables et des fichiers de base de données. Si votre application active un accès simultané à la base de données, vous rencontrerez probablement des erreurs de disponibilité et de verrouillage. Vous pouvez atténuer de nombreuses erreurs en utilisant un [cache partagé](connection-strings.md#cache) et une [journalisation avec écriture anticipée](async.md).

Chaque fois que Microsoft. Data. sqlite rencontre une erreur occupée ou verrouillée, il réessaie automatiquement jusqu’à ce qu’il aboutisse ou que le délai d’attente de la commande soit atteint.

Vous pouvez augmenter le délai d’expiration de la <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>commande en définissant. Le délai d’attente par défaut est de 30 secondes. La valeur signifie `0` qu’il n’y A pas de délai d’attente.

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

Microsoft. Data. sqlite doit parfois créer un objet de commande implicite. Par exemple, pendant BeginTransaction. Pour définir le délai d’expiration de ces commandes <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>, utilisez.

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a>Voir aussi

* [Codes d’erreur SQLite](https://www.sqlite.org/rescode.html)
* [Verrouillage de fichier dans SQLite](https://www.sqlite.org/lockingv3.html)
* [Mode de cache partagé](https://www.sqlite.org/sharedcache.html)
* [Journalisation avec écriture anticipée](https://www.sqlite.org/wal.html)
