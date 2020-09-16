---
title: Chaînes de connexion
ms.date: 12/13/2019
description: Les mots clés et les valeurs de chaîne de connexion pris en charge.
ms.openlocfilehash: 3c50b31689abf6d47aa8f83a6f6f755bcfec0ea3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555391"
---
# <a name="connection-strings"></a><span data-ttu-id="2b5d5-103">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="2b5d5-103">Connection strings</span></span>

<span data-ttu-id="2b5d5-104">Une chaîne de connexion est utilisée pour spécifier la manière de se connecter à la base de données.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="2b5d5-105">Les chaînes de connexion dans Microsoft. Data. sqlite suivent la [syntaxe ADO.net](../../../framework/data/adonet/connection-strings.md) standard sous la forme d’une liste de mots clés et de valeurs séparées par des points-virgules.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="2b5d5-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2b5d5-106">Keywords</span></span>

<span data-ttu-id="2b5d5-107">Les mots clés de chaîne de connexion suivants peuvent être utilisés avec Microsoft. Data. sqlite :</span><span class="sxs-lookup"><span data-stu-id="2b5d5-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="2b5d5-108">Source de données</span><span class="sxs-lookup"><span data-stu-id="2b5d5-108">Data source</span></span>

<span data-ttu-id="2b5d5-109">Chemin d'accès au fichier de base de données.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-109">The path to the database file.</span></span> <span data-ttu-id="2b5d5-110">*DataSource* (sans espace) et *filename* sont des alias de ce mot clé.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="2b5d5-111">SQLite traite les chemins d’accès par rapport au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="2b5d5-112">Vous pouvez également spécifier des chemins d’accès absolus.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="2b5d5-113">S’il est **vide**, SQLite crée une base de données sur disque temporaire qui est supprimée lorsque la connexion est fermée.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="2b5d5-114">Si `:memory:` , une base de données en mémoire est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="2b5d5-115">Pour plus d’informations, consultez [bases de données en mémoire](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="2b5d5-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="2b5d5-116">Les chemins d’accès qui commencent par la `|DataDirectory|` chaîne de substitution sont traités de la même façon que les chemins d’accès relatifs.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="2b5d5-117">Si cette valeur est définie, les chemins d’accès sont définis par rapport à la valeur de la propriété de domaine d’application DataDirectory.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="2b5d5-118">Ce mot clé prend également en charge les noms de fichiers [URI](https://www.sqlite.org/uri.html).</span><span class="sxs-lookup"><span data-stu-id="2b5d5-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="2b5d5-119">Mode</span><span class="sxs-lookup"><span data-stu-id="2b5d5-119">Mode</span></span>

<span data-ttu-id="2b5d5-120">Mode de connexion.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-120">The connection mode.</span></span>

| <span data-ttu-id="2b5d5-121">Value</span><span class="sxs-lookup"><span data-stu-id="2b5d5-121">Value</span></span>           | <span data-ttu-id="2b5d5-122">Description</span><span class="sxs-lookup"><span data-stu-id="2b5d5-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="2b5d5-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="2b5d5-123">ReadWriteCreate</span></span> | <span data-ttu-id="2b5d5-124">Ouvre la base de données pour la lecture et l’écriture, et la crée si elle n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="2b5d5-125">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-125">This is the default.</span></span> |
| <span data-ttu-id="2b5d5-126">Lecture/écriture</span><span class="sxs-lookup"><span data-stu-id="2b5d5-126">ReadWrite</span></span>       | <span data-ttu-id="2b5d5-127">Ouvre la base de données pour la lecture et l’écriture.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="2b5d5-128">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="2b5d5-128">ReadOnly</span></span>        | <span data-ttu-id="2b5d5-129">Ouvre la base de données en mode lecture seule.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="2b5d5-130">Mémoire</span><span class="sxs-lookup"><span data-stu-id="2b5d5-130">Memory</span></span>          | <span data-ttu-id="2b5d5-131">Ouvre une base de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="2b5d5-132">Cache</span><span class="sxs-lookup"><span data-stu-id="2b5d5-132">Cache</span></span>

<span data-ttu-id="2b5d5-133">Mode de mise en cache utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="2b5d5-134">Value</span><span class="sxs-lookup"><span data-stu-id="2b5d5-134">Value</span></span>   | <span data-ttu-id="2b5d5-135">Description</span><span class="sxs-lookup"><span data-stu-id="2b5d5-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="2b5d5-136">Default</span><span class="sxs-lookup"><span data-stu-id="2b5d5-136">Default</span></span> | <span data-ttu-id="2b5d5-137">Utilise le mode par défaut de la bibliothèque SQLite sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="2b5d5-138">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-138">This is the default.</span></span>                   |
| <span data-ttu-id="2b5d5-139">Private</span><span class="sxs-lookup"><span data-stu-id="2b5d5-139">Private</span></span> | <span data-ttu-id="2b5d5-140">Chaque connexion utilise un cache privé.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="2b5d5-141">Partagé</span><span class="sxs-lookup"><span data-stu-id="2b5d5-141">Shared</span></span>  | <span data-ttu-id="2b5d5-142">Les connexions partagent un cache.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-142">Connections share a cache.</span></span> <span data-ttu-id="2b5d5-143">Ce mode peut modifier le comportement du verrouillage de la transaction et de la table.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="2b5d5-144">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="2b5d5-144">Password</span></span>

<span data-ttu-id="2b5d5-145">Clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-145">The encryption key.</span></span> <span data-ttu-id="2b5d5-146">Lorsqu' `PRAGMA key` il est spécifié, est envoyé immédiatement après l’ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="2b5d5-147">Le mot de passe n’a aucun effet lorsque le chiffrement n’est pas pris en charge par la bibliothèque SQLite native.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="2b5d5-148">Clés étrangères</span><span class="sxs-lookup"><span data-stu-id="2b5d5-148">Foreign Keys</span></span>

<span data-ttu-id="2b5d5-149">Valeur indiquant s’il faut activer les contraintes de clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="2b5d5-150">Value</span><span class="sxs-lookup"><span data-stu-id="2b5d5-150">Value</span></span>   | <span data-ttu-id="2b5d5-151">Description</span><span class="sxs-lookup"><span data-stu-id="2b5d5-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="2b5d5-152">True</span><span class="sxs-lookup"><span data-stu-id="2b5d5-152">True</span></span>    | <span data-ttu-id="2b5d5-153">Envoie `PRAGMA foreign_keys = 1` immédiatement après l’ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="2b5d5-154">Faux</span><span class="sxs-lookup"><span data-stu-id="2b5d5-154">False</span></span>   | <span data-ttu-id="2b5d5-155">Envoie `PRAGMA foreign_keys = 0` immédiatement après l’ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="2b5d5-156">(empty)</span><span class="sxs-lookup"><span data-stu-id="2b5d5-156">(empty)</span></span> | <span data-ttu-id="2b5d5-157">N’envoie pas `PRAGMA foreign_keys` .</span><span class="sxs-lookup"><span data-stu-id="2b5d5-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="2b5d5-158">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-158">This is the default.</span></span> |

<span data-ttu-id="2b5d5-159">Il n’est pas nécessaire d’activer les clés étrangères si, comme dans e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS a été utilisé pour compiler la bibliothèque SQLite native.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="2b5d5-160">Déclencheurs récursifs</span><span class="sxs-lookup"><span data-stu-id="2b5d5-160">Recursive triggers</span></span>

<span data-ttu-id="2b5d5-161">Valeur qui indique s’il faut activer les déclencheurs récursifs.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="2b5d5-162">Value</span><span class="sxs-lookup"><span data-stu-id="2b5d5-162">Value</span></span> | <span data-ttu-id="2b5d5-163">Description</span><span class="sxs-lookup"><span data-stu-id="2b5d5-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="2b5d5-164">True</span><span class="sxs-lookup"><span data-stu-id="2b5d5-164">True</span></span>  | <span data-ttu-id="2b5d5-165">Envoie `PRAGMA recursive_triggers` immédiatement après l’ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="2b5d5-166">Faux</span><span class="sxs-lookup"><span data-stu-id="2b5d5-166">False</span></span> | <span data-ttu-id="2b5d5-167">N’envoie pas `PRAGMA recursive_triggers` .</span><span class="sxs-lookup"><span data-stu-id="2b5d5-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="2b5d5-168">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="2b5d5-169">Générateur de chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="2b5d5-169">Connection string builder</span></span>

<span data-ttu-id="2b5d5-170">Vous pouvez utiliser <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> comme un moyen fortement typé de créer des chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="2b5d5-171">Il peut également être utilisé pour empêcher les attaques par injection de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="2b5d5-172">Exemples</span><span class="sxs-lookup"><span data-stu-id="2b5d5-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="2b5d5-173">Basic</span><span class="sxs-lookup"><span data-stu-id="2b5d5-173">Basic</span></span>

<span data-ttu-id="2b5d5-174">Chaîne de connexion de base avec un cache partagé pour améliorer la concurrence.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="2b5d5-175">Chiffré</span><span class="sxs-lookup"><span data-stu-id="2b5d5-175">Encrypted</span></span>

<span data-ttu-id="2b5d5-176">Base de données chiffrée.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-176">An encrypted database.</span></span>

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="2b5d5-177">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="2b5d5-177">Read-only</span></span>

<span data-ttu-id="2b5d5-178">Base de données en lecture seule qui ne peut pas être modifiée par l’application.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-178">A read-only database that cannot be modified by the app.</span></span>

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="2b5d5-179">En mémoire</span><span class="sxs-lookup"><span data-stu-id="2b5d5-179">In-memory</span></span>

<span data-ttu-id="2b5d5-180">Base de données en mémoire privée.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-180">A private, in-memory database.</span></span>

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="2b5d5-181">Partage en mémoire</span><span class="sxs-lookup"><span data-stu-id="2b5d5-181">Sharable in-memory</span></span>

<span data-ttu-id="2b5d5-182">Base de données en mémoire partageable identifiée par le nom *partageable*.</span><span class="sxs-lookup"><span data-stu-id="2b5d5-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="2b5d5-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b5d5-183">See also</span></span>

* [<span data-ttu-id="2b5d5-184">Chaînes de connexion dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2b5d5-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="2b5d5-185">Bases de données en mémoire</span><span class="sxs-lookup"><span data-stu-id="2b5d5-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="2b5d5-186">Transactions</span><span class="sxs-lookup"><span data-stu-id="2b5d5-186">Transactions</span></span>](transactions.md)
