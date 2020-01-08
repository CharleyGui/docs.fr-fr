---
title: Limitations de ADO.NET
ms.date: 12/13/2019
description: Décrit certaines des limitations de ADO.NET que vous pouvez rencontrer.
ms.openlocfilehash: b58fd3a9ea324e9c17ad21479e53e45f5982db9d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447089"
---
# <a name="adonet-limitations"></a><span data-ttu-id="7a0eb-103">Limitations de ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7a0eb-103">ADO.NET limitations</span></span>

<span data-ttu-id="7a0eb-104">Microsoft. Data. sqlite fournit des implémentations de nombreuses abstractions ADO.NET, mais il existe certaines limitations.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-104">Microsoft.Data.Sqlite provides implementations of many of the ADO.NET abstractions, but there are some limitations.</span></span>

## <a name="database-schema-information"></a><span data-ttu-id="7a0eb-105">Informations sur le schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="7a0eb-105">Database schema information</span></span>

<span data-ttu-id="7a0eb-106">Les métadonnées relatives aux résultats de la requête sont disponibles à l’aide de la méthode <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-106">Metadata about query results is available using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method.</span></span>

<span data-ttu-id="7a0eb-107">`DbConnection.GetSchema()` n’est pas implémenté.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-107">`DbConnection.GetSchema()` isn't implemented.</span></span> <span data-ttu-id="7a0eb-108">Cette API n’est pas bien définie. nous vous recommandons donc de récupérer les métadonnées de base de données directement à l’aide d’API SQLite standard, telles que la table [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) et le pragma [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) .</span><span class="sxs-lookup"><span data-stu-id="7a0eb-108">This API isn't well-defined, so we recommend retrieving database metadata directly using standard SQLite APIs like the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and the [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA.</span></span>

<span data-ttu-id="7a0eb-109">Pour plus d’informations, consultez [métadonnées](metadata.md).</span><span class="sxs-lookup"><span data-stu-id="7a0eb-109">For more information, see [Metadata](metadata.md).</span></span>

## <a name="systemtransactions"></a><span data-ttu-id="7a0eb-110">System.Transactions</span><span class="sxs-lookup"><span data-stu-id="7a0eb-110">System.Transactions</span></span>

<span data-ttu-id="7a0eb-111">Microsoft. Data. sqlite ne prend pas encore en charge System. transactions.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-111">Microsoft.Data.Sqlite doesn't yet support System.Transactions.</span></span> <span data-ttu-id="7a0eb-112">Utilisez à la place des transactions ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-112">Use ADO.NET transactions instead.</span></span> <span data-ttu-id="7a0eb-113">Pour plus d’informations, consultez [transactions](transactions.md).</span><span class="sxs-lookup"><span data-stu-id="7a0eb-113">For more information, see [Transactions](transactions.md).</span></span>

<span data-ttu-id="7a0eb-114">Fournissez des commentaires sur l’absence de prise en charge de System. transactions sur le problème [#13825](https://github.com/aspnet/EntityFrameworkCore/issues/13825).</span><span class="sxs-lookup"><span data-stu-id="7a0eb-114">Provide feedback about the lack of support for System.Transactions on issue [#13825](https://github.com/aspnet/EntityFrameworkCore/issues/13825).</span></span>

## <a name="data-adapters"></a><span data-ttu-id="7a0eb-115">Adaptateurs de données</span><span class="sxs-lookup"><span data-stu-id="7a0eb-115">Data adapters</span></span>

<span data-ttu-id="7a0eb-116">`DbDataAdapter` n’est pas encore implémenté par Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-116">`DbDataAdapter` isn't yet implemented by Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="7a0eb-117">Cela signifie que vous pouvez uniquement utiliser ADO.NET `DataSet` et `DataTable` pour charger des données et ne pas les mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-117">This means you can only use ADO.NET `DataSet` and `DataTable` to load data and not update it.</span></span>

<span data-ttu-id="7a0eb-118">Utilisez [#13838](https://github.com/aspnet/EntityFrameworkCore/issues/13838) de problème pour fournir des commentaires sur l’implémentation de `DbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-118">Use issue [#13838](https://github.com/aspnet/EntityFrameworkCore/issues/13838) to provide feedback about implementing `DbDataAdapter`.</span></span>

## <a name="output-parameters"></a><span data-ttu-id="7a0eb-119">Paramètres de sortie</span><span class="sxs-lookup"><span data-stu-id="7a0eb-119">Output parameters</span></span>

<span data-ttu-id="7a0eb-120">SQLite ne prend pas en charge les paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-120">SQLite doesn't support output parameters.</span></span>

## <a name="positional-parameters"></a><span data-ttu-id="7a0eb-121">Paramètres positionnels</span><span class="sxs-lookup"><span data-stu-id="7a0eb-121">Positional parameters</span></span>

<span data-ttu-id="7a0eb-122">Microsoft. Data. sqlite prend uniquement en charge les [paramètres](parameters.md)nommés.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-122">Microsoft.Data.Sqlite only supports named [parameters](parameters.md).</span></span> <span data-ttu-id="7a0eb-123">Les paramètres positionnels ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-123">Positional parameters aren't supported.</span></span>

## <a name="stored-procedures"></a><span data-ttu-id="7a0eb-124">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="7a0eb-124">Stored procedures</span></span>

<span data-ttu-id="7a0eb-125">SQLite ne prend pas en charge les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-125">SQLite doesn't support stored procedures.</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="7a0eb-126">Niveaux d'isolement</span><span class="sxs-lookup"><span data-stu-id="7a0eb-126">Isolation levels</span></span>

<span data-ttu-id="7a0eb-127">Les niveaux d’isolation `Chaos` et `Snapshot` ne sont pas pris en charge dans les transactions SQLite.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-127">The `Chaos` and `Snapshot` isolation levels aren't supported in SQLite transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a0eb-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a0eb-128">See also</span></span>

* [<span data-ttu-id="7a0eb-129">Limitations Async</span><span class="sxs-lookup"><span data-stu-id="7a0eb-129">Async limitations</span></span>](async.md)
* [<span data-ttu-id="7a0eb-130">Types de données</span><span class="sxs-lookup"><span data-stu-id="7a0eb-130">Data types</span></span>](types.md)
* [<span data-ttu-id="7a0eb-131">Transactions</span><span class="sxs-lookup"><span data-stu-id="7a0eb-131">Transactions</span></span>](transactions.md)
