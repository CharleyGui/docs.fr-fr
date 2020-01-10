---
title: Collation
ms.date: 12/13/2019
description: Découvrez comment créer une séquence de classement personnalisée.
ms.openlocfilehash: 9cc574a75c8f5347dd9bb44e36af72e50afa57b4
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777387"
---
# <a name="collation"></a><span data-ttu-id="53c75-103">Collation</span><span class="sxs-lookup"><span data-stu-id="53c75-103">Collation</span></span>

<span data-ttu-id="53c75-104">Les séquences de classement sont utilisées par SQLite lors de la comparaison des valeurs de texte pour déterminer l’ordre et l’égalité.</span><span class="sxs-lookup"><span data-stu-id="53c75-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="53c75-105">Vous pouvez spécifier le classement à utiliser lors de la création de colonnes ou par opération dans des requêtes SQL.</span><span class="sxs-lookup"><span data-stu-id="53c75-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="53c75-106">SQLite comprend trois séquences de classement par défaut.</span><span class="sxs-lookup"><span data-stu-id="53c75-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="53c75-107">Collation</span><span class="sxs-lookup"><span data-stu-id="53c75-107">Collation</span></span> | <span data-ttu-id="53c75-108">Description</span><span class="sxs-lookup"><span data-stu-id="53c75-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="53c75-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="53c75-109">RTRIM</span></span>     | <span data-ttu-id="53c75-110">Ignore les espaces de fin</span><span class="sxs-lookup"><span data-stu-id="53c75-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="53c75-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="53c75-111">NOCASE</span></span>    | <span data-ttu-id="53c75-112">Non-respect de la casse pour les caractères ASCII A-Z</span><span class="sxs-lookup"><span data-stu-id="53c75-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="53c75-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="53c75-113">BINARY</span></span>    | <span data-ttu-id="53c75-114">Respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="53c75-114">Case-sensitive.</span></span> <span data-ttu-id="53c75-115">Compare les octets directement</span><span class="sxs-lookup"><span data-stu-id="53c75-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="53c75-116">Classement personnalisé</span><span class="sxs-lookup"><span data-stu-id="53c75-116">Custom collation</span></span>

<span data-ttu-id="53c75-117">Vous pouvez également définir vos propres séquences de classement ou remplacer celles prédéfinies à l’aide de <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="53c75-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="53c75-118">L’exemple suivant illustre le remplacement du classement nocase pour prendre en charge les caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="53c75-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="53c75-119">L' [exemple de code complet](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="53c75-119">The [full sample code](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="53c75-120">Like (opérateur)</span><span class="sxs-lookup"><span data-stu-id="53c75-120">Like operator</span></span>

<span data-ttu-id="53c75-121">L’opérateur LIKE dans SQLite ne respecte pas les classements.</span><span class="sxs-lookup"><span data-stu-id="53c75-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="53c75-122">L’implémentation par défaut a la même sémantique que le classement nocase.</span><span class="sxs-lookup"><span data-stu-id="53c75-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="53c75-123">Elle ne respecte pas la casse pour les caractères ASCII de A à Z.</span><span class="sxs-lookup"><span data-stu-id="53c75-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="53c75-124">Vous pouvez facilement faire en sorte que l’opérateur LIKE respecte la casse en utilisant l’instruction pragma suivante :</span><span class="sxs-lookup"><span data-stu-id="53c75-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 0
```

<span data-ttu-id="53c75-125">Pour plus d’informations sur la substitution de l’implémentation de l’opérateur LIKE [, consultez fonctions définies](user-defined-functions.md) par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="53c75-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="53c75-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53c75-126">See also</span></span>

* [<span data-ttu-id="53c75-127">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="53c75-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="53c75-128">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="53c75-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
