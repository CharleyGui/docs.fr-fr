---
title: Mots clés de requête - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 44af3bf1a7c013c16c7b4a4528c3516621bea149
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422540"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="09e1f-102">Mots clés de requête (référence C#)</span><span class="sxs-lookup"><span data-stu-id="09e1f-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="09e1f-103">Cette section contient les mots clés contextuels utilisés dans les expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="09e1f-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="09e1f-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="09e1f-104">In this section</span></span>

|<span data-ttu-id="09e1f-105">Clause</span><span class="sxs-lookup"><span data-stu-id="09e1f-105">Clause</span></span>|<span data-ttu-id="09e1f-106">Description</span><span class="sxs-lookup"><span data-stu-id="09e1f-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="09e1f-107">from</span><span class="sxs-lookup"><span data-stu-id="09e1f-107">from</span></span>](from-clause.md)|<span data-ttu-id="09e1f-108">Spécifie une source de données et une variable de portée (semblable à une variable d’itération).</span><span class="sxs-lookup"><span data-stu-id="09e1f-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="09e1f-109">where</span><span class="sxs-lookup"><span data-stu-id="09e1f-109">where</span></span>](where-clause.md)|<span data-ttu-id="09e1f-110">Filtre des éléments sources basés sur une ou plusieurs expressions booléennes séparées par des opérateurs AND et OR logiques (`&&` ou <code>&#124;&#124;</code>).</span><span class="sxs-lookup"><span data-stu-id="09e1f-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="09e1f-111">select</span><span class="sxs-lookup"><span data-stu-id="09e1f-111">select</span></span>](select-clause.md)|<span data-ttu-id="09e1f-112">Spécifie le type et la forme que les éléments de la séquence retournée auront une fois la requête exécutée.</span><span class="sxs-lookup"><span data-stu-id="09e1f-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="09e1f-113">group</span><span class="sxs-lookup"><span data-stu-id="09e1f-113">group</span></span>](group-clause.md)|<span data-ttu-id="09e1f-114">Regroupe les résultats de la requête d’après une valeur de clé spécifiée.</span><span class="sxs-lookup"><span data-stu-id="09e1f-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="09e1f-115">into</span><span class="sxs-lookup"><span data-stu-id="09e1f-115">into</span></span>](into.md)|<span data-ttu-id="09e1f-116">Fournit un identificateur qui peut servir comme référence pour les résultats d’une clause join, group ou select.</span><span class="sxs-lookup"><span data-stu-id="09e1f-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="09e1f-117">orderby</span><span class="sxs-lookup"><span data-stu-id="09e1f-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="09e1f-118">Trie des résultats de la requête par ordre croissant ou décroissant selon le comparateur par défaut du type d’élément.</span><span class="sxs-lookup"><span data-stu-id="09e1f-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="09e1f-119">join</span><span class="sxs-lookup"><span data-stu-id="09e1f-119">join</span></span>](join-clause.md)|<span data-ttu-id="09e1f-120">Joint deux sources de données selon une comparaison d’égalité entre deux critères de comparaison spécifiés.</span><span class="sxs-lookup"><span data-stu-id="09e1f-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="09e1f-121">let</span><span class="sxs-lookup"><span data-stu-id="09e1f-121">let</span></span>](let-clause.md)|<span data-ttu-id="09e1f-122">Introduit une variable de portée pour stocker des résultats de sous-expression dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="09e1f-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="09e1f-123">in</span><span class="sxs-lookup"><span data-stu-id="09e1f-123">in</span></span>](in.md)|<span data-ttu-id="09e1f-124">Mot clé contextuel dans une clause [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="09e1f-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="09e1f-125">on</span><span class="sxs-lookup"><span data-stu-id="09e1f-125">on</span></span>](on.md)|<span data-ttu-id="09e1f-126">Mot clé contextuel dans une clause [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="09e1f-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="09e1f-127">equals</span><span class="sxs-lookup"><span data-stu-id="09e1f-127">equals</span></span>](equals.md)|<span data-ttu-id="09e1f-128">Mot clé contextuel dans une clause [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="09e1f-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="09e1f-129">by</span><span class="sxs-lookup"><span data-stu-id="09e1f-129">by</span></span>](by.md)|<span data-ttu-id="09e1f-130">Mot clé contextuel dans une clause [group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="09e1f-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="09e1f-131">ascending</span><span class="sxs-lookup"><span data-stu-id="09e1f-131">ascending</span></span>](ascending.md)|<span data-ttu-id="09e1f-132">Mot clé contextuel dans une clause [orderby](orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="09e1f-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="09e1f-133">descending</span><span class="sxs-lookup"><span data-stu-id="09e1f-133">descending</span></span>](descending.md)|<span data-ttu-id="09e1f-134">Mot clé contextuel dans une clause [orderby](orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="09e1f-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="09e1f-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09e1f-135">See also</span></span>

- [<span data-ttu-id="09e1f-136">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="09e1f-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="09e1f-137">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="09e1f-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="09e1f-138">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="09e1f-138">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="09e1f-139">Mise en route de LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="09e1f-139">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
