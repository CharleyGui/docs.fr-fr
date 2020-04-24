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
# <a name="database-errors"></a><span data-ttu-id="086a4-103">Erreurs de base de données</span><span class="sxs-lookup"><span data-stu-id="086a4-103">Database errors</span></span>

<span data-ttu-id="086a4-104"><xref:Microsoft.Data.Sqlite.SqliteException>est levée lorsqu’une erreur SQLite est rencontrée.</span><span class="sxs-lookup"><span data-stu-id="086a4-104"><xref:Microsoft.Data.Sqlite.SqliteException> is thrown when a SQLite error is encountered.</span></span> <span data-ttu-id="086a4-105">Le message est fourni par SQLite.</span><span class="sxs-lookup"><span data-stu-id="086a4-105">The message is provided by SQLite.</span></span> <span data-ttu-id="086a4-106">Les `SqliteErrorCode` propriétés `SqliteExtendedErrorCode` et contiennent le [Code de résultat](https://www.sqlite.org/rescode.html) SQLite de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="086a4-106">The `SqliteErrorCode` and `SqliteExtendedErrorCode` properties contain the SQLite [result code](https://www.sqlite.org/rescode.html) of the error.</span></span>

<span data-ttu-id="086a4-107">Des erreurs peuvent se produire chaque fois que Microsoft. Data. sqlite interagit avec la bibliothèque SQLite native.</span><span class="sxs-lookup"><span data-stu-id="086a4-107">Errors may be encountered any time the Microsoft.Data.Sqlite interacts with the native SQLite library.</span></span> <span data-ttu-id="086a4-108">La liste suivante présente les scénarios courants dans lesquels des erreurs peuvent se produire :</span><span class="sxs-lookup"><span data-stu-id="086a4-108">The following list shows the common scenarios where errors can occur:</span></span>

* <span data-ttu-id="086a4-109">Ouverture d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="086a4-109">Opening a connection.</span></span>
* <span data-ttu-id="086a4-110">Début d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="086a4-110">Beginning a transaction.</span></span>
* <span data-ttu-id="086a4-111">Exécution d'une commande.</span><span class="sxs-lookup"><span data-stu-id="086a4-111">Executing a command.</span></span>
* <span data-ttu-id="086a4-112">Appel de <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span><span class="sxs-lookup"><span data-stu-id="086a4-112">Calling <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span></span>

<span data-ttu-id="086a4-113">Réfléchissez à la manière dont votre application gère ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="086a4-113">Consider carefully how your app will handle these errors.</span></span>

## <a name="locking-retries-and-timeouts"></a><span data-ttu-id="086a4-114">Verrouillage, nouvelles tentatives et délais d’expiration</span><span class="sxs-lookup"><span data-stu-id="086a4-114">Locking, retries, and timeouts</span></span>

<span data-ttu-id="086a4-115">SQLite est agressif lorsqu’il s’agit de verrouiller des tables et des fichiers de base de données.</span><span class="sxs-lookup"><span data-stu-id="086a4-115">SQLite is aggressive when it comes to locking tables and database files.</span></span> <span data-ttu-id="086a4-116">Si votre application active un accès simultané à la base de données, vous rencontrerez probablement des erreurs de disponibilité et de verrouillage.</span><span class="sxs-lookup"><span data-stu-id="086a4-116">If your app enables any concurrent database access, you'll likely encounter busy and locked errors.</span></span> <span data-ttu-id="086a4-117">Vous pouvez atténuer de nombreuses erreurs en utilisant un [cache partagé](connection-strings.md#cache) et une [journalisation avec écriture anticipée](async.md).</span><span class="sxs-lookup"><span data-stu-id="086a4-117">You can mitigate many errors by using a [shared cache](connection-strings.md#cache) and [write-ahead logging](async.md).</span></span>

<span data-ttu-id="086a4-118">Chaque fois que Microsoft. Data. sqlite rencontre une erreur occupée ou verrouillée, il réessaie automatiquement jusqu’à ce qu’il aboutisse ou que le délai d’attente de la commande soit atteint.</span><span class="sxs-lookup"><span data-stu-id="086a4-118">Whenever Microsoft.Data.Sqlite encounters a busy or locked error, it will automatically retry until it succeeds or the command timeout is reached.</span></span>

<span data-ttu-id="086a4-119">Vous pouvez augmenter le délai d’expiration de la <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>commande en définissant.</span><span class="sxs-lookup"><span data-stu-id="086a4-119">You can increase the timeout of command by setting <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span></span> <span data-ttu-id="086a4-120">Le délai d’attente par défaut est de 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="086a4-120">The default timeout is 30 seconds.</span></span> <span data-ttu-id="086a4-121">La valeur signifie `0` qu’il n’y A pas de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="086a4-121">A value of `0` means no timeout.</span></span>

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

<span data-ttu-id="086a4-122">Microsoft. Data. sqlite doit parfois créer un objet de commande implicite.</span><span class="sxs-lookup"><span data-stu-id="086a4-122">Microsoft.Data.Sqlite sometimes needs to create an implicit command object.</span></span> <span data-ttu-id="086a4-123">Par exemple, pendant BeginTransaction.</span><span class="sxs-lookup"><span data-stu-id="086a4-123">For example, during BeginTransaction.</span></span> <span data-ttu-id="086a4-124">Pour définir le délai d’expiration de ces commandes <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>, utilisez.</span><span class="sxs-lookup"><span data-stu-id="086a4-124">To set the timeout for these commands, use <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span></span>

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a><span data-ttu-id="086a4-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="086a4-125">See also</span></span>

* [<span data-ttu-id="086a4-126">Codes d’erreur SQLite</span><span class="sxs-lookup"><span data-stu-id="086a4-126">SQLite Error Codes</span></span>](https://www.sqlite.org/rescode.html)
* [<span data-ttu-id="086a4-127">Verrouillage de fichier dans SQLite</span><span class="sxs-lookup"><span data-stu-id="086a4-127">File Locking In SQLite</span></span>](https://www.sqlite.org/lockingv3.html)
* [<span data-ttu-id="086a4-128">Mode de cache partagé</span><span class="sxs-lookup"><span data-stu-id="086a4-128">Shared-Cache Mode</span></span>](https://www.sqlite.org/sharedcache.html)
* [<span data-ttu-id="086a4-129">Journalisation avec écriture anticipée</span><span class="sxs-lookup"><span data-stu-id="086a4-129">Write-Ahead Logging</span></span>](https://www.sqlite.org/wal.html)
