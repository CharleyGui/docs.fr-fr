---
title: Paramètres
ms.date: 12/13/2019
description: Apprenez à utiliser les paramètres SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400455"
---
# <a name="parameters"></a><span data-ttu-id="3187a-103">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3187a-103">Parameters</span></span>

<span data-ttu-id="3187a-104">Les paramètres sont utilisés pour se protéger contre les attaques d’injection SQL.</span><span class="sxs-lookup"><span data-stu-id="3187a-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="3187a-105">Au lieu de concatenating entrée utilisateur avec les instructions SQL, utilisez des paramètres pour s’assurer que l’entrée n’est jamais traitée comme une valeur littérale et jamais exécutée.</span><span class="sxs-lookup"><span data-stu-id="3187a-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="3187a-106">Dans SQLite, les paramètres sont généralement autorisés partout où un littéal est autorisé dans les déclarations SQL.</span><span class="sxs-lookup"><span data-stu-id="3187a-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="3187a-107">Les paramètres peuvent être préfixés avec l’un ou l’autre, `:` `@`, ou `$`.</span><span class="sxs-lookup"><span data-stu-id="3187a-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="3187a-108">Voir [les types de données](types.md) pour plus de détails sur la façon dont les valeurs .NET sont cartographiées aux valeurs SQLite.</span><span class="sxs-lookup"><span data-stu-id="3187a-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="3187a-109">Troncation</span><span class="sxs-lookup"><span data-stu-id="3187a-109">Truncation</span></span>

<span data-ttu-id="3187a-110">Utilisez <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> la propriété pour tronquer les valeurs TEXT et BLOB.</span><span class="sxs-lookup"><span data-stu-id="3187a-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="3187a-111">Types alternatifs</span><span class="sxs-lookup"><span data-stu-id="3187a-111">Alternative types</span></span>

<span data-ttu-id="3187a-112">Parfois, vous pouvez utiliser un autre type SQLite.</span><span class="sxs-lookup"><span data-stu-id="3187a-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="3187a-113">Faites-le en <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> fixant la propriété.</span><span class="sxs-lookup"><span data-stu-id="3187a-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="3187a-114">Les cartes de type alternatif suivantes peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="3187a-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="3187a-115">Pour les cartes par défaut, voir [les types de données](types.md).</span><span class="sxs-lookup"><span data-stu-id="3187a-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="3187a-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="3187a-116">Value</span></span>          | <span data-ttu-id="3187a-117">SqliteType (SqliteType)</span><span class="sxs-lookup"><span data-stu-id="3187a-117">SqliteType</span></span> | <span data-ttu-id="3187a-118">Notes </span><span class="sxs-lookup"><span data-stu-id="3187a-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="3187a-119">Char</span><span class="sxs-lookup"><span data-stu-id="3187a-119">Char</span></span>           | <span data-ttu-id="3187a-120">Integer</span><span class="sxs-lookup"><span data-stu-id="3187a-120">Integer</span></span>    | <span data-ttu-id="3187a-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="3187a-121">UTF-16</span></span>           |
| <span data-ttu-id="3187a-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="3187a-122">DateTime</span></span>       | <span data-ttu-id="3187a-123">Real</span><span class="sxs-lookup"><span data-stu-id="3187a-123">Real</span></span>       | <span data-ttu-id="3187a-124">Julian valeur de jour</span><span class="sxs-lookup"><span data-stu-id="3187a-124">Julian day value</span></span> |
| <span data-ttu-id="3187a-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="3187a-125">DateTimeOffset</span></span> | <span data-ttu-id="3187a-126">Real</span><span class="sxs-lookup"><span data-stu-id="3187a-126">Real</span></span>       | <span data-ttu-id="3187a-127">Julian valeur de jour</span><span class="sxs-lookup"><span data-stu-id="3187a-127">Julian day value</span></span> |
| <span data-ttu-id="3187a-128">Guid</span><span class="sxs-lookup"><span data-stu-id="3187a-128">Guid</span></span>           | <span data-ttu-id="3187a-129">Objet blob</span><span class="sxs-lookup"><span data-stu-id="3187a-129">Blob</span></span>       |                  |
| <span data-ttu-id="3187a-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3187a-130">TimeSpan</span></span>       | <span data-ttu-id="3187a-131">Real</span><span class="sxs-lookup"><span data-stu-id="3187a-131">Real</span></span>       | <span data-ttu-id="3187a-132">En jours</span><span class="sxs-lookup"><span data-stu-id="3187a-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="3187a-133">Paramètres de sortie</span><span class="sxs-lookup"><span data-stu-id="3187a-133">Output parameters</span></span>

<span data-ttu-id="3187a-134">SQLite ne prend pas en charge les paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="3187a-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="3187a-135">Valeurs de rendement dans les résultats de la requête à la place.</span><span class="sxs-lookup"><span data-stu-id="3187a-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="3187a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3187a-136">See also</span></span>

* [<span data-ttu-id="3187a-137">Types de données</span><span class="sxs-lookup"><span data-stu-id="3187a-137">Data types</span></span>](types.md)
