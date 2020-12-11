---
title: Extensions
ms.date: 12/08/2020
description: Découvrez comment charger des extensions SQLite.
ms.openlocfilehash: 68d31093662f373d6ebf4460d6a5d44029c27c5c
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110843"
---
# <a name="extensions"></a>Extensions

SQLite prend en charge le chargement des extensions au moment de l’exécution. Les extensions incluent des fonctions telles que les fonctions SQL supplémentaires, les classements, les tables virtuelles et bien plus encore.

.NET Core comprend une logique supplémentaire pour localiser les bibliothèques natives dans d’autres emplacements, tels que les packages NuGet référencés. Malheureusement, SQLite ne peut pas tirer parti de cette logique. Il appelle l’API de la plateforme directement pour charger des bibliothèques. Pour cette raison, vous devrez peut-être modifier les variables d’environnement PATH, LD_LIBRARY_PATH ou DYLD_LIBRARY_PATH avant de charger les extensions SQLite. [Un exemple](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) sur GitHub illustre la recherche de fichiers binaires pour le runtime actuel à l’intérieur d’un package NuGet référencé.

Pour charger une extension, appelez la <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> méthode. Microsoft. Data. sqlite garantit que l’extension reste chargée même si la connexion est fermée et rouverte.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

> [!NOTE]
> La méthode LoadExtension a été ajoutée dans la version 3,0.

## <a name="see-also"></a>Voir aussi

* [Extensions chargeable au moment de l’exécution](https://www.sqlite.org/loadext.html)
