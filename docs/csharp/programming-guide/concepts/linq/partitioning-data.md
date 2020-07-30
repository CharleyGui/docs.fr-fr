---
title: Partitionnement des données (C#)
description: Découvrez comment partitionner des données dans LINQ. Affichez une illustration montrant les résultats des opérations de partitionnement.
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 3c85eaec2dc01b683234a27714750354982be440
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302605"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="9a9a9-104">Partitionnement des données (C#)</span><span class="sxs-lookup"><span data-stu-id="9a9a9-104">Partitioning Data (C#)</span></span>
<span data-ttu-id="9a9a9-105">Le partitionnement dans LINQ désigne l’opération consistant à diviser une séquence d’entrée en deux sections, sans réorganiser les éléments, puis à retourner l’une des sections.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-105">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="9a9a9-106">L’illustration suivante montre les résultats de trois opérations de partitionnement différentes sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-106">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="9a9a9-107">La première opération retourne les trois premiers éléments de la séquence.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-107">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="9a9a9-108">La deuxième opération ignore les trois premiers éléments et retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-108">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="9a9a9-109">La troisième opération ignore les deux premiers éléments de la séquence et retourne les trois éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-109">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Illustration des trois opérations de partitionnement LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="9a9a9-111">Les méthodes d’opérateurs de requête standard qui partitionnent des séquences sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-111">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="9a9a9-112">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="9a9a9-112">Operators</span></span>  
  
|<span data-ttu-id="9a9a9-113">Nom de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="9a9a9-113">Operator Name</span></span>|<span data-ttu-id="9a9a9-114">Description</span><span class="sxs-lookup"><span data-stu-id="9a9a9-114">Description</span></span>|<span data-ttu-id="9a9a9-115">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="9a9a9-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="9a9a9-116">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="9a9a9-116">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="9a9a9-117">Ignorer</span><span class="sxs-lookup"><span data-stu-id="9a9a9-117">Skip</span></span>|<span data-ttu-id="9a9a9-118">Ignore les éléments jusqu’à une position spécifiée dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-118">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="9a9a9-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9a9a9-120">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="9a9a9-120">SkipWhile</span></span>|<span data-ttu-id="9a9a9-121">Ignore les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-121">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="9a9a9-122">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9a9a9-123">Take</span><span class="sxs-lookup"><span data-stu-id="9a9a9-123">Take</span></span>|<span data-ttu-id="9a9a9-124">Prend les éléments jusqu’à une position spécifiée dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-124">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="9a9a9-125">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9a9a9-126">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="9a9a9-126">TakeWhile</span></span>|<span data-ttu-id="9a9a9-127">Prend les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-127">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="9a9a9-128">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="9a9a9-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="9a9a9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a9a9-129">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9a9a9-130">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="9a9a9-130">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
