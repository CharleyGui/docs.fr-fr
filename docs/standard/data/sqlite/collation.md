---
title: Classement
ms.date: 12/13/2019
description: Apprenez à créer une séquence de collation personnalisée.
ms.openlocfilehash: b93c82a4ace154b8293b05effa8f9e9294fa7708
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506539"
---
# <a name="collation"></a><span data-ttu-id="72f0b-103">Classement</span><span class="sxs-lookup"><span data-stu-id="72f0b-103">Collation</span></span>

<span data-ttu-id="72f0b-104">Les séquences de collation sont utilisées par SQLite pour comparer les valeurs textUELLEs pour déterminer l’ordre et l’égalité.</span><span class="sxs-lookup"><span data-stu-id="72f0b-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="72f0b-105">Vous pouvez spécifier la collation à utiliser lors de la création de colonnes ou par opération dans les requêtes SQL.</span><span class="sxs-lookup"><span data-stu-id="72f0b-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="72f0b-106">SQLite comprend trois séquences de collation par défaut.</span><span class="sxs-lookup"><span data-stu-id="72f0b-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="72f0b-107">Classement</span><span class="sxs-lookup"><span data-stu-id="72f0b-107">Collation</span></span> | <span data-ttu-id="72f0b-108">Description</span><span class="sxs-lookup"><span data-stu-id="72f0b-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="72f0b-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="72f0b-109">RTRIM</span></span>     | <span data-ttu-id="72f0b-110">Ignore l’espace blanc qui suit</span><span class="sxs-lookup"><span data-stu-id="72f0b-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="72f0b-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="72f0b-111">NOCASE</span></span>    | <span data-ttu-id="72f0b-112">Cas insensible pour les personnages ASCII A-Z</span><span class="sxs-lookup"><span data-stu-id="72f0b-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="72f0b-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="72f0b-113">BINARY</span></span>    | <span data-ttu-id="72f0b-114">Sensible aux cas.</span><span class="sxs-lookup"><span data-stu-id="72f0b-114">Case-sensitive.</span></span> <span data-ttu-id="72f0b-115">Compare directement les octets</span><span class="sxs-lookup"><span data-stu-id="72f0b-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="72f0b-116">Collation personnalisée</span><span class="sxs-lookup"><span data-stu-id="72f0b-116">Custom collation</span></span>

<span data-ttu-id="72f0b-117">Vous pouvez également définir vos propres séquences de collation <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>ou remplacer les séquences intégrées à l’aide de .</span><span class="sxs-lookup"><span data-stu-id="72f0b-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="72f0b-118">L’exemple suivant montre la collation NOCASE pour prendre en charge les caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="72f0b-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="72f0b-119">Le [code d’échantillon complet](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="72f0b-119">The [full sample code](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="72f0b-120">Like (opérateur)</span><span class="sxs-lookup"><span data-stu-id="72f0b-120">Like operator</span></span>

<span data-ttu-id="72f0b-121">L’opérateur LIKE de SQLite n’honore pas les collations.</span><span class="sxs-lookup"><span data-stu-id="72f0b-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="72f0b-122">La mise en œuvre par défaut a la même sémantique que la collation NOCASE.</span><span class="sxs-lookup"><span data-stu-id="72f0b-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="72f0b-123">Ce n’est que insensible aux caractères ASCII A à Z.</span><span class="sxs-lookup"><span data-stu-id="72f0b-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="72f0b-124">Vous pouvez facilement rendre l’opérateur LIKE sensible au cas en utilisant la déclaration pragma suivante :</span><span class="sxs-lookup"><span data-stu-id="72f0b-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="72f0b-125">Consultez [les fonctions définies par l’utilisateur](user-defined-functions.md) pour plus de détails sur la mise en œuvre de l’opérateur LIKE.</span><span class="sxs-lookup"><span data-stu-id="72f0b-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="72f0b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72f0b-126">See also</span></span>

* [<span data-ttu-id="72f0b-127">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="72f0b-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="72f0b-128">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="72f0b-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
