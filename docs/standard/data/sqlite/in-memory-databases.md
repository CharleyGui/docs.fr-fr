---
title: Bases de données en mémoire
ms.date: 12/13/2019
description: Découvrez comment utiliser les bases de données SQLite en mémoire.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391206"
---
# <a name="in-memory-databases"></a><span data-ttu-id="9d30a-103">Bases de données en mémoire</span><span class="sxs-lookup"><span data-stu-id="9d30a-103">In-memory databases</span></span>

<span data-ttu-id="9d30a-104">Les bases de données en mémoire SQLite sont stockées entièrement en mémoire, et non sur le disque.</span><span class="sxs-lookup"><span data-stu-id="9d30a-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="9d30a-105">Utilisez le nom de fichier `:memory:` de la source de données spéciale pour créer une base de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="9d30a-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="9d30a-106">Lorsque la connexion est fermée, la base de données est supprimée.</span><span class="sxs-lookup"><span data-stu-id="9d30a-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="9d30a-107">Lors de `:memory:`l’utilisation de, chaque connexion crée sa propre base de données.</span><span class="sxs-lookup"><span data-stu-id="9d30a-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="9d30a-108">Bases de données en mémoire partageables</span><span class="sxs-lookup"><span data-stu-id="9d30a-108">Shareable in-memory databases</span></span>

<span data-ttu-id="9d30a-109">Les bases de données en mémoire peuvent être partagées entre plusieurs connexions `Mode=Memory` à `Cache=Shared` l’aide de et dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="9d30a-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="9d30a-110">Le `Data Source` mot clé est utilisé pour attribuer un nom à la base de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="9d30a-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="9d30a-111">Les chaînes de connexion qui utilisent le même nom accèdent à la même base de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="9d30a-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="9d30a-112">La base de données est conservée tant qu’au moins une connexion à celle-ci reste ouverte.</span><span class="sxs-lookup"><span data-stu-id="9d30a-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="9d30a-113">Un [exemple](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) illustrant cette fonction est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="9d30a-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
