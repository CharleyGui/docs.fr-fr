---
title: Parameters
ms.date: 12/13/2019
description: Découvrez comment utiliser les paramètres SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447187"
---
# <a name="parameters"></a><span data-ttu-id="6ad07-103">Parameters</span><span class="sxs-lookup"><span data-stu-id="6ad07-103">Parameters</span></span>

<span data-ttu-id="6ad07-104">Les paramètres sont utilisés pour se protéger contre les attaques par injection SQL.</span><span class="sxs-lookup"><span data-stu-id="6ad07-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="6ad07-105">Au lieu de concaténer les entrées utilisateur avec les instructions SQL, utilisez des paramètres pour vous assurer que l’entrée n’est jamais traitée comme une valeur littérale et qu’elle n’est jamais exécutée.</span><span class="sxs-lookup"><span data-stu-id="6ad07-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="6ad07-106">Dans SQLite, les paramètres sont généralement autorisés partout où un littéral est autorisé dans les instructions SQL.</span><span class="sxs-lookup"><span data-stu-id="6ad07-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="6ad07-107">Les paramètres peuvent être précédés de `:`, `@`ou `$`.</span><span class="sxs-lookup"><span data-stu-id="6ad07-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="6ad07-108">Pour plus d’informations sur la façon dont les valeurs .NET sont mappées aux valeurs SQLite, consultez [types de données](types.md) .</span><span class="sxs-lookup"><span data-stu-id="6ad07-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="6ad07-109">Troncation</span><span class="sxs-lookup"><span data-stu-id="6ad07-109">Truncation</span></span>

<span data-ttu-id="6ad07-110">Utilisez la propriété <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> pour tronquer les valeurs de texte et d’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="6ad07-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="6ad07-111">Autres types</span><span class="sxs-lookup"><span data-stu-id="6ad07-111">Alternative types</span></span>

<span data-ttu-id="6ad07-112">Parfois, vous souhaiterez peut-être utiliser un autre type de SQLite.</span><span class="sxs-lookup"><span data-stu-id="6ad07-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="6ad07-113">Pour ce faire, définissez la propriété <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>.</span><span class="sxs-lookup"><span data-stu-id="6ad07-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="6ad07-114">Les mappages de type alternatifs suivants peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="6ad07-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="6ad07-115">Pour les mappages par défaut, consultez [types de données](types.md).</span><span class="sxs-lookup"><span data-stu-id="6ad07-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="6ad07-116">Value</span><span class="sxs-lookup"><span data-stu-id="6ad07-116">Value</span></span>          | <span data-ttu-id="6ad07-117">SqliteType</span><span class="sxs-lookup"><span data-stu-id="6ad07-117">SqliteType</span></span> | <span data-ttu-id="6ad07-118">Notes</span><span class="sxs-lookup"><span data-stu-id="6ad07-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="6ad07-119">Char</span><span class="sxs-lookup"><span data-stu-id="6ad07-119">Char</span></span>           | <span data-ttu-id="6ad07-120">Entier</span><span class="sxs-lookup"><span data-stu-id="6ad07-120">Integer</span></span>    | <span data-ttu-id="6ad07-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="6ad07-121">UTF-16</span></span>           |
| <span data-ttu-id="6ad07-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="6ad07-122">DateTime</span></span>       | <span data-ttu-id="6ad07-123">Real</span><span class="sxs-lookup"><span data-stu-id="6ad07-123">Real</span></span>       | <span data-ttu-id="6ad07-124">Valeur du jour julien</span><span class="sxs-lookup"><span data-stu-id="6ad07-124">Julian day value</span></span> |
| <span data-ttu-id="6ad07-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6ad07-125">DateTimeOffset</span></span> | <span data-ttu-id="6ad07-126">Real</span><span class="sxs-lookup"><span data-stu-id="6ad07-126">Real</span></span>       | <span data-ttu-id="6ad07-127">Valeur du jour julien</span><span class="sxs-lookup"><span data-stu-id="6ad07-127">Julian day value</span></span> |
| <span data-ttu-id="6ad07-128">GUID</span><span class="sxs-lookup"><span data-stu-id="6ad07-128">Guid</span></span>           | <span data-ttu-id="6ad07-129">Objet Blob</span><span class="sxs-lookup"><span data-stu-id="6ad07-129">Blob</span></span>       |                  |
| <span data-ttu-id="6ad07-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="6ad07-130">TimeSpan</span></span>       | <span data-ttu-id="6ad07-131">Real</span><span class="sxs-lookup"><span data-stu-id="6ad07-131">Real</span></span>       | <span data-ttu-id="6ad07-132">En jours</span><span class="sxs-lookup"><span data-stu-id="6ad07-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="6ad07-133">Paramètres de sortie</span><span class="sxs-lookup"><span data-stu-id="6ad07-133">Output parameters</span></span>

<span data-ttu-id="6ad07-134">SQLite ne prend pas en charge les paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="6ad07-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="6ad07-135">Retournent les valeurs dans les résultats de la requête à la place.</span><span class="sxs-lookup"><span data-stu-id="6ad07-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ad07-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ad07-136">See also</span></span>

* [<span data-ttu-id="6ad07-137">Types de données</span><span class="sxs-lookup"><span data-stu-id="6ad07-137">Data types</span></span>](types.md)
