---
title: Vue d’ensemble
ms.date: 12/13/2019
description: Vue d’ensemble de Microsoft. Data. sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543597"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="d6442-103">Vue d’ensemble de Microsoft. Data. sqlite</span><span class="sxs-lookup"><span data-stu-id="d6442-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="d6442-104">Microsoft. Data. sqlite est un fournisseur [ADO.net](../../../framework/data/adonet/index.md) léger pour SQLite.</span><span class="sxs-lookup"><span data-stu-id="d6442-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="d6442-105">Le fournisseur [Entity Framework Core](/ef/core/) pour SQLite s’appuie sur cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d6442-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="d6442-106">Toutefois, il peut également être utilisé indépendamment ou avec d’autres bibliothèques d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="d6442-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="d6442-107">Installation</span><span class="sxs-lookup"><span data-stu-id="d6442-107">Installation</span></span>

<span data-ttu-id="d6442-108">La dernière version stable est disponible sur [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="d6442-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="d6442-109">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6442-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="d6442-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d6442-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="d6442-111">Usage</span><span class="sxs-lookup"><span data-stu-id="d6442-111">Usage</span></span>

<span data-ttu-id="d6442-112">Cette bibliothèque implémente les abstractions ADO.NET courantes pour les connexions, les commandes, les lecteurs de données, etc.</span><span class="sxs-lookup"><span data-stu-id="d6442-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="d6442-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6442-113">See also</span></span>

* [<span data-ttu-id="d6442-114">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="d6442-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="d6442-115">Référence sur l’API</span><span class="sxs-lookup"><span data-stu-id="d6442-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0)
* [<span data-ttu-id="d6442-116">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="d6442-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
