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
# <a name="encryption"></a><span data-ttu-id="c0702-103">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="c0702-103">Encryption</span></span>

<span data-ttu-id="c0702-104">SQLite ne prend pas en charge le chiffrement des fichiers de base de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="c0702-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="c0702-105">Au lieu de cela, vous devez utiliser une version modifiée de SQLite comme [See](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)ou [wxSQLite3](https://utelle.github.io/wxsqlite3).</span><span class="sxs-lookup"><span data-stu-id="c0702-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="c0702-106">Cet article montre comment utiliser une build Open source non prise en charge de SQLCipher, mais les informations s’appliquent également à d’autres solutions dans la mesure où elles suivent généralement le même modèle.</span><span class="sxs-lookup"><span data-stu-id="c0702-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="c0702-107">Installation</span><span class="sxs-lookup"><span data-stu-id="c0702-107">Installation</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="c0702-108">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="c0702-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="c0702-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c0702-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="c0702-110">Pour plus d’informations sur l’utilisation d’une bibliothèque Native différente pour le chiffrement, consultez [versions SQLite personnalisées](custom-versions.md).</span><span class="sxs-lookup"><span data-stu-id="c0702-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="c0702-111">Spécifier la clé</span><span class="sxs-lookup"><span data-stu-id="c0702-111">Specify the key</span></span>

<span data-ttu-id="c0702-112">Pour activer le chiffrement, spécifiez la `Password` clé à l’aide du mot clé de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="c0702-112">To enable encryption, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="c0702-113">Permet <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> d’ajouter ou de mettre à jour la valeur de l’entrée d’utilisateur et d’éviter les attaques par injection de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="c0702-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a><span data-ttu-id="c0702-114">Regénération du clé de la base de données</span><span class="sxs-lookup"><span data-stu-id="c0702-114">Rekeying the database</span></span>

<span data-ttu-id="c0702-115">Si vous souhaitez modifier la clé de chiffrement d’une base de données `PRAGMA rekey` , émettez une instruction.</span><span class="sxs-lookup"><span data-stu-id="c0702-115">If you want to change the encryption key of a database, issue a `PRAGMA rekey` statement.</span></span> <span data-ttu-id="c0702-116">Pour déchiffrer la base `NULL`de données, spécifiez.</span><span class="sxs-lookup"><span data-stu-id="c0702-116">To decrypt the database, specify `NULL`.</span></span>

<span data-ttu-id="c0702-117">Malheureusement, SQLite ne prend pas en `PRAGMA` charge les paramètres dans les instructions.</span><span class="sxs-lookup"><span data-stu-id="c0702-117">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="c0702-118">Utilisez plutôt la fonction `quote()` pour empêcher l’injection SQL.</span><span class="sxs-lookup"><span data-stu-id="c0702-118">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
