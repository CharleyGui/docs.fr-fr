---
title: Transactions
ms.date: 09/08/2020
description: Découvrez comment utiliser des transactions.
ms.openlocfilehash: 50c4cd1023eac892cafc3ae4395e9168bd8e9f36
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678860"
---
# <a name="transactions"></a>Transactions

Les transactions vous permettent de regrouper plusieurs instructions SQL en une seule unité de travail qui est validée dans la base de données comme une seule unité atomique. Si une instruction de la transaction échoue, les modifications apportées par les instructions précédentes peuvent être annulées. L’état initial de la base de données au moment du démarrage de la transaction est préservé. L’utilisation d’une transaction peut également améliorer les performances sur SQLite lorsque de nombreuses modifications sont apportées à la base de données en même temps.

## <a name="concurrency"></a>Accès concurrentiel

Dans SQLite, une seule transaction peut avoir des modifications en attente dans la base de données à la fois. Pour cette raison, les appels à <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> et aux `Execute` méthodes sur <xref:Microsoft.Data.Sqlite.SqliteCommand> peuvent expirer si une autre transaction prend trop de temps pour s’exécuter.

Pour plus d’informations sur le verrouillage, les nouvelles tentatives et les délais d’attente, consultez [Erreurs de base de données](database-errors.md).

## <a name="isolation-levels"></a>Niveaux d'isolement

Les transactions sont **sérialisables** par défaut dans sqlite. Ce niveau d’isolation garantit que toutes les modifications apportées dans une transaction sont complètement isolées. Les autres instructions exécutées en dehors de la transaction ne sont pas affectées par les modifications de la transaction.

SQLite prend également en charge la **lecture non validée** lors de l’utilisation d’un cache partagé. Ce niveau autorise les lectures erronées, les lectures non reproductibles et les fantômes :

- Une *lecture incorrecte* se produit lorsque des modifications en attente dans une transaction sont retournées par une requête en dehors de la transaction, mais que les modifications de la transaction sont annulées. Les résultats contiennent des données qui n’ont jamais été réellement validées dans la base de données.

- Une *lecture non renouvelable* se produit lorsqu’une transaction interroge la même ligne à deux reprises, mais les résultats sont différents parce qu’ils ont été modifiés entre les deux requêtes par une autre transaction.

- Les *fantômes* sont des lignes qui ont été modifiées ou ajoutées pour respecter la clause WHERE d’une requête au cours d’une transaction. Si elle est autorisée, la même requête peut retourner des lignes différentes lorsqu’elle est exécutée deux fois dans la même transaction.

Microsoft. Data. sqlite traite la valeur IsolationLevel transmise à <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> comme un niveau minimal. Le niveau d’isolation réel sera promu en lecture non validée ou sérialisable.

Le code suivant simule une lecture incorrecte. Notez que la chaîne de connexion doit inclure `Cache=Shared` .

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]

## <a name="deferred-transactions"></a>Transactions différées

À compter de Microsoft. Data. SQLite version 5,0, les transactions peuvent être différées. Cela diffère la création de la transaction réelle dans la base de données jusqu’à ce que la première commande soit exécutée. Cela entraîne également la mise à niveau progressive de la transaction d’une transaction de lecture vers une transaction d’écriture en fonction des besoins de ses commandes. Cela peut être utile pour permettre l’accès simultané à la base de données pendant la transaction.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DeferredTransactionSample/Program.cs?name=snippet_DeferredTransaction)]

> [!WARNING]
> Les commandes à l’intérieur d’une transaction différée peuvent échouer si elles provoquent la mise à niveau de la transaction d’une transaction de lecture vers une transaction d’écriture alors que la base de données est verrouillée. Dans ce cas, l’application doit retenter l’intégralité de la transaction.
