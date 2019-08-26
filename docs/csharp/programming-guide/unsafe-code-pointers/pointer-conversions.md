---
title: Conversions de pointeur - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 81b2110e6a571e174693fd272d1c6b4bf44dbae3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588220"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="0bd64-102">Conversions de pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="0bd64-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="0bd64-103">Le tableau suivant présente les conversions de pointeur implicites prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="0bd64-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="0bd64-104">Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.</span><span class="sxs-lookup"><span data-stu-id="0bd64-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="0bd64-105">Conversions de pointeur implicites</span><span class="sxs-lookup"><span data-stu-id="0bd64-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="0bd64-106">From</span><span class="sxs-lookup"><span data-stu-id="0bd64-106">From</span></span>|<span data-ttu-id="0bd64-107">À</span><span class="sxs-lookup"><span data-stu-id="0bd64-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="0bd64-108">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0bd64-108">Any pointer type</span></span>|<span data-ttu-id="0bd64-109">void\*</span><span class="sxs-lookup"><span data-stu-id="0bd64-109">void\*</span></span>|  
|<span data-ttu-id="0bd64-110">null</span><span class="sxs-lookup"><span data-stu-id="0bd64-110">null</span></span>|<span data-ttu-id="0bd64-111">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0bd64-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="0bd64-112">La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast.</span><span class="sxs-lookup"><span data-stu-id="0bd64-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="0bd64-113">Le tableau suivant liste ces conversions.</span><span class="sxs-lookup"><span data-stu-id="0bd64-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="0bd64-114">Conversions de pointeur explicites</span><span class="sxs-lookup"><span data-stu-id="0bd64-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="0bd64-115">From</span><span class="sxs-lookup"><span data-stu-id="0bd64-115">From</span></span>|<span data-ttu-id="0bd64-116">À</span><span class="sxs-lookup"><span data-stu-id="0bd64-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="0bd64-117">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0bd64-117">Any pointer type</span></span>|<span data-ttu-id="0bd64-118">Tout autre type pointeur</span><span class="sxs-lookup"><span data-stu-id="0bd64-118">Any other pointer type</span></span>|  
|<span data-ttu-id="0bd64-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="0bd64-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="0bd64-120">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0bd64-120">Any pointer type</span></span>|  
|<span data-ttu-id="0bd64-121">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0bd64-121">Any pointer type</span></span>|<span data-ttu-id="0bd64-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="0bd64-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0bd64-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="0bd64-123">Example</span></span>  
 <span data-ttu-id="0bd64-124">Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`.</span><span class="sxs-lookup"><span data-stu-id="0bd64-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="0bd64-125">Notez que le pointeur pointe vers l’octet traité le plus faible de la variable.</span><span class="sxs-lookup"><span data-stu-id="0bd64-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="0bd64-126">Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.</span><span class="sxs-lookup"><span data-stu-id="0bd64-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0bd64-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bd64-127">See also</span></span>

- [<span data-ttu-id="0bd64-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0bd64-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0bd64-129">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="0bd64-129">Pointer types</span></span>](./pointer-types.md)
- [<span data-ttu-id="0bd64-130">Types</span><span class="sxs-lookup"><span data-stu-id="0bd64-130">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="0bd64-131">unsafe</span><span class="sxs-lookup"><span data-stu-id="0bd64-131">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="0bd64-132">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="0bd64-132">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="0bd64-133">stackalloc</span><span class="sxs-lookup"><span data-stu-id="0bd64-133">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
