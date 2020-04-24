---
title: Extensions
ms.date: 12/13/2019
description: Découvrez comment charger des extensions SQLite.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242957"
---
# <a name="extensions"></a>Extensions

SQLite prend en charge le chargement des extensions au moment de l’exécution. Les extensions incluent des fonctions telles que les fonctions SQL supplémentaires, les classements, les tables virtuelles et bien plus encore.

.NET Core comprend une logique supplémentaire pour localiser les bibliothèques natives dans d’autres emplacements, tels que les packages NuGet référencés. Malheureusement, SQLite ne peut pas tirer parti de cette logique. Il appelle l’API de la plateforme directement pour charger des bibliothèques. Pour cette raison, vous devrez peut-être modifier les variables d’environnement PATH, LD_LIBRARY_PATH ou DYLD_LIBRARY_PATH avant de charger les extensions SQLite. [Un exemple](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) sur GitHub illustre la recherche de fichiers binaires pour le runtime actuel à l’intérieur d’un package NuGet référencé.

Pour charger une extension, appelez la <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> méthode. Microsoft. Data. sqlite garantit que l’extension reste chargée même si la connexion est fermée et rouverte.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Voir aussi

* [Extensions chargeable au moment de l’exécution](https://www.sqlite.org/loadext.html)
