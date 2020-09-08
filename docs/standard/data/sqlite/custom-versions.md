---
title: Versions SQLite personnalisées
ms.date: 09/04/2020
description: Découvrez comment utiliser une version personnalisée de la bibliothèque SQLite native.
ms.openlocfilehash: fbf4b4cd33e6e890ce0c0cfe0b7688487b94b4a3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516136"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="bb6b1-103">Versions SQLite personnalisées</span><span class="sxs-lookup"><span data-stu-id="bb6b1-103">Custom SQLite versions</span></span>

<span data-ttu-id="bb6b1-104">`Microsoft.Data.Sqlite` repose sur `SQLitePCLRaw` .</span><span class="sxs-lookup"><span data-stu-id="bb6b1-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="bb6b1-105">Vous pouvez utiliser des versions personnalisées de la bibliothèque SQLite native à l’aide d’un bundle ou en configurant un `SQLitePCLRaw` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="bb6b1-106">Offres groupées</span><span class="sxs-lookup"><span data-stu-id="bb6b1-106">Bundles</span></span>

<span data-ttu-id="bb6b1-107">`SQLitePCLRaw` fournit des packages de Bundle basés sur la commodité, qui facilitent l’apport des dépendances appropriées sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="bb6b1-108">Le `Microsoft.Data.Sqlite` package principal est intégré `SQLitePCLRaw.bundle_e_sqlite3` par défaut.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="bb6b1-109">Pour utiliser un autre Bundle, installez le `Microsoft.Data.Sqlite.Core` package à la place du package que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="bb6b1-110">Les offres groupées sont automatiquement initialisées par `Microsoft.Data.Sqlite` .</span><span class="sxs-lookup"><span data-stu-id="bb6b1-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="bb6b1-111">Bundle</span><span class="sxs-lookup"><span data-stu-id="bb6b1-111">Bundle</span></span> | <span data-ttu-id="bb6b1-112">Description</span><span class="sxs-lookup"><span data-stu-id="bb6b1-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="bb6b1-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="bb6b1-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="bb6b1-114">Fournit une version cohérente de SQLite sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="bb6b1-115">Comprend les extensions d’arborescence FTS4, FTS5, JSON1 et R \*.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="bb6b1-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-116">This is the default.</span></span> |
| [<span data-ttu-id="bb6b1-117">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="bb6b1-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="bb6b1-118">Fournit une build Open source non officielle de `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="bb6b1-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="bb6b1-119">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="bb6b1-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="bb6b1-120">Identique à `bundle_e_sqlite3` , sauf sur iOS où il utilise la bibliothèque SQLite du système.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="bb6b1-121">SQLitePCLRaw. bundle_sqlite3</span><span class="sxs-lookup"><span data-stu-id="bb6b1-121">SQLitePCLRaw.bundle_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_sqlite3) | <span data-ttu-id="bb6b1-122">Utilise la bibliothèque SQLite du système.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-122">Uses the system SQLite library.</span></span> |
| [<span data-ttu-id="bb6b1-123">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="bb6b1-123">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="bb6b1-124">Utilise `winsqlite3.dll` , la bibliothèque SQLite système sur Windows 10.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-124">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="bb6b1-125">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="bb6b1-125">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="bb6b1-126">Utilise les `SQLCipher` Builds officielles de zetetic (non inclus).</span><span class="sxs-lookup"><span data-stu-id="bb6b1-126">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="bb6b1-127">Par exemple, pour utiliser la build Open source non officielle de, `SQLCipher` Utilisez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-127">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="bb6b1-128">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb6b1-128">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="bb6b1-129">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb6b1-129">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="bb6b1-130">Fournisseurs disponibles SQLitePCLRaw</span><span class="sxs-lookup"><span data-stu-id="bb6b1-130">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="bb6b1-131">Si vous ne comptez pas sur un bundle, vous pouvez utiliser les fournisseurs de SQLite disponibles avec l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-131">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="bb6b1-132">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="bb6b1-132">Provider</span></span> | <span data-ttu-id="bb6b1-133">Description</span><span class="sxs-lookup"><span data-stu-id="bb6b1-133">Description</span></span> |
|--|--|
| [<span data-ttu-id="bb6b1-134">SQLitePCLRaw. Provider. Dynamic</span><span class="sxs-lookup"><span data-stu-id="bb6b1-134">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="bb6b1-135">Le `dynamic` fournisseur charge la bibliothèque Native au lieu d’utiliser des <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributs.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-135">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="bb6b1-136">Pour plus d’informations sur l’utilisation de ce fournisseur, consultez [utiliser le fournisseur dynamique](#use-the-dynamic-provider).</span><span class="sxs-lookup"><span data-stu-id="bb6b1-136">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="bb6b1-137">SQLitePCLRaw. Provider. e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="bb6b1-137">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="bb6b1-138">`e_sqlite3`Est le fournisseur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-138">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="bb6b1-139">SQLitePCLRaw. Provider. e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="bb6b1-139">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="bb6b1-140">Le `e_sqlcipher` fournisseur est non officiel et non pris en charge `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="bb6b1-140">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="bb6b1-141">SQLitePCLRaw. Provider. sqlite3</span><span class="sxs-lookup"><span data-stu-id="bb6b1-141">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="bb6b1-142">Le `sqlite3` fournisseur est un système fourni `SQLite` pour iOS, MacOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-142">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="bb6b1-143">SQLitePCLRaw. Provider. sqlcipher</span><span class="sxs-lookup"><span data-stu-id="bb6b1-143">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="bb6b1-144">Le `sqlcipher` fournisseur est destiné aux `SQLCipher` Builds officielles à partir de `Zetetic` .</span><span class="sxs-lookup"><span data-stu-id="bb6b1-144">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="bb6b1-145">SQLitePCLRaw. Provider. winsqlite3</span><span class="sxs-lookup"><span data-stu-id="bb6b1-145">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="bb6b1-146">Le `winsqlite3` fournisseur est destiné aux environnements Windows 10.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-146">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="bb6b1-147">Pour utiliser le `sqlite3` fournisseur, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bb6b1-147">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="bb6b1-148">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb6b1-148">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="bb6b1-149">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb6b1-149">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="bb6b1-150">Une fois les packages installés, vous définissez le fournisseur sur l' `sqlite3` instance.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-150">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="bb6b1-151">Utiliser le fournisseur dynamique</span><span class="sxs-lookup"><span data-stu-id="bb6b1-151">Use the dynamic provider</span></span>

<span data-ttu-id="bb6b1-152">Vous pouvez utiliser votre propre Build de SQLite en tirant parti du `SQLitePCLRaw.provider.dynamic_cdecl` Package.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-152">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="bb6b1-153">Dans ce cas, vous êtes responsable du déploiement de la bibliothèque native avec votre application.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-153">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="bb6b1-154">Notez que les détails du déploiement de bibliothèques natives avec votre application varient considérablement selon la plateforme et le Runtime .NET que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-154">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="bb6b1-155">Tout d’abord, vous devez implémenter `IGetFunctionPointer` .</span><span class="sxs-lookup"><span data-stu-id="bb6b1-155">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="bb6b1-156">L’implémentation sur .NET Core est la suivante :</span><span class="sxs-lookup"><span data-stu-id="bb6b1-156">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="bb6b1-157">Ensuite, configurez le `SQLitePCLRaw` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-157">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="bb6b1-158">Assurez-vous que cette opération est effectuée avant que `Microsoft.Data.Sqlite` ne soit utilisé dans votre application.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-158">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="bb6b1-159">Évitez également d’utiliser un `SQLitePCLRaw` package de bundle qui peut remplacer votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bb6b1-159">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
