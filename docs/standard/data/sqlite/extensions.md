---
title: Extensions
ms.date: 12/13/2019
description: Apprenez à charger les extensions SQLite.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242957"
---
# <a name="extensions"></a>Extensions

SQLite prend en charge les extensions de chargement au moment de l’exécution. Les extensions comprennent des choses comme des fonctions SQL supplémentaires, des collations, des tables virtuelles, et plus encore.

.NET Core inclut une logique supplémentaire pour localiser les bibliothèques indigènes dans d’autres endroits comme les forfaits NuGet référencés. Malheureusement, SQLite ne peut pas tirer parti de cette logique; il appelle la plate-forme API directement pour charger les bibliothèques. Pour cette raison, vous devrez peut-être modifier les variables PATH, LD_LIBRARY_PATH ou DYLD_LIBRARY_PATH environnement avant de charger les extensions SQLite. Il ya [un échantillon](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) sur GitHub qui démontre la recherche de binaires pour le temps d’exécution actuel à l’intérieur d’un paquet NuGet référencé.

Pour charger une extension, appelez la <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> méthode. Microsoft.Data.Sqlite s’assurera que l’extension reste chargée même si la connexion est fermée et rouverte.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Voir aussi

* [Extensions chargeables à durée d’exécution](https://www.sqlite.org/loadext.html)
