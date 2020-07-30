---
title: Conversions de pointeur - Guide de programmation C#
description: En savoir plus sur les conversions de pointeur. Consultez les tableaux des conversions de pointeur implicites et explicites, des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: c39be5cb52964abbea5bc5636c6fa74d8411a331
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382085"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="a516e-104">Conversions de pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a516e-104">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="a516e-105">Le tableau suivant présente les conversions de pointeur implicites prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="a516e-105">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="a516e-106">Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.</span><span class="sxs-lookup"><span data-stu-id="a516e-106">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="a516e-107">Conversions de pointeur implicites</span><span class="sxs-lookup"><span data-stu-id="a516e-107">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="a516e-108">À partir</span><span class="sxs-lookup"><span data-stu-id="a516e-108">From</span></span>|<span data-ttu-id="a516e-109">À</span><span class="sxs-lookup"><span data-stu-id="a516e-109">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="a516e-110">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="a516e-110">Any pointer type</span></span>|<span data-ttu-id="a516e-111">void\*</span><span class="sxs-lookup"><span data-stu-id="a516e-111">void\*</span></span>|  
|<span data-ttu-id="a516e-112">null</span><span class="sxs-lookup"><span data-stu-id="a516e-112">null</span></span>|<span data-ttu-id="a516e-113">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="a516e-113">Any pointer type</span></span>|  
  
 <span data-ttu-id="a516e-114">La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast.</span><span class="sxs-lookup"><span data-stu-id="a516e-114">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="a516e-115">Le tableau suivant liste ces conversions.</span><span class="sxs-lookup"><span data-stu-id="a516e-115">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="a516e-116">Conversions de pointeur explicites</span><span class="sxs-lookup"><span data-stu-id="a516e-116">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="a516e-117">À partir</span><span class="sxs-lookup"><span data-stu-id="a516e-117">From</span></span>|<span data-ttu-id="a516e-118">À</span><span class="sxs-lookup"><span data-stu-id="a516e-118">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="a516e-119">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="a516e-119">Any pointer type</span></span>|<span data-ttu-id="a516e-120">Tout autre type pointeur</span><span class="sxs-lookup"><span data-stu-id="a516e-120">Any other pointer type</span></span>|  
|<span data-ttu-id="a516e-121">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="a516e-121">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="a516e-122">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="a516e-122">Any pointer type</span></span>|  
|<span data-ttu-id="a516e-123">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="a516e-123">Any pointer type</span></span>|<span data-ttu-id="a516e-124">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="a516e-124">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a516e-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="a516e-125">Example</span></span>  
 <span data-ttu-id="a516e-126">Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`.</span><span class="sxs-lookup"><span data-stu-id="a516e-126">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="a516e-127">Notez que le pointeur pointe vers l’octet traité le plus faible de la variable.</span><span class="sxs-lookup"><span data-stu-id="a516e-127">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="a516e-128">Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.</span><span class="sxs-lookup"><span data-stu-id="a516e-128">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a516e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a516e-129">See also</span></span>

- [<span data-ttu-id="a516e-130">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a516e-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a516e-131">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="a516e-131">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="a516e-132">Types référence</span><span class="sxs-lookup"><span data-stu-id="a516e-132">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="a516e-133">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="a516e-133">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="a516e-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="a516e-134">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="a516e-135">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="a516e-135">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="a516e-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="a516e-136">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
