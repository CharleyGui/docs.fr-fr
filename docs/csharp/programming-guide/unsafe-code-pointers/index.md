---
title: Pointeurs et code unsafe - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 9f4e74e1e8fa71d1492a10162191822c1edfb635
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608035"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="043f8-102">Pointeurs et code unsafe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="043f8-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="043f8-103">Pour conserver la sécurité des types, par défaut, C# ne prend pas en charge les opérations arithmétiques sur les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="043f8-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="043f8-104">Cependant, en utilisant le mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md), vous pouvez définir un contexte non sécurisé dans lequel des pointeurs peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="043f8-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="043f8-105">Pour plus d’informations sur les pointeurs, consultez la rubrique [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="043f8-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="043f8-106">Dans le common language runtime (CLR), le code non sécurisé est appelé « code non vérifiable ».</span><span class="sxs-lookup"><span data-stu-id="043f8-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="043f8-107">Le code non sécurisé en C# n’est pas nécessairement dangereux : il s’agit simplement de code dont la sécurité ne peut pas être vérifiée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="043f8-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="043f8-108">Le CLR exécute du code non sécurisé seulement s’il se trouve dans un assembly entièrement fiable.</span><span class="sxs-lookup"><span data-stu-id="043f8-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="043f8-109">Si vous utilisez du code non sécurisé, il vous incombe de vérifier que votre code n’introduit pas de risques de sécurité ni d’erreurs de pointeur.</span><span class="sxs-lookup"><span data-stu-id="043f8-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="043f8-110">Vue d’ensemble du code non sécurisé</span><span class="sxs-lookup"><span data-stu-id="043f8-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="043f8-111">Le code non sécurisé a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="043f8-111">Unsafe code has the following properties:</span></span>  
  
- <span data-ttu-id="043f8-112">Les méthodes, les types et les blocs de code peuvent être définis comme non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="043f8-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
- <span data-ttu-id="043f8-113">Dans certains cas, le code non sécurisé peut augmenter les performances d’une application en supprimant les vérifications des limites des tableaux.</span><span class="sxs-lookup"><span data-stu-id="043f8-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
- <span data-ttu-id="043f8-114">Du code non sécurisé est obligatoire quand vous appelez des fonctions natives nécessitant des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="043f8-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
- <span data-ttu-id="043f8-115">L’utilisation de code non sécurisé introduit des risques pour la sécurité et la stabilité.</span><span class="sxs-lookup"><span data-stu-id="043f8-115">Using unsafe code introduces security and stability risks.</span></span>  
  
- <span data-ttu-id="043f8-116">Pour que C# compile du code non sécurisé, l’application doit être compilée avec [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="043f8-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="043f8-117">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="043f8-117">Related Sections</span></span>  
 <span data-ttu-id="043f8-118">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="043f8-118">For more information, see:</span></span>  
  
- [<span data-ttu-id="043f8-119">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="043f8-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
- [<span data-ttu-id="043f8-120">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="043f8-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
- [<span data-ttu-id="043f8-121">Guide pratique pour utiliser des pointeurs pour copier un tableau d’octets</span><span class="sxs-lookup"><span data-stu-id="043f8-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
- [<span data-ttu-id="043f8-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="043f8-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="043f8-123">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="043f8-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="043f8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="043f8-124">See also</span></span>

- [<span data-ttu-id="043f8-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="043f8-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
