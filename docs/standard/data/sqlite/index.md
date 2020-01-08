---
title: Vue d'ensemble de
ms.date: 12/13/2019
description: Vue d’ensemble de Microsoft. Data. sqlite
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447229"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="5fd96-103">Vue d’ensemble de Microsoft. Data. sqlite</span><span class="sxs-lookup"><span data-stu-id="5fd96-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="5fd96-104">Microsoft. Data. sqlite est un fournisseur [ADO.net](../../../framework/data/adonet/index.md) léger pour SQLite.</span><span class="sxs-lookup"><span data-stu-id="5fd96-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="5fd96-105">Le fournisseur [Entity Framework Core](/ef/core/) pour SQLite s’appuie sur cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="5fd96-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="5fd96-106">Toutefois, il peut également être utilisé indépendamment ou avec d’autres bibliothèques d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="5fd96-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="5fd96-107">Installation de</span><span class="sxs-lookup"><span data-stu-id="5fd96-107">Installation</span></span>

<span data-ttu-id="5fd96-108">La dernière version stable est disponible sur [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="5fd96-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="5fd96-109">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="5fd96-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="5fd96-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5fd96-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="5fd96-111">Contrôle</span><span class="sxs-lookup"><span data-stu-id="5fd96-111">Usage</span></span>

<span data-ttu-id="5fd96-112">Cette bibliothèque implémente les abstractions ADO.NET courantes pour les connexions, les commandes, les lecteurs de données, etc.</span><span class="sxs-lookup"><span data-stu-id="5fd96-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="5fd96-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fd96-113">See also</span></span>

* [<span data-ttu-id="5fd96-114">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="5fd96-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="5fd96-115">Informations de référence sur les API</span><span class="sxs-lookup"><span data-stu-id="5fd96-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [<span data-ttu-id="5fd96-116">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="5fd96-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
