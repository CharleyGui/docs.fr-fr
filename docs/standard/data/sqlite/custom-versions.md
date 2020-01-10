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
# <a name="custom-sqlite-versions"></a>Versions SQLite personnalisées

Microsoft. Data. sqlite est basé sur SQLitePCLRaw. Vous pouvez utiliser des versions personnalisées de la bibliothèque SQLite native à l’aide d’un bundle ou en configurant un fournisseur SQLitePCLRaw.

## <a name="bundles"></a>Offres groupées

SQLitePCLRaw fournit des packages de bundle qui facilitent l’apport des dépendances appropriées sur différentes plateformes.

Le package principal Microsoft. Data. sqlite apporte par défaut SQLitePCLRaw. bundle_e_sqlite3.

Pour utiliser un autre Bundle, installez le package `Microsoft.Data.Sqlite.Core` au lieu du package que vous souhaitez utiliser. Les offres groupées sont automatiquement initialisées par Microsoft. Data. sqlite.

| Offre groupée | Description |
| --- | --- |
| SQLitePCLRaw. bundle_e_sqlite3 | Fournit une version cohérente de SQLite sur toutes les plateformes. Comprend les FTS4, FTS5, JSON1 et | Extensions d’arborescence R *. Il s'agit de la valeur par défaut. |
| SQLitePCLRaw. bundle_green | Identique à bundle_e_sqlite3, sauf sur iOS où il utilise la bibliothèque SQLite du système. |
| SQLitePCLRaw. bundle_zetetic | Utilise les builds officielles de SQLCipher à partir de zetetic (non inclus). |
| SQLitePCLRaw. bundle_winsqlite3 | Utilise winsqlite3. dll, la bibliothèque SQLite système sur Windows 10. |
| SQLitePCLRaw. bundle_e_sqlcipher | Fournit une build Open source non officielle de SQLCipher. |

Par exemple, pour utiliser la build Open source non officielle de SQLCipher, utilisez les commandes suivantes.

### <a name="net-core-clitabnetcore-cli"></a>[CLI .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a>Fournisseurs SQLitePCLRaw

Vous pouvez utiliser votre propre Build de SQLite en tirant parti du package `SQLitePCLRaw.provider.dynamic_cdecl`. Dans ce cas, vous êtes responsable du déploiement de la bibliothèque native avec votre application. Notez que les détails du déploiement de bibliothèques natives avec votre application varient considérablement selon la plateforme et le Runtime .NET que vous utilisez.

Tout d’abord, vous devez implémenter IGetFunctionPointer. L’implémentation est relativement trivial sur .NET Core.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Ensuite, configurez le fournisseur SQLitePCLRaw. Assurez-vous que cette opération est effectuée avant l’utilisation de Microsoft. Data. sqlite dans votre application. Évitez également d’utiliser un package de Bundle SQLitePCLRaw qui peut remplacer votre fournisseur.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
