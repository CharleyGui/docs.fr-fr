---
title: Paramètres
ms.date: 12/13/2019
description: Découvrez comment utiliser les paramètres SQL.
ms.openlocfilehash: b24610a5cb65e2b24171452acef9bf55b4995431
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768948"
---
# <a name="parameters"></a><span data-ttu-id="63e87-103">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63e87-103">Parameters</span></span>

<span data-ttu-id="63e87-104">Les paramètres sont utilisés pour se protéger contre les attaques par injection SQL.</span><span class="sxs-lookup"><span data-stu-id="63e87-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="63e87-105">Au lieu de concaténer les entrées utilisateur avec les instructions SQL, utilisez des paramètres pour vous assurer que l’entrée n’est jamais traitée comme une valeur littérale et qu’elle n’est jamais exécutée.</span><span class="sxs-lookup"><span data-stu-id="63e87-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="63e87-106">Dans SQLite, les paramètres sont généralement autorisés partout où un littéral est autorisé dans les instructions SQL.</span><span class="sxs-lookup"><span data-stu-id="63e87-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="63e87-107">Les paramètres peuvent être préfixés avec `:` , `@` ou `$` .</span><span class="sxs-lookup"><span data-stu-id="63e87-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="63e87-108">Pour plus d’informations sur la façon dont les valeurs .NET sont mappées aux valeurs SQLite, consultez [types de données](types.md) .</span><span class="sxs-lookup"><span data-stu-id="63e87-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="63e87-109">Troncation</span><span class="sxs-lookup"><span data-stu-id="63e87-109">Truncation</span></span>

<span data-ttu-id="63e87-110">Utilisez la <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> propriété pour tronquer les valeurs de texte et d’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="63e87-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Size = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="63e87-111">Autres types</span><span class="sxs-lookup"><span data-stu-id="63e87-111">Alternative types</span></span>

<span data-ttu-id="63e87-112">Parfois, vous souhaiterez peut-être utiliser un autre type de SQLite.</span><span class="sxs-lookup"><span data-stu-id="63e87-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="63e87-113">Pour ce faire, définissez la <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> propriété.</span><span class="sxs-lookup"><span data-stu-id="63e87-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="63e87-114">Les mappages de type alternatifs suivants peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="63e87-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="63e87-115">Pour les mappages par défaut, consultez [types de données](types.md).</span><span class="sxs-lookup"><span data-stu-id="63e87-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="63e87-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="63e87-116">Value</span></span>          | <span data-ttu-id="63e87-117">SqliteType</span><span class="sxs-lookup"><span data-stu-id="63e87-117">SqliteType</span></span> | <span data-ttu-id="63e87-118">Notes</span><span class="sxs-lookup"><span data-stu-id="63e87-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="63e87-119">Char</span><span class="sxs-lookup"><span data-stu-id="63e87-119">Char</span></span>           | <span data-ttu-id="63e87-120">Integer</span><span class="sxs-lookup"><span data-stu-id="63e87-120">Integer</span></span>    | <span data-ttu-id="63e87-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="63e87-121">UTF-16</span></span>           |
| <span data-ttu-id="63e87-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="63e87-122">DateTime</span></span>       | <span data-ttu-id="63e87-123">Real</span><span class="sxs-lookup"><span data-stu-id="63e87-123">Real</span></span>       | <span data-ttu-id="63e87-124">Valeur du jour julien</span><span class="sxs-lookup"><span data-stu-id="63e87-124">Julian day value</span></span> |
| <span data-ttu-id="63e87-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="63e87-125">DateTimeOffset</span></span> | <span data-ttu-id="63e87-126">Real</span><span class="sxs-lookup"><span data-stu-id="63e87-126">Real</span></span>       | <span data-ttu-id="63e87-127">Valeur du jour julien</span><span class="sxs-lookup"><span data-stu-id="63e87-127">Julian day value</span></span> |
| <span data-ttu-id="63e87-128">Guid</span><span class="sxs-lookup"><span data-stu-id="63e87-128">Guid</span></span>           | <span data-ttu-id="63e87-129">Objet blob</span><span class="sxs-lookup"><span data-stu-id="63e87-129">Blob</span></span>       |                  |
| <span data-ttu-id="63e87-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="63e87-130">TimeSpan</span></span>       | <span data-ttu-id="63e87-131">Real</span><span class="sxs-lookup"><span data-stu-id="63e87-131">Real</span></span>       | <span data-ttu-id="63e87-132">En jours</span><span class="sxs-lookup"><span data-stu-id="63e87-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="63e87-133">Paramètres de sortie</span><span class="sxs-lookup"><span data-stu-id="63e87-133">Output parameters</span></span>

<span data-ttu-id="63e87-134">SQLite ne prend pas en charge les paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="63e87-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="63e87-135">Retournent les valeurs dans les résultats de la requête à la place.</span><span class="sxs-lookup"><span data-stu-id="63e87-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="63e87-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63e87-136">See also</span></span>

* [<span data-ttu-id="63e87-137">Types de données</span><span class="sxs-lookup"><span data-stu-id="63e87-137">Data types</span></span>](types.md)
