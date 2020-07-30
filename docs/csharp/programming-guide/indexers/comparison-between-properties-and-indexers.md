---
title: Comparaison entre propriétés et indexeurs - Guide de programmation C#
description: Comparez la manière dont les indexeurs en C# sont similaires aux propriétés. À l’exception des différences, les règles définies pour les accesseurs de propriété s’appliquent aux accesseurs de l’indexeur.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: b83ce3db3d4b53fb7bcc5f3b3cd603a375d5d473
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299173"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="36e75-104">Comparaison entre propriétés et indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="36e75-104">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="36e75-105">Les indexeurs sont semblables aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="36e75-105">Indexers are like properties.</span></span> <span data-ttu-id="36e75-106">À l’exception des différences répertoriées dans le tableau suivant, toutes les règles définies pour les accesseurs des propriétés s’appliquent également aux accesseurs des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="36e75-106">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="36e75-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="36e75-107">Property</span></span>|<span data-ttu-id="36e75-108">Indexeur</span><span class="sxs-lookup"><span data-stu-id="36e75-108">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="36e75-109">Permet aux méthodes d’être appelées comme si elles étaient des membres de données publics.</span><span class="sxs-lookup"><span data-stu-id="36e75-109">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="36e75-110">Permet aux éléments d’une collection interne d’un objet d’être accessibles à l’aide de la notation de tableau sur l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="36e75-110">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="36e75-111">Accessible par le biais d’un nom simple.</span><span class="sxs-lookup"><span data-stu-id="36e75-111">Accessed through a simple name.</span></span>|<span data-ttu-id="36e75-112">Accessible par le biais d’un index.</span><span class="sxs-lookup"><span data-stu-id="36e75-112">Accessed through an index.</span></span>|  
|<span data-ttu-id="36e75-113">Peut être un membre statique ou un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="36e75-113">Can be a static or an instance member.</span></span>|<span data-ttu-id="36e75-114">Doit être un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="36e75-114">Must be an instance member.</span></span>|  
|<span data-ttu-id="36e75-115">Un accesseur [get](../../language-reference/keywords/get.md) d’une propriété n’a aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="36e75-115">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="36e75-116">Un accesseur `get` d’un indexeur possède la même liste de paramètres formels que l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="36e75-116">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="36e75-117">Un accesseur [set](../../language-reference/keywords/set.md) d’une propriété contient le paramètre `value` implicite.</span><span class="sxs-lookup"><span data-stu-id="36e75-117">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="36e75-118">Un accesseur `set` d’un indexeur possède la même liste de paramètres formels que l’indexeur, outre le paramètre [value](../../language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="36e75-118">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="36e75-119">Prend en charge la syntaxe abrégée avec les [propriétés implémentées automatiquement](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="36e75-119">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="36e75-120">Prend en charge les membres expression-bodied pour les indexeurs get-only.</span><span class="sxs-lookup"><span data-stu-id="36e75-120">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36e75-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36e75-121">See also</span></span>

- [<span data-ttu-id="36e75-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="36e75-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="36e75-123">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="36e75-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="36e75-124">Propriétés</span><span class="sxs-lookup"><span data-stu-id="36e75-124">Properties</span></span>](../classes-and-structs/properties.md)
