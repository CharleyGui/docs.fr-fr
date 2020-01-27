---
title: Versions SQLite personnalisées
ms.date: 12/13/2019
description: Découvrez comment utiliser une version personnalisée de la bibliothèque SQLite native.
ms.openlocfilehash: dd27278c1dbe17b12e5067d04d19043bf259b1e8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746993"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="3180b-103">Versions SQLite personnalisées</span><span class="sxs-lookup"><span data-stu-id="3180b-103">Custom SQLite versions</span></span>

<span data-ttu-id="3180b-104">Microsoft. Data. sqlite est basé sur SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="3180b-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="3180b-105">Vous pouvez utiliser des versions personnalisées de la bibliothèque SQLite native à l’aide d’un bundle ou en configurant un fournisseur SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="3180b-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="3180b-106">Offres groupées</span><span class="sxs-lookup"><span data-stu-id="3180b-106">Bundles</span></span>

<span data-ttu-id="3180b-107">SQLitePCLRaw fournit des packages de bundle qui facilitent l’apport des dépendances appropriées sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="3180b-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="3180b-108">Le package principal Microsoft. Data. sqlite apporte par défaut SQLitePCLRaw. bundle_e_sqlite3.</span><span class="sxs-lookup"><span data-stu-id="3180b-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="3180b-109">Pour utiliser un autre Bundle, installez le package `Microsoft.Data.Sqlite.Core` au lieu du package que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="3180b-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="3180b-110">Les offres groupées sont automatiquement initialisées par Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="3180b-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="3180b-111">Lots</span><span class="sxs-lookup"><span data-stu-id="3180b-111">Bundle</span></span> | <span data-ttu-id="3180b-112">Description</span><span class="sxs-lookup"><span data-stu-id="3180b-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3180b-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="3180b-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="3180b-114">Fournit une version cohérente de SQLite sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="3180b-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="3180b-115">Comprend les extensions d’arborescence FTS4, FTS5, JSON1 et R \*.</span><span class="sxs-lookup"><span data-stu-id="3180b-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="3180b-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3180b-116">This is the default.</span></span> |
| <span data-ttu-id="3180b-117">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="3180b-117">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="3180b-118">Identique à bundle_e_sqlite3, sauf sur iOS où il utilise la bibliothèque SQLite du système.</span><span class="sxs-lookup"><span data-stu-id="3180b-118">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="3180b-119">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="3180b-119">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="3180b-120">Utilise les builds officielles de SQLCipher à partir de zetetic (non inclus).</span><span class="sxs-lookup"><span data-stu-id="3180b-120">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="3180b-121">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="3180b-121">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="3180b-122">Utilise winsqlite3. dll, la bibliothèque SQLite système sur Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3180b-122">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="3180b-123">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="3180b-123">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="3180b-124">Fournit une build Open source non officielle de SQLCipher.</span><span class="sxs-lookup"><span data-stu-id="3180b-124">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="3180b-125">Par exemple, pour utiliser la build Open source non officielle de SQLCipher, utilisez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3180b-125">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="3180b-126">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="3180b-126">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="3180b-127">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3180b-127">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="3180b-128">Fournisseurs SQLitePCLRaw</span><span class="sxs-lookup"><span data-stu-id="3180b-128">SQLitePCLRaw providers</span></span>

<span data-ttu-id="3180b-129">Vous pouvez utiliser votre propre Build de SQLite en tirant parti du package `SQLitePCLRaw.provider.dynamic_cdecl`.</span><span class="sxs-lookup"><span data-stu-id="3180b-129">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="3180b-130">Dans ce cas, vous êtes responsable du déploiement de la bibliothèque native avec votre application.</span><span class="sxs-lookup"><span data-stu-id="3180b-130">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="3180b-131">Notez que les détails du déploiement de bibliothèques natives avec votre application varient considérablement selon la plateforme et le Runtime .NET que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="3180b-131">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="3180b-132">Tout d’abord, vous devez implémenter IGetFunctionPointer.</span><span class="sxs-lookup"><span data-stu-id="3180b-132">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="3180b-133">L’implémentation est relativement trivial sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3180b-133">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="3180b-134">Ensuite, configurez le fournisseur SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="3180b-134">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="3180b-135">Assurez-vous que cette opération est effectuée avant l’utilisation de Microsoft. Data. sqlite dans votre application.</span><span class="sxs-lookup"><span data-stu-id="3180b-135">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="3180b-136">Évitez également d’utiliser un package de Bundle SQLitePCLRaw qui peut remplacer votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3180b-136">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
