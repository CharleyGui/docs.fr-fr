---
title: Comparaison entre propriétés et indexeurs - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 31e6b4b10a6ffec031a2e41a2bd16c843f802fb7
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671679"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="b7af8-102">Comparaison entre propriétés et indexeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b7af8-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="b7af8-103">Les indexeurs sont semblables aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="b7af8-103">Indexers are like properties.</span></span> <span data-ttu-id="b7af8-104">À l’exception des différences répertoriées dans le tableau suivant, toutes les règles définies pour les accesseurs des propriétés s’appliquent également aux accesseurs des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="b7af8-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="b7af8-105">Property</span><span class="sxs-lookup"><span data-stu-id="b7af8-105">Property</span></span>|<span data-ttu-id="b7af8-106">Indexeur</span><span class="sxs-lookup"><span data-stu-id="b7af8-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="b7af8-107">Permet aux méthodes d’être appelées comme si elles étaient des membres de données publics.</span><span class="sxs-lookup"><span data-stu-id="b7af8-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="b7af8-108">Permet aux éléments d’une collection interne d’un objet d’être accessibles à l’aide de la notation de tableau sur l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="b7af8-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="b7af8-109">Accessible par le biais d’un nom simple.</span><span class="sxs-lookup"><span data-stu-id="b7af8-109">Accessed through a simple name.</span></span>|<span data-ttu-id="b7af8-110">Accessible par le biais d’un index.</span><span class="sxs-lookup"><span data-stu-id="b7af8-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="b7af8-111">Peut être un membre statique ou un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="b7af8-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="b7af8-112">Doit être un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="b7af8-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="b7af8-113">Un accesseur [get](../../../csharp/language-reference/keywords/get.md) d’une propriété n’a aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="b7af8-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="b7af8-114">Un accesseur `get` d’un indexeur possède la même liste de paramètres formels que l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="b7af8-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="b7af8-115">Un accesseur [set](../../../csharp/language-reference/keywords/set.md) d’une propriété contient le paramètre `value` implicite.</span><span class="sxs-lookup"><span data-stu-id="b7af8-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="b7af8-116">Un accesseur `set` d’un indexeur possède la même liste de paramètres formels que l’indexeur, outre le paramètre [value](../../../csharp/language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="b7af8-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="b7af8-117">Prend en charge la syntaxe abrégée avec les [propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b7af8-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="b7af8-118">Prend en charge les membres expression-bodied pour les indexeurs get-only.</span><span class="sxs-lookup"><span data-stu-id="b7af8-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7af8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7af8-119">See also</span></span>

- [<span data-ttu-id="b7af8-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b7af8-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b7af8-121">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="b7af8-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="b7af8-122">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b7af8-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
