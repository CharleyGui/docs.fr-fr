---
title: Conversions de pointeur - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745365"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="224df-102">Conversions de pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="224df-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="224df-103">Le tableau suivant présente les conversions de pointeur implicites prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="224df-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="224df-104">Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.</span><span class="sxs-lookup"><span data-stu-id="224df-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="224df-105">Conversions de pointeur implicites</span><span class="sxs-lookup"><span data-stu-id="224df-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="224df-106">De</span><span class="sxs-lookup"><span data-stu-id="224df-106">From</span></span>|<span data-ttu-id="224df-107">Pour</span><span class="sxs-lookup"><span data-stu-id="224df-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="224df-108">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="224df-108">Any pointer type</span></span>|<span data-ttu-id="224df-109">void\*</span><span class="sxs-lookup"><span data-stu-id="224df-109">void\*</span></span>|  
|<span data-ttu-id="224df-110">null</span><span class="sxs-lookup"><span data-stu-id="224df-110">null</span></span>|<span data-ttu-id="224df-111">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="224df-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="224df-112">La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast.</span><span class="sxs-lookup"><span data-stu-id="224df-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="224df-113">Le tableau suivant liste ces conversions.</span><span class="sxs-lookup"><span data-stu-id="224df-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="224df-114">Conversions de pointeur explicites</span><span class="sxs-lookup"><span data-stu-id="224df-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="224df-115">De</span><span class="sxs-lookup"><span data-stu-id="224df-115">From</span></span>|<span data-ttu-id="224df-116">Pour</span><span class="sxs-lookup"><span data-stu-id="224df-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="224df-117">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="224df-117">Any pointer type</span></span>|<span data-ttu-id="224df-118">Tout autre type pointeur</span><span class="sxs-lookup"><span data-stu-id="224df-118">Any other pointer type</span></span>|  
|<span data-ttu-id="224df-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="224df-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="224df-120">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="224df-120">Any pointer type</span></span>|  
|<span data-ttu-id="224df-121">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="224df-121">Any pointer type</span></span>|<span data-ttu-id="224df-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="224df-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="224df-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="224df-123">Example</span></span>  
 <span data-ttu-id="224df-124">Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`.</span><span class="sxs-lookup"><span data-stu-id="224df-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="224df-125">Notez que le pointeur pointe vers l’octet traité le plus faible de la variable.</span><span class="sxs-lookup"><span data-stu-id="224df-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="224df-126">Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.</span><span class="sxs-lookup"><span data-stu-id="224df-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="224df-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="224df-127">See also</span></span>

- [<span data-ttu-id="224df-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="224df-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="224df-129">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="224df-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="224df-130">Types référence</span><span class="sxs-lookup"><span data-stu-id="224df-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="224df-131">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="224df-131">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="224df-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="224df-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="224df-133">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="224df-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="224df-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="224df-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
