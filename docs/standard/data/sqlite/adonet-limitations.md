---
title: Limitations de ADO.NET
ms.date: 12/13/2019
description: Décrit certaines des limitations de ADO.NET que vous pouvez rencontrer.
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901254"
---
# <a name="adonet-limitations"></a>Limitations de ADO.NET

Microsoft. Data. sqlite fournit des implémentations de nombreuses abstractions ADO.NET, mais il existe certaines limitations.

## <a name="database-schema-information"></a>Informations sur le schéma de base de données

Les métadonnées relatives aux résultats de la <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> requête sont disponibles à l’aide de la méthode.

`DbConnection.GetSchema()`n’est pas implémenté. Cette API n’est pas bien définie. nous vous recommandons donc de récupérer les métadonnées de base de données directement à l’aide d’API SQLite standard, telles que la table [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) et le pragma [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) .

Pour plus d’informations, consultez [métadonnées](metadata.md).

## <a name="systemtransactions"></a>System.Transactions

Microsoft. Data. sqlite ne prend pas encore en charge System. transactions. Utilisez à la place des transactions ADO.NET. Pour plus d’informations, consultez [Transactions](transactions.md).

Fournissez des commentaires sur l’absence de prise en charge de System. transactions sur le problème [#13825](https://github.com/dotnet/efcore/issues/13825).

## <a name="data-adapters"></a>Adaptateurs de données

`DbDataAdapter`n’est pas encore implémenté par Microsoft. Data. sqlite. Cela signifie que vous pouvez uniquement utiliser `DataSet` ADO.NET `DataTable` et charger des données sans les mettre à jour.

Utilisez [#13838](https://github.com/dotnet/efcore/issues/13838) de problème pour fournir des commentaires `DbDataAdapter`sur l’implémentation de.

## <a name="output-parameters"></a>Paramètres de sortie

SQLite ne prend pas en charge les paramètres de sortie.

## <a name="positional-parameters"></a>Paramètres positionnels

Microsoft. Data. sqlite prend uniquement en charge les [paramètres](parameters.md)nommés. Les paramètres positionnels ne sont pas pris en charge.

## <a name="stored-procedures"></a>Procédures stockées

SQLite ne prend pas en charge les procédures stockées.

## <a name="isolation-levels"></a>Niveaux d'isolement

Les `Chaos` niveaux `Snapshot` d’isolation et ne sont pas pris en charge dans les transactions sqlite.

## <a name="see-also"></a>Voir aussi

* [Limitations Async](async.md)
* [Types de données](types.md)
* [Transactions](transactions.md)
