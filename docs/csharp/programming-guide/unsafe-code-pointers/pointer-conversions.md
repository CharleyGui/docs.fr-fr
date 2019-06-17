---
title: Conversions de pointeur - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 3cef2f2d2af2d285504daea14aa57c55b9e9a21b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833458"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="3d155-102">Conversions de pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3d155-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="3d155-103">Le tableau suivant présente les conversions de pointeur implicites prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="3d155-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="3d155-104">Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.</span><span class="sxs-lookup"><span data-stu-id="3d155-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="3d155-105">Conversions de pointeur implicites</span><span class="sxs-lookup"><span data-stu-id="3d155-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="3d155-106">From</span><span class="sxs-lookup"><span data-stu-id="3d155-106">From</span></span>|<span data-ttu-id="3d155-107">À</span><span class="sxs-lookup"><span data-stu-id="3d155-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="3d155-108">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="3d155-108">Any pointer type</span></span>|<span data-ttu-id="3d155-109">void\*</span><span class="sxs-lookup"><span data-stu-id="3d155-109">void\*</span></span>|  
|<span data-ttu-id="3d155-110">null</span><span class="sxs-lookup"><span data-stu-id="3d155-110">null</span></span>|<span data-ttu-id="3d155-111">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="3d155-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="3d155-112">La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast.</span><span class="sxs-lookup"><span data-stu-id="3d155-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="3d155-113">Le tableau suivant liste ces conversions.</span><span class="sxs-lookup"><span data-stu-id="3d155-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="3d155-114">Conversions de pointeur explicites</span><span class="sxs-lookup"><span data-stu-id="3d155-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="3d155-115">From</span><span class="sxs-lookup"><span data-stu-id="3d155-115">From</span></span>|<span data-ttu-id="3d155-116">À</span><span class="sxs-lookup"><span data-stu-id="3d155-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="3d155-117">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="3d155-117">Any pointer type</span></span>|<span data-ttu-id="3d155-118">Tout autre type pointeur</span><span class="sxs-lookup"><span data-stu-id="3d155-118">Any other pointer type</span></span>|  
|<span data-ttu-id="3d155-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="3d155-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="3d155-120">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="3d155-120">Any pointer type</span></span>|  
|<span data-ttu-id="3d155-121">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="3d155-121">Any pointer type</span></span>|<span data-ttu-id="3d155-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="3d155-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3d155-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="3d155-123">Example</span></span>  
 <span data-ttu-id="3d155-124">Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`.</span><span class="sxs-lookup"><span data-stu-id="3d155-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="3d155-125">Notez que le pointeur pointe vers l’octet traité le plus faible de la variable.</span><span class="sxs-lookup"><span data-stu-id="3d155-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="3d155-126">Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.</span><span class="sxs-lookup"><span data-stu-id="3d155-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3d155-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d155-127">See also</span></span>

- [<span data-ttu-id="3d155-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3d155-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3d155-129">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="3d155-129">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="3d155-130">Types</span><span class="sxs-lookup"><span data-stu-id="3d155-130">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="3d155-131">unsafe</span><span class="sxs-lookup"><span data-stu-id="3d155-131">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="3d155-132">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="3d155-132">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="3d155-133">stackalloc</span><span class="sxs-lookup"><span data-stu-id="3d155-133">stackalloc</span></span>](../../../csharp/language-reference/operators/stackalloc.md)
