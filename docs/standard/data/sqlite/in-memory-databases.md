---
title: Bases de données en mémoire
ms.date: 12/13/2019
description: Apprenez à utiliser les bases de données SQLite en mémoire.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391206"
---
# <a name="in-memory-databases"></a><span data-ttu-id="ce6f7-103">Bases de données en mémoire</span><span class="sxs-lookup"><span data-stu-id="ce6f7-103">In-memory databases</span></span>

<span data-ttu-id="ce6f7-104">Les bases de données en mémoire SQLite sont des bases de données entièrement stockées dans la mémoire, et non sur disque.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="ce6f7-105">Utilisez le nom de `:memory:` fichier source de données spéciale pour créer une base de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="ce6f7-106">Lorsque la connexion est fermée, la base de données est supprimée.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="ce6f7-107">Lors `:memory:`de l’utilisation, chaque connexion crée sa propre base de données.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="ce6f7-108">Bases de données en mémoire partageables</span><span class="sxs-lookup"><span data-stu-id="ce6f7-108">Shareable in-memory databases</span></span>

<span data-ttu-id="ce6f7-109">Les bases de données en mémoire peuvent `Mode=Memory` `Cache=Shared` être partagées entre plusieurs connexions en utilisant et dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="ce6f7-110">Le `Data Source` mot clé est utilisé pour donner un nom à la base de données mémoire.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="ce6f7-111">Les chaînes de connexion utilisant le même nom accéderont à la même base de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="ce6f7-112">La base de données persiste tant qu’au moins une connexion reste ouverte.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="ce6f7-113">Un [échantillon](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) démontrant cela est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="ce6f7-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
