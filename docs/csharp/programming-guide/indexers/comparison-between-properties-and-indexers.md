---
title: Comparaison entre propriétés et indexeurs - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712128"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="8b9db-102">Comparaison entre propriétés et indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8b9db-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="8b9db-103">Les indexeurs sont semblables aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="8b9db-103">Indexers are like properties.</span></span> <span data-ttu-id="8b9db-104">À l’exception des différences répertoriées dans le tableau suivant, toutes les règles définies pour les accesseurs des propriétés s’appliquent également aux accesseurs des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="8b9db-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="8b9db-105">Propriété</span><span class="sxs-lookup"><span data-stu-id="8b9db-105">Property</span></span>|<span data-ttu-id="8b9db-106">Indexeur</span><span class="sxs-lookup"><span data-stu-id="8b9db-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="8b9db-107">Permet aux méthodes d’être appelées comme si elles étaient des membres de données publics.</span><span class="sxs-lookup"><span data-stu-id="8b9db-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="8b9db-108">Permet aux éléments d’une collection interne d’un objet d’être accessibles à l’aide de la notation de tableau sur l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="8b9db-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="8b9db-109">Accessible par le biais d’un nom simple.</span><span class="sxs-lookup"><span data-stu-id="8b9db-109">Accessed through a simple name.</span></span>|<span data-ttu-id="8b9db-110">Accessible par le biais d’un index.</span><span class="sxs-lookup"><span data-stu-id="8b9db-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="8b9db-111">Peut être un membre statique ou un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="8b9db-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="8b9db-112">Doit être un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="8b9db-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="8b9db-113">Un accesseur [get](../../language-reference/keywords/get.md) d’une propriété n’a aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="8b9db-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="8b9db-114">Un accesseur `get` d’un indexeur possède la même liste de paramètres formels que l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="8b9db-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="8b9db-115">Un accesseur [set](../../language-reference/keywords/set.md) d’une propriété contient le paramètre `value` implicite.</span><span class="sxs-lookup"><span data-stu-id="8b9db-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="8b9db-116">Un accesseur `set` d’un indexeur possède la même liste de paramètres formels que l’indexeur, outre le paramètre [value](../../language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="8b9db-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="8b9db-117">Prend en charge la syntaxe abrégée avec les [propriétés implémentées automatiquement](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="8b9db-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="8b9db-118">Prend en charge les membres expression-bodied pour les indexeurs get-only.</span><span class="sxs-lookup"><span data-stu-id="8b9db-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b9db-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b9db-119">See also</span></span>

- [<span data-ttu-id="8b9db-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8b9db-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8b9db-121">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="8b9db-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="8b9db-122">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8b9db-122">Properties</span></span>](../classes-and-structs/properties.md)
