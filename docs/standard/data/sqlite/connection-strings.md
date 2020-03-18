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
# <a name="connection-strings"></a><span data-ttu-id="09989-103">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="09989-103">Connection strings</span></span>

<span data-ttu-id="09989-104">Une chaîne de connexion est utilisée pour spécifier comment se connecter à la base de données.</span><span class="sxs-lookup"><span data-stu-id="09989-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="09989-105">Les chaînes de connexion dans Microsoft.Data.Sqlite suivent la [syntaxe standard ADO.NET](../../../framework/data/adonet/connection-strings.md) comme une liste de mots clés et de valeurs séparées des semi-remorques.</span><span class="sxs-lookup"><span data-stu-id="09989-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="09989-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="09989-106">Keywords</span></span>

<span data-ttu-id="09989-107">Les mots clés suivants de la chaîne de connexion peuvent être utilisés avec Microsoft.Data.Sqlite :</span><span class="sxs-lookup"><span data-stu-id="09989-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="09989-108">Source de données</span><span class="sxs-lookup"><span data-stu-id="09989-108">Data source</span></span>

<span data-ttu-id="09989-109">Chemin d'accès au fichier de base de données.</span><span class="sxs-lookup"><span data-stu-id="09989-109">The path to the database file.</span></span> <span data-ttu-id="09989-110">*DataSource* (sans espace) et *Filename* sont des alias de ce mot clé.</span><span class="sxs-lookup"><span data-stu-id="09989-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="09989-111">SQLite traite les chemins par rapport à l’annuaire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="09989-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="09989-112">Des chemins absolus peuvent également être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="09989-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="09989-113">En **cas de vide,** SQLite crée une base de données temporaire sur disque qui est supprimée lorsque la connexion est fermée.</span><span class="sxs-lookup"><span data-stu-id="09989-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="09989-114">Si `:memory:`, une base de données en mémoire est utilisée.</span><span class="sxs-lookup"><span data-stu-id="09989-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="09989-115">Pour plus d’informations, consultez [les bases de données In-Memory](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="09989-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="09989-116">Les chemins qui `|DataDirectory|` commencent par la chaîne de substitution sont traités de la même façon que les chemins relatifs.</span><span class="sxs-lookup"><span data-stu-id="09989-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="09989-117">Si vous êtes défini, des chemins sont réalisés par rapport à la valeur de propriété du domaine d’application DataDirectory.</span><span class="sxs-lookup"><span data-stu-id="09989-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="09989-118">Ce mot clé prend également en charge [URI Filenames](https://www.sqlite.org/uri.html).</span><span class="sxs-lookup"><span data-stu-id="09989-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="09989-119">Mode</span><span class="sxs-lookup"><span data-stu-id="09989-119">Mode</span></span>

<span data-ttu-id="09989-120">Le mode de connexion.</span><span class="sxs-lookup"><span data-stu-id="09989-120">The connection mode.</span></span>

| <span data-ttu-id="09989-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="09989-121">Value</span></span>           | <span data-ttu-id="09989-122">Description</span><span class="sxs-lookup"><span data-stu-id="09989-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="09989-123">LireWriteCreate</span><span class="sxs-lookup"><span data-stu-id="09989-123">ReadWriteCreate</span></span> | <span data-ttu-id="09989-124">Ouvre la base de données pour la lecture et l’écriture, et la crée si elle n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="09989-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="09989-125">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="09989-125">This is the default.</span></span> |
| <span data-ttu-id="09989-126">Lecture/écriture</span><span class="sxs-lookup"><span data-stu-id="09989-126">ReadWrite</span></span>       | <span data-ttu-id="09989-127">Ouvre la base de données pour la lecture et l’écriture.</span><span class="sxs-lookup"><span data-stu-id="09989-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="09989-128">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="09989-128">ReadOnly</span></span>        | <span data-ttu-id="09989-129">Ouvre la base de données en mode lecture uniquement.</span><span class="sxs-lookup"><span data-stu-id="09989-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="09989-130">Mémoire</span><span class="sxs-lookup"><span data-stu-id="09989-130">Memory</span></span>          | <span data-ttu-id="09989-131">Ouvre une base de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="09989-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="09989-132">Cache</span><span class="sxs-lookup"><span data-stu-id="09989-132">Cache</span></span>

<span data-ttu-id="09989-133">Le mode de mise en cache utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="09989-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="09989-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="09989-134">Value</span></span>   | <span data-ttu-id="09989-135">Description</span><span class="sxs-lookup"><span data-stu-id="09989-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="09989-136">Default</span><span class="sxs-lookup"><span data-stu-id="09989-136">Default</span></span> | <span data-ttu-id="09989-137">Utilise le mode par défaut de la bibliothèque SQLite sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="09989-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="09989-138">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="09989-138">This is the default.</span></span>                   |
| <span data-ttu-id="09989-139">Privé</span><span class="sxs-lookup"><span data-stu-id="09989-139">Private</span></span> | <span data-ttu-id="09989-140">Chaque connexion utilise un cache privé.</span><span class="sxs-lookup"><span data-stu-id="09989-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="09989-141">Partagé</span><span class="sxs-lookup"><span data-stu-id="09989-141">Shared</span></span>  | <span data-ttu-id="09989-142">Les connexions partagent un cache.</span><span class="sxs-lookup"><span data-stu-id="09989-142">Connections share a cache.</span></span> <span data-ttu-id="09989-143">Ce mode peut modifier le comportement des transactions et du verrouillage de la table.</span><span class="sxs-lookup"><span data-stu-id="09989-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="09989-144">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="09989-144">Password</span></span>

<span data-ttu-id="09989-145">Clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="09989-145">The encryption key.</span></span> <span data-ttu-id="09989-146">Lorsqu’il `PRAGMA key` est spécifié, est envoyé immédiatement après l’ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="09989-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="09989-147">Mot de passe n’a aucun effet lorsque le chiffrement n’est pas pris en charge par la bibliothèque SQLite indigène.</span><span class="sxs-lookup"><span data-stu-id="09989-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="09989-148">Clés étrangères</span><span class="sxs-lookup"><span data-stu-id="09989-148">Foreign Keys</span></span>

<span data-ttu-id="09989-149">Une valeur indiquant s’il faut permettre des contraintes clés à l’étranger.</span><span class="sxs-lookup"><span data-stu-id="09989-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="09989-150">Valeur</span><span class="sxs-lookup"><span data-stu-id="09989-150">Value</span></span>   | <span data-ttu-id="09989-151">Description</span><span class="sxs-lookup"><span data-stu-id="09989-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="09989-152">True</span><span class="sxs-lookup"><span data-stu-id="09989-152">True</span></span>    | <span data-ttu-id="09989-153">Envoie `PRAGMA foreign_keys = 1` immédiatement après l’ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="09989-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="09989-154">False</span><span class="sxs-lookup"><span data-stu-id="09989-154">False</span></span>   | <span data-ttu-id="09989-155">Envoie `PRAGMA foreign_keys = 0` immédiatement après l’ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="09989-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="09989-156">(empty)</span><span class="sxs-lookup"><span data-stu-id="09989-156">(empty)</span></span> | <span data-ttu-id="09989-157">N’envoie `PRAGMA foreign_keys`pas .</span><span class="sxs-lookup"><span data-stu-id="09989-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="09989-158">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="09989-158">This is the default.</span></span> |

<span data-ttu-id="09989-159">Il n’est pas nécessaire de permettre des clés étrangères si, comme dans e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS a été utilisé pour compiler la bibliothèque SQLite indigène.</span><span class="sxs-lookup"><span data-stu-id="09989-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="09989-160">Déclencheurs récursifs</span><span class="sxs-lookup"><span data-stu-id="09989-160">Recursive triggers</span></span>

<span data-ttu-id="09989-161">Une valeur qui indique s’il faut activer les déclencheurs récursifs.</span><span class="sxs-lookup"><span data-stu-id="09989-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="09989-162">Valeur</span><span class="sxs-lookup"><span data-stu-id="09989-162">Value</span></span> | <span data-ttu-id="09989-163">Description</span><span class="sxs-lookup"><span data-stu-id="09989-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="09989-164">True</span><span class="sxs-lookup"><span data-stu-id="09989-164">True</span></span>  | <span data-ttu-id="09989-165">Envoie `PRAGMA recursive_triggers` immédiatement après l’ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="09989-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="09989-166">False</span><span class="sxs-lookup"><span data-stu-id="09989-166">False</span></span> | <span data-ttu-id="09989-167">N’envoie `PRAGMA recursive_triggers`pas .</span><span class="sxs-lookup"><span data-stu-id="09989-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="09989-168">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="09989-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="09989-169">Constructeur de cordes de connexion</span><span class="sxs-lookup"><span data-stu-id="09989-169">Connection string builder</span></span>

<span data-ttu-id="09989-170">Vous pouvez <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> utiliser comme un moyen fortement tapé de créer des chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="09989-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="09989-171">Il peut également être utilisé pour prévenir les attaques d’injection de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="09989-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="09989-172">Exemples</span><span class="sxs-lookup"><span data-stu-id="09989-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="09989-173">De base</span><span class="sxs-lookup"><span data-stu-id="09989-173">Basic</span></span>

<span data-ttu-id="09989-174">Une chaîne de connexion de base avec un cache partagé pour une concurrence améliorée.</span><span class="sxs-lookup"><span data-stu-id="09989-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="09989-175">Chiffré</span><span class="sxs-lookup"><span data-stu-id="09989-175">Encrypted</span></span>

<span data-ttu-id="09989-176">Une base de données cryptée.</span><span class="sxs-lookup"><span data-stu-id="09989-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="09989-177">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="09989-177">Read-only</span></span>

<span data-ttu-id="09989-178">Une base de données de lecture uniquement qui ne peut pas être modifiée par l’application.</span><span class="sxs-lookup"><span data-stu-id="09989-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="09989-179">En mémoire</span><span class="sxs-lookup"><span data-stu-id="09989-179">In-memory</span></span>

<span data-ttu-id="09989-180">Une base de données privée et en mémoire.</span><span class="sxs-lookup"><span data-stu-id="09989-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="09989-181">Sharable dans la mémoire</span><span class="sxs-lookup"><span data-stu-id="09989-181">Sharable in-memory</span></span>

<span data-ttu-id="09989-182">Une base de données sharable, dans la mémoire identifiée par le nom *Sharable*.</span><span class="sxs-lookup"><span data-stu-id="09989-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="09989-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09989-183">See also</span></span>

* [<span data-ttu-id="09989-184">Chaînes de connexion dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09989-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="09989-185">Bases de données in-Memory</span><span class="sxs-lookup"><span data-stu-id="09989-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="09989-186">Transactions</span><span class="sxs-lookup"><span data-stu-id="09989-186">Transactions</span></span>](transactions.md)
