---
description: Mots clés de requête - Référence C#
title: Mots clés de requête - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 0beea8634d13222aa18f14d79fdbd95a35cc832e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137134"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="69d72-103">Mots clés de requête (référence C#)</span><span class="sxs-lookup"><span data-stu-id="69d72-103">Query keywords (C# Reference)</span></span>

<span data-ttu-id="69d72-104">Cette section contient les mots clés contextuels utilisés dans les expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="69d72-104">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="69d72-105">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="69d72-105">In this section</span></span>

|<span data-ttu-id="69d72-106">Clause</span><span class="sxs-lookup"><span data-stu-id="69d72-106">Clause</span></span>|<span data-ttu-id="69d72-107">Description</span><span class="sxs-lookup"><span data-stu-id="69d72-107">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="69d72-108">from</span><span class="sxs-lookup"><span data-stu-id="69d72-108">from</span></span>](from-clause.md)|<span data-ttu-id="69d72-109">Spécifie une source de données et une variable de portée (semblable à une variable d’itération).</span><span class="sxs-lookup"><span data-stu-id="69d72-109">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="69d72-110">where</span><span class="sxs-lookup"><span data-stu-id="69d72-110">where</span></span>](where-clause.md)|<span data-ttu-id="69d72-111">Filtre des éléments sources basés sur une ou plusieurs expressions booléennes séparées par des opérateurs AND et OR logiques (`&&` ou <code>&#124;&#124;</code>).</span><span class="sxs-lookup"><span data-stu-id="69d72-111">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="69d72-112">select</span><span class="sxs-lookup"><span data-stu-id="69d72-112">select</span></span>](select-clause.md)|<span data-ttu-id="69d72-113">Spécifie le type et la forme que les éléments de la séquence retournée auront une fois la requête exécutée.</span><span class="sxs-lookup"><span data-stu-id="69d72-113">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="69d72-114">groupe</span><span class="sxs-lookup"><span data-stu-id="69d72-114">group</span></span>](group-clause.md)|<span data-ttu-id="69d72-115">Regroupe les résultats de la requête d’après une valeur de clé spécifiée.</span><span class="sxs-lookup"><span data-stu-id="69d72-115">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="69d72-116">into</span><span class="sxs-lookup"><span data-stu-id="69d72-116">into</span></span>](into.md)|<span data-ttu-id="69d72-117">Fournit un identificateur qui peut servir comme référence pour les résultats d’une clause join, group ou select.</span><span class="sxs-lookup"><span data-stu-id="69d72-117">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="69d72-118">TriPar</span><span class="sxs-lookup"><span data-stu-id="69d72-118">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="69d72-119">Trie des résultats de la requête par ordre croissant ou décroissant selon le comparateur par défaut du type d’élément.</span><span class="sxs-lookup"><span data-stu-id="69d72-119">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="69d72-120">join</span><span class="sxs-lookup"><span data-stu-id="69d72-120">join</span></span>](join-clause.md)|<span data-ttu-id="69d72-121">Joint deux sources de données selon une comparaison d’égalité entre deux critères de comparaison spécifiés.</span><span class="sxs-lookup"><span data-stu-id="69d72-121">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="69d72-122">Explor</span><span class="sxs-lookup"><span data-stu-id="69d72-122">let</span></span>](let-clause.md)|<span data-ttu-id="69d72-123">Introduit une variable de portée pour stocker des résultats de sous-expression dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="69d72-123">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="69d72-124">in</span><span class="sxs-lookup"><span data-stu-id="69d72-124">in</span></span>](in.md)|<span data-ttu-id="69d72-125">Mot clé contextuel dans une clause [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69d72-125">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="69d72-126">actif</span><span class="sxs-lookup"><span data-stu-id="69d72-126">on</span></span>](on.md)|<span data-ttu-id="69d72-127">Mot clé contextuel dans une clause [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69d72-127">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="69d72-128">equals</span><span class="sxs-lookup"><span data-stu-id="69d72-128">equals</span></span>](equals.md)|<span data-ttu-id="69d72-129">Mot clé contextuel dans une clause [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69d72-129">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="69d72-130">by</span><span class="sxs-lookup"><span data-stu-id="69d72-130">by</span></span>](by.md)|<span data-ttu-id="69d72-131">Mot clé contextuel dans une clause [group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69d72-131">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="69d72-132">ascending</span><span class="sxs-lookup"><span data-stu-id="69d72-132">ascending</span></span>](ascending.md)|<span data-ttu-id="69d72-133">Mot clé contextuel dans une clause [orderby](orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69d72-133">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="69d72-134">descending</span><span class="sxs-lookup"><span data-stu-id="69d72-134">descending</span></span>](descending.md)|<span data-ttu-id="69d72-135">Mot clé contextuel dans une clause [orderby](orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69d72-135">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="69d72-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69d72-136">See also</span></span>

- [<span data-ttu-id="69d72-137">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="69d72-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="69d72-138">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="69d72-138">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="69d72-139">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="69d72-139">LINQ in C#</span></span>](../../linq/index.md)
