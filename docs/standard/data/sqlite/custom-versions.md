---
title: Versions SQLite personnalisées
ms.date: 05/14/2020
description: Découvrez comment utiliser une version personnalisée de la bibliothèque SQLite native.
ms.openlocfilehash: 15db10db26bc7c5017313ca020a0e1e528ba207a
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83440835"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="0ba05-103">Versions SQLite personnalisées</span><span class="sxs-lookup"><span data-stu-id="0ba05-103">Custom SQLite versions</span></span>

<span data-ttu-id="0ba05-104">`Microsoft.Data.Sqlite`repose sur `SQLitePCLRaw` .</span><span class="sxs-lookup"><span data-stu-id="0ba05-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="0ba05-105">Vous pouvez utiliser des versions personnalisées de la bibliothèque SQLite native à l’aide d’un bundle ou en configurant un `SQLitePCLRaw` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0ba05-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="0ba05-106">Offres groupées</span><span class="sxs-lookup"><span data-stu-id="0ba05-106">Bundles</span></span>

<span data-ttu-id="0ba05-107">`SQLitePCLRaw`fournit des packages de Bundle basés sur la commodité, qui facilitent l’apport des dépendances appropriées sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="0ba05-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="0ba05-108">Le `Microsoft.Data.Sqlite` package principal est intégré `SQLitePCLRaw.bundle_e_sqlite3` par défaut.</span><span class="sxs-lookup"><span data-stu-id="0ba05-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="0ba05-109">Pour utiliser un autre Bundle, installez le `Microsoft.Data.Sqlite.Core` package à la place du package que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="0ba05-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="0ba05-110">Les offres groupées sont automatiquement initialisées par `Microsoft.Data.Sqlite` .</span><span class="sxs-lookup"><span data-stu-id="0ba05-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="0ba05-111">Bundle</span><span class="sxs-lookup"><span data-stu-id="0ba05-111">Bundle</span></span> | <span data-ttu-id="0ba05-112">Description</span><span class="sxs-lookup"><span data-stu-id="0ba05-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="0ba05-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="0ba05-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="0ba05-114">Fournit une version cohérente de SQLite sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="0ba05-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="0ba05-115">Comprend les extensions d’arborescence FTS4, FTS5, JSON1 et R \*.</span><span class="sxs-lookup"><span data-stu-id="0ba05-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="0ba05-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0ba05-116">This is the default.</span></span> |
| [<span data-ttu-id="0ba05-117">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="0ba05-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="0ba05-118">Fournit une build Open source non officielle de `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="0ba05-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="0ba05-119">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="0ba05-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="0ba05-120">Identique à `bundle_e_sqlite3` , sauf sur iOS où il utilise la bibliothèque SQLite du système.</span><span class="sxs-lookup"><span data-stu-id="0ba05-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="0ba05-121">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="0ba05-121">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="0ba05-122">Utilise `winsqlite3.dll` , la bibliothèque SQLite système sur Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0ba05-122">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="0ba05-123">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="0ba05-123">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="0ba05-124">Utilise les `SQLCipher` Builds officielles de zetetic (non inclus).</span><span class="sxs-lookup"><span data-stu-id="0ba05-124">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="0ba05-125">Par exemple, pour utiliser la build Open source non officielle de, `SQLCipher` Utilisez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="0ba05-125">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="0ba05-126">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ba05-126">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="0ba05-127">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ba05-127">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="0ba05-128">Fournisseurs disponibles SQLitePCLRaw</span><span class="sxs-lookup"><span data-stu-id="0ba05-128">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="0ba05-129">Si vous ne comptez pas sur un bundle, vous pouvez utiliser les fournisseurs de SQLite disponibles avec l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="0ba05-129">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="0ba05-130">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="0ba05-130">Provider</span></span> | <span data-ttu-id="0ba05-131">Description</span><span class="sxs-lookup"><span data-stu-id="0ba05-131">Description</span></span> |
|--|--|
| [<span data-ttu-id="0ba05-132">SQLitePCLRaw. Provider. Dynamic</span><span class="sxs-lookup"><span data-stu-id="0ba05-132">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="0ba05-133">Le `dynamic` fournisseur charge la bibliothèque Native au lieu d’utiliser des <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributs.</span><span class="sxs-lookup"><span data-stu-id="0ba05-133">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="0ba05-134">Pour plus d’informations sur l’utilisation de ce fournisseur, consultez [utiliser le fournisseur dynamique](#use-the-dynamic-provider).</span><span class="sxs-lookup"><span data-stu-id="0ba05-134">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="0ba05-135">SQLitePCLRaw. Provider. e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="0ba05-135">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="0ba05-136">`e_sqlite3`Est le fournisseur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0ba05-136">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="0ba05-137">SQLitePCLRaw. Provider. e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="0ba05-137">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="0ba05-138">Le `e_sqlcipher` fournisseur est non officiel et non pris en charge `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="0ba05-138">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="0ba05-139">SQLitePCLRaw. Provider. sqlite3</span><span class="sxs-lookup"><span data-stu-id="0ba05-139">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="0ba05-140">Le `sqlite3` fournisseur est un système fourni `SQLite` pour iOS, MacOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="0ba05-140">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="0ba05-141">SQLitePCLRaw. Provider. sqlcipher</span><span class="sxs-lookup"><span data-stu-id="0ba05-141">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="0ba05-142">Le `sqlcipher` fournisseur est destiné aux `SQLCipher` Builds officielles à partir de `Zetetic` .</span><span class="sxs-lookup"><span data-stu-id="0ba05-142">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="0ba05-143">SQLitePCLRaw. Provider. winsqlite3</span><span class="sxs-lookup"><span data-stu-id="0ba05-143">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="0ba05-144">Le `winsqlite3` fournisseur est destiné aux environnements Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0ba05-144">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="0ba05-145">Pour utiliser le `sqlite3` fournisseur, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0ba05-145">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="0ba05-146">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ba05-146">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="0ba05-147">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ba05-147">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="0ba05-148">Une fois les packages installés, vous définissez le fournisseur sur l' `sqlite3` instance.</span><span class="sxs-lookup"><span data-stu-id="0ba05-148">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="0ba05-149">Utiliser le fournisseur dynamique</span><span class="sxs-lookup"><span data-stu-id="0ba05-149">Use the dynamic provider</span></span>

<span data-ttu-id="0ba05-150">Vous pouvez utiliser votre propre Build de SQLite en tirant parti du `SQLitePCLRaw.provider.dynamic_cdecl` Package.</span><span class="sxs-lookup"><span data-stu-id="0ba05-150">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="0ba05-151">Dans ce cas, vous êtes responsable du déploiement de la bibliothèque native avec votre application.</span><span class="sxs-lookup"><span data-stu-id="0ba05-151">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="0ba05-152">Notez que les détails du déploiement de bibliothèques natives avec votre application varient considérablement selon la plateforme et le Runtime .NET que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="0ba05-152">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="0ba05-153">Tout d’abord, vous devez implémenter `IGetFunctionPointer` .</span><span class="sxs-lookup"><span data-stu-id="0ba05-153">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="0ba05-154">L’implémentation sur .NET Core est la suivante :</span><span class="sxs-lookup"><span data-stu-id="0ba05-154">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="0ba05-155">Ensuite, configurez le `SQLitePCLRaw` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0ba05-155">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="0ba05-156">Assurez-vous que cette opération est effectuée avant que `Microsoft.Data.Sqlite` ne soit utilisé dans votre application.</span><span class="sxs-lookup"><span data-stu-id="0ba05-156">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="0ba05-157">Évitez également d’utiliser un `SQLitePCLRaw` package de bundle qui peut remplacer votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0ba05-157">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
