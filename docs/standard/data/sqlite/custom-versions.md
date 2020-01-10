---
title: Versions SQLite personnalisées
ms.date: 12/13/2019
description: Découvrez comment utiliser une version personnalisée de la bibliothèque SQLite native.
ms.openlocfilehash: 8a2646138ea9dbecf412a2e8e0e347e2d71a5b0b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447145"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="e98ea-103">Versions SQLite personnalisées</span><span class="sxs-lookup"><span data-stu-id="e98ea-103">Custom SQLite versions</span></span>

<span data-ttu-id="e98ea-104">Microsoft. Data. sqlite est basé sur SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="e98ea-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="e98ea-105">Vous pouvez utiliser des versions personnalisées de la bibliothèque SQLite native à l’aide d’un bundle ou en configurant un fournisseur SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="e98ea-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="e98ea-106">Offres groupées</span><span class="sxs-lookup"><span data-stu-id="e98ea-106">Bundles</span></span>

<span data-ttu-id="e98ea-107">SQLitePCLRaw fournit des packages de bundle qui facilitent l’apport des dépendances appropriées sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="e98ea-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="e98ea-108">Le package principal Microsoft. Data. sqlite apporte par défaut SQLitePCLRaw. bundle_e_sqlite3.</span><span class="sxs-lookup"><span data-stu-id="e98ea-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="e98ea-109">Pour utiliser un autre Bundle, installez le package `Microsoft.Data.Sqlite.Core` au lieu du package que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e98ea-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="e98ea-110">Les offres groupées sont automatiquement initialisées par Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="e98ea-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="e98ea-111">Offre groupée</span><span class="sxs-lookup"><span data-stu-id="e98ea-111">Bundle</span></span> | <span data-ttu-id="e98ea-112">Description</span><span class="sxs-lookup"><span data-stu-id="e98ea-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e98ea-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="e98ea-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="e98ea-114">Fournit une version cohérente de SQLite sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="e98ea-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="e98ea-115">Comprend les FTS4, FTS5, JSON1 et</span><span class="sxs-lookup"><span data-stu-id="e98ea-115">Includes the FTS4, FTS5, JSON1, and</span></span> | <span data-ttu-id="e98ea-116">Extensions d’arborescence R \*.</span><span class="sxs-lookup"><span data-stu-id="e98ea-116">R\*Tree extensions.</span></span> <span data-ttu-id="e98ea-117">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e98ea-117">This is the default.</span></span> |
| <span data-ttu-id="e98ea-118">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="e98ea-118">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="e98ea-119">Identique à bundle_e_sqlite3, sauf sur iOS où il utilise la bibliothèque SQLite du système.</span><span class="sxs-lookup"><span data-stu-id="e98ea-119">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="e98ea-120">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="e98ea-120">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="e98ea-121">Utilise les builds officielles de SQLCipher à partir de zetetic (non inclus).</span><span class="sxs-lookup"><span data-stu-id="e98ea-121">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="e98ea-122">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="e98ea-122">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="e98ea-123">Utilise winsqlite3. dll, la bibliothèque SQLite système sur Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e98ea-123">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="e98ea-124">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="e98ea-124">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="e98ea-125">Fournit une build Open source non officielle de SQLCipher.</span><span class="sxs-lookup"><span data-stu-id="e98ea-125">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="e98ea-126">Par exemple, pour utiliser la build Open source non officielle de SQLCipher, utilisez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="e98ea-126">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="e98ea-127">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="e98ea-127">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="e98ea-128">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e98ea-128">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="e98ea-129">Fournisseurs SQLitePCLRaw</span><span class="sxs-lookup"><span data-stu-id="e98ea-129">SQLitePCLRaw providers</span></span>

<span data-ttu-id="e98ea-130">Vous pouvez utiliser votre propre Build de SQLite en tirant parti du package `SQLitePCLRaw.provider.dynamic_cdecl`.</span><span class="sxs-lookup"><span data-stu-id="e98ea-130">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="e98ea-131">Dans ce cas, vous êtes responsable du déploiement de la bibliothèque native avec votre application.</span><span class="sxs-lookup"><span data-stu-id="e98ea-131">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="e98ea-132">Notez que les détails du déploiement de bibliothèques natives avec votre application varient considérablement selon la plateforme et le Runtime .NET que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="e98ea-132">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="e98ea-133">Tout d’abord, vous devez implémenter IGetFunctionPointer.</span><span class="sxs-lookup"><span data-stu-id="e98ea-133">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="e98ea-134">L’implémentation est relativement trivial sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e98ea-134">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="e98ea-135">Ensuite, configurez le fournisseur SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="e98ea-135">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="e98ea-136">Assurez-vous que cette opération est effectuée avant l’utilisation de Microsoft. Data. sqlite dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e98ea-136">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="e98ea-137">Évitez également d’utiliser un package de Bundle SQLitePCLRaw qui peut remplacer votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e98ea-137">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
