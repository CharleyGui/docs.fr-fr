---
title: Comparaison entre propriétés et indexeurs - Guide de programmation C#
description: Comparez la manière dont les indexeurs en C# sont similaires aux propriétés. À l’exception des différences, les règles définies pour les accesseurs de propriété s’appliquent aux accesseurs de l’indexeur.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: fff20ca965e7614d26f7da32321a829d13292389
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192527"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="fe107-104">Comparaison entre propriétés et indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fe107-104">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="fe107-105">Les indexeurs sont semblables aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="fe107-105">Indexers are like properties.</span></span> <span data-ttu-id="fe107-106">À l’exception des différences répertoriées dans le tableau suivant, toutes les règles définies pour les accesseurs des propriétés s’appliquent également aux accesseurs des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="fe107-106">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="fe107-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="fe107-107">Property</span></span>|<span data-ttu-id="fe107-108">Indexation</span><span class="sxs-lookup"><span data-stu-id="fe107-108">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="fe107-109">Permet aux méthodes d’être appelées comme si elles étaient des membres de données publics.</span><span class="sxs-lookup"><span data-stu-id="fe107-109">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="fe107-110">Permet aux éléments d’une collection interne d’un objet d’être accessibles à l’aide de la notation de tableau sur l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="fe107-110">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="fe107-111">Accessible par le biais d’un nom simple.</span><span class="sxs-lookup"><span data-stu-id="fe107-111">Accessed through a simple name.</span></span>|<span data-ttu-id="fe107-112">Accessible par le biais d’un index.</span><span class="sxs-lookup"><span data-stu-id="fe107-112">Accessed through an index.</span></span>|  
|<span data-ttu-id="fe107-113">Peut être un membre statique ou un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="fe107-113">Can be a static or an instance member.</span></span>|<span data-ttu-id="fe107-114">Doit être un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="fe107-114">Must be an instance member.</span></span>|  
|<span data-ttu-id="fe107-115">Un accesseur [get](../../language-reference/keywords/get.md) d’une propriété n’a aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="fe107-115">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="fe107-116">Un accesseur `get` d’un indexeur possède la même liste de paramètres formels que l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="fe107-116">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="fe107-117">Un accesseur [set](../../language-reference/keywords/set.md) d’une propriété contient le paramètre `value` implicite.</span><span class="sxs-lookup"><span data-stu-id="fe107-117">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="fe107-118">Un accesseur `set` d’un indexeur possède la même liste de paramètres formels que l’indexeur, outre le paramètre [value](../../language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="fe107-118">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="fe107-119">Prend en charge la syntaxe abrégée avec les [propriétés implémentées automatiquement](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="fe107-119">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="fe107-120">Prend en charge les membres expression-bodied pour les indexeurs get-only.</span><span class="sxs-lookup"><span data-stu-id="fe107-120">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe107-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe107-121">See also</span></span>

- [<span data-ttu-id="fe107-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fe107-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fe107-123">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="fe107-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="fe107-124">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fe107-124">Properties</span></span>](../classes-and-structs/properties.md)
