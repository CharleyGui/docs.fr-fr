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
# <a name="custom-sqlite-versions"></a>Versions SQLite personnalisées

`Microsoft.Data.Sqlite`repose sur `SQLitePCLRaw` . Vous pouvez utiliser des versions personnalisées de la bibliothèque SQLite native à l’aide d’un bundle ou en configurant un `SQLitePCLRaw` fournisseur.

## <a name="bundles"></a>Offres groupées

`SQLitePCLRaw`fournit des packages de Bundle basés sur la commodité, qui facilitent l’apport des dépendances appropriées sur différentes plateformes. Le `Microsoft.Data.Sqlite` package principal est intégré `SQLitePCLRaw.bundle_e_sqlite3` par défaut. Pour utiliser un autre Bundle, installez le `Microsoft.Data.Sqlite.Core` package à la place du package que vous souhaitez utiliser. Les offres groupées sont automatiquement initialisées par `Microsoft.Data.Sqlite` .

| Bundle | Description |
|--|--|
| [SQLitePCLRaw. bundle_e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | Fournit une version cohérente de SQLite sur toutes les plateformes. Comprend les extensions d’arborescence FTS4, FTS5, JSON1 et R *. Il s'agit de la valeur par défaut. |
| [SQLitePCLRaw. bundle_e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | Fournit une build Open source non officielle de `SQLCipher` . |
| [SQLitePCLRaw. bundle_green](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | Identique à `bundle_e_sqlite3` , sauf sur iOS où il utilise la bibliothèque SQLite du système. |
| [SQLitePCLRaw. bundle_winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | Utilise `winsqlite3.dll` , la bibliothèque SQLite système sur Windows 10. |
| [SQLitePCLRaw. bundle_zetetic](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | Utilise les `SQLCipher` Builds officielles de zetetic (non inclus). |

Par exemple, pour utiliser la build Open source non officielle de, `SQLCipher` Utilisez les commandes suivantes.

### <a name="net-core-cli"></a>[CLI .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a>Fournisseurs disponibles SQLitePCLRaw

Si vous ne comptez pas sur un bundle, vous pouvez utiliser les fournisseurs de SQLite disponibles avec l’assembly principal.

| Fournisseur | Description |
|--|--|
| [SQLitePCLRaw. Provider. Dynamic](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | Le `dynamic` fournisseur charge la bibliothèque Native au lieu d’utiliser des <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributs. Pour plus d’informations sur l’utilisation de ce fournisseur, consultez [utiliser le fournisseur dynamique](#use-the-dynamic-provider). |
| [SQLitePCLRaw. Provider. e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | `e_sqlite3`Est le fournisseur par défaut. |
| [SQLitePCLRaw. Provider. e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | Le `e_sqlcipher` fournisseur est non officiel et non pris en charge `SQLCipher` . |
| [SQLitePCLRaw. Provider. sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | Le `sqlite3` fournisseur est un système fourni `SQLite` pour iOS, MacOS et Linux. |
| [SQLitePCLRaw. Provider. sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | Le `sqlcipher` fournisseur est destiné aux `SQLCipher` Builds officielles à partir de `Zetetic` . |
| [SQLitePCLRaw. Provider. winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | Le `winsqlite3` fournisseur est destiné aux environnements Windows 10. |

Pour utiliser le `sqlite3` fournisseur, utilisez les commandes suivantes :

### <a name="net-core-cli"></a>[CLI .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

Une fois les packages installés, vous définissez le fournisseur sur l' `sqlite3` instance.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a>Utiliser le fournisseur dynamique

Vous pouvez utiliser votre propre Build de SQLite en tirant parti du `SQLitePCLRaw.provider.dynamic_cdecl` Package. Dans ce cas, vous êtes responsable du déploiement de la bibliothèque native avec votre application. Notez que les détails du déploiement de bibliothèques natives avec votre application varient considérablement selon la plateforme et le Runtime .NET que vous utilisez.

Tout d’abord, vous devez implémenter `IGetFunctionPointer` . L’implémentation sur .NET Core est la suivante :

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Ensuite, configurez le `SQLitePCLRaw` fournisseur. Assurez-vous que cette opération est effectuée avant que `Microsoft.Data.Sqlite` ne soit utilisé dans votre application. Évitez également d’utiliser un `SQLitePCLRaw` package de bundle qui peut remplacer votre fournisseur.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
