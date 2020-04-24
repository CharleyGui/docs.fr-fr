---
title: Chiffrement
ms.date: 12/13/2019
description: Découvrez comment chiffrer votre fichier de base de données.
ms.openlocfilehash: ccdd4b6b8642b3cde1c2667c9ca432a9b0ef21f2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447264"
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

Pour activer le chiffrement, spécifiez la `Password` clé à l’aide du mot clé de chaîne de connexion. Permet <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> d’ajouter ou de mettre à jour la valeur de l’entrée d’utilisateur et d’éviter les attaques par injection de chaîne de connexion.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a>Regénération du clé de la base de données

Si vous souhaitez modifier la clé de chiffrement d’une base de données `PRAGMA rekey` , émettez une instruction. Pour déchiffrer la base `NULL`de données, spécifiez.

Malheureusement, SQLite ne prend pas en `PRAGMA` charge les paramètres dans les instructions. Utilisez plutôt la fonction `quote()` pour empêcher l’injection SQL.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
