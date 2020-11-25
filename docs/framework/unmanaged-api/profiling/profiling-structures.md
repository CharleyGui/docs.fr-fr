---
title: Structures de profilage
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 3f832850fac918a568d02e9ef2f1e5b140ffc04f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722750"
---
# <a name="profiling-structures"></a><span data-ttu-id="50cde-102">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="50cde-102">Profiling Structures</span></span>

<span data-ttu-id="50cde-103">Cette section décrit les structures non managées utilisées par l'API de profilage.</span><span class="sxs-lookup"><span data-stu-id="50cde-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50cde-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="50cde-104">In This Section</span></span>  

 [<span data-ttu-id="50cde-105">COR_PRF_ASSEMBLY_REFERENCE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="50cde-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="50cde-106">Fournit au CLR (Common Language Runtime) des informations sur un assembly de référence qui doit être pris en compte lors d'un parcours de fermeture des références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="50cde-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="50cde-107">COR_PRF_CODE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="50cde-107">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="50cde-108">Représente un bloc contigu de code natif stocké en mémoire.</span><span class="sxs-lookup"><span data-stu-id="50cde-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="50cde-109">COR_PRF_EX_CLAUSE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="50cde-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="50cde-110">Stocke des informations sur une instance de clause d'exception spécifique et sa trame associée.</span><span class="sxs-lookup"><span data-stu-id="50cde-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="50cde-111">COR_PRF_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="50cde-111">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="50cde-112">Fournit une représentation unique d'une fonction en combinant son ID avec l'ID de sa version recompilée.</span><span class="sxs-lookup"><span data-stu-id="50cde-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="50cde-113">COR_PRF_FUNCTION_ARGUMENT_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="50cde-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="50cde-114">Représente les arguments d’une fonction, selon un ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="50cde-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="50cde-115">COR_PRF_FUNCTION_ARGUMENT_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="50cde-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="50cde-116">Représente un bloc d’arguments de fonction stockés de façon contiguë en mémoire selon un ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="50cde-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="50cde-117">COR_PRF_GC_GENERATION_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="50cde-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="50cde-118">Décrit une plage (un bloc) de mémoire qui va faire l'objet d'une récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="50cde-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="50cde-119">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="50cde-119">Related Sections</span></span>  

 <span data-ttu-id="50cde-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="50cde-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="50cde-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="50cde-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="50cde-122">Vue d’ensemble du profilage</span><span class="sxs-lookup"><span data-stu-id="50cde-122">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="50cde-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="50cde-123">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="50cde-124">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="50cde-124">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="50cde-125">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="50cde-125">Profiling Enumerations</span></span>](profiling-enumerations.md)
