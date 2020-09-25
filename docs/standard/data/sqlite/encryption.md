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
# <a name="encryption"></a><span data-ttu-id="7741d-103">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="7741d-103">Encryption</span></span>

<span data-ttu-id="7741d-104">SQLite ne prend pas en charge le chiffrement des fichiers de base de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="7741d-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="7741d-105">Au lieu de cela, vous devez utiliser une version modifiée de SQLite comme [See](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)ou [wxSQLite3](https://utelle.github.io/wxsqlite3).</span><span class="sxs-lookup"><span data-stu-id="7741d-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="7741d-106">Cet article montre comment utiliser une build Open source non prise en charge de SQLCipher, mais les informations s’appliquent également à d’autres solutions dans la mesure où elles suivent généralement le même modèle.</span><span class="sxs-lookup"><span data-stu-id="7741d-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="7741d-107">Installation</span><span class="sxs-lookup"><span data-stu-id="7741d-107">Installation</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="7741d-108">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="7741d-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="7741d-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7741d-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="7741d-110">Pour plus d’informations sur l’utilisation d’une bibliothèque Native différente pour le chiffrement, consultez [versions SQLite personnalisées](custom-versions.md).</span><span class="sxs-lookup"><span data-stu-id="7741d-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="7741d-111">Spécifier la clé</span><span class="sxs-lookup"><span data-stu-id="7741d-111">Specify the key</span></span>

<span data-ttu-id="7741d-112">Pour activer le chiffrement sur une nouvelle base de données, spécifiez la clé à l’aide du `Password` mot clé de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="7741d-112">To enable encryption on a new database, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="7741d-113">Permet <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> d’ajouter ou de mettre à jour la valeur de l’entrée d’utilisateur et d’éviter les attaques par injection de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="7741d-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

> [!TIP]
> <span data-ttu-id="7741d-114">La méthode de chiffrement et de déchiffrement des bases de données existantes varie selon la solution que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="7741d-114">The method for encrypting and decrypting existing databases varies depending on which solution you're using.</span></span> <span data-ttu-id="7741d-115">Par exemple, vous devez utiliser la `sqlcipher_export()` fonction sur SQLCipher.</span><span class="sxs-lookup"><span data-stu-id="7741d-115">For example, you need to use the `sqlcipher_export()` function on SQLCipher.</span></span> <span data-ttu-id="7741d-116">Pour plus d’informations, consultez la documentation de votre solution.</span><span class="sxs-lookup"><span data-stu-id="7741d-116">Check your solution's documentation for details.</span></span>

## <a name="rekeying-the-database"></a><span data-ttu-id="7741d-117">Regénération du clé de la base de données</span><span class="sxs-lookup"><span data-stu-id="7741d-117">Rekeying the database</span></span>

<span data-ttu-id="7741d-118">Si vous souhaitez modifier la clé d’une base de données chiffrée, émettez une `PRAGMA rekey` instruction.</span><span class="sxs-lookup"><span data-stu-id="7741d-118">If you want to change the key of an encrypted database, issue a `PRAGMA rekey` statement.</span></span>

<span data-ttu-id="7741d-119">Malheureusement, SQLite ne prend pas en charge les paramètres dans les `PRAGMA` instructions.</span><span class="sxs-lookup"><span data-stu-id="7741d-119">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="7741d-120">Utilisez plutôt la `quote()` fonction pour empêcher l’injection SQL.</span><span class="sxs-lookup"><span data-stu-id="7741d-120">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
