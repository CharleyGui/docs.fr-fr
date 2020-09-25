---
title: Chiffrement
ms.date: 09/08/2020
description: Découvrez comment chiffrer votre fichier de base de données.
ms.openlocfilehash: 1b33e1510a269aba87caba2cd39faab33791aa55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203408"
---
# <a name="encryption"></a>Chiffrement

SQLite ne prend pas en charge le chiffrement des fichiers de base de données par défaut. Au lieu de cela, vous devez utiliser une version modifiée de SQLite comme [See](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)ou [wxSQLite3](https://utelle.github.io/wxsqlite3). Cet article montre comment utiliser une build Open source non prise en charge de SQLCipher, mais les informations s’appliquent également à d’autres solutions dans la mesure où elles suivent généralement le même modèle.

## <a name="installation"></a>Installation

### <a name="net-core-cli"></a>[CLI .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

Pour plus d’informations sur l’utilisation d’une bibliothèque Native différente pour le chiffrement, consultez [versions SQLite personnalisées](custom-versions.md).

## <a name="specify-the-key"></a>Spécifier la clé

Pour activer le chiffrement sur une nouvelle base de données, spécifiez la clé à l’aide du `Password` mot clé de chaîne de connexion. Permet <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> d’ajouter ou de mettre à jour la valeur de l’entrée d’utilisateur et d’éviter les attaques par injection de chaîne de connexion.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

> [!TIP]
> La méthode de chiffrement et de déchiffrement des bases de données existantes varie selon la solution que vous utilisez. Par exemple, vous devez utiliser la `sqlcipher_export()` fonction sur SQLCipher. Pour plus d’informations, consultez la documentation de votre solution.

## <a name="rekeying-the-database"></a>Regénération du clé de la base de données

Si vous souhaitez modifier la clé d’une base de données chiffrée, émettez une `PRAGMA rekey` instruction.

Malheureusement, SQLite ne prend pas en charge les paramètres dans les `PRAGMA` instructions. Utilisez plutôt la `quote()` fonction pour empêcher l’injection SQL.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
