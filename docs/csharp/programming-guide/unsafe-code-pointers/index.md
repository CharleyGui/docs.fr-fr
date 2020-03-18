---
title: Pointeurs et code unsafe - Guide de programmation C#
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
ms.openlocfilehash: 013af4e55c8fc396bbc92058d7fb454484f3263e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711829"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="7c404-102">Pointeurs et code unsafe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7c404-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="7c404-103">Pour conserver la sécurité des types, par défaut, C# ne prend pas en charge les opérations arithmétiques sur les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="7c404-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="7c404-104">Cependant, en utilisant le mot clé [unsafe](../../language-reference/keywords/unsafe.md), vous pouvez définir un contexte non sécurisé dans lequel des pointeurs peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="7c404-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="7c404-105">Pour en savoir plus sur les pointeurs, consultez la rubrique [Types de pointeur](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="7c404-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c404-106">Dans le common language runtime (CLR), le code non sécurisé est appelé « code non vérifiable ».</span><span class="sxs-lookup"><span data-stu-id="7c404-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="7c404-107">Le code non sécurisé en C# n’est pas nécessairement dangereux : il s’agit simplement de code dont la sécurité ne peut pas être vérifiée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="7c404-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="7c404-108">Le CLR exécute du code non sécurisé seulement s’il se trouve dans un assembly entièrement fiable.</span><span class="sxs-lookup"><span data-stu-id="7c404-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="7c404-109">Si vous utilisez du code non sécurisé, il vous incombe de vérifier que votre code n’introduit pas de risques de sécurité ni d’erreurs de pointeur.</span><span class="sxs-lookup"><span data-stu-id="7c404-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="7c404-110">Vue d’ensemble du code unsafe</span><span class="sxs-lookup"><span data-stu-id="7c404-110">Unsafe code overview</span></span>

<span data-ttu-id="7c404-111">Le code non sécurisé a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c404-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="7c404-112">Les méthodes, les types et les blocs de code peuvent être définis comme non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="7c404-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="7c404-113">Dans certains cas, le code non sécurisé peut augmenter les performances d’une application en supprimant les vérifications des limites des tableaux.</span><span class="sxs-lookup"><span data-stu-id="7c404-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="7c404-114">Du code non sécurisé est obligatoire quand vous appelez des fonctions natives nécessitant des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="7c404-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="7c404-115">L’utilisation de code non sécurisé introduit des risques pour la sécurité et la stabilité.</span><span class="sxs-lookup"><span data-stu-id="7c404-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="7c404-116">Le code qui contient des blocs unsafe doit être compilé avec l’option de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7c404-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="7c404-117">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="7c404-117">Related sections</span></span>

<span data-ttu-id="7c404-118">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c404-118">For more information, see:</span></span>

- [<span data-ttu-id="7c404-119">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="7c404-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="7c404-120">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="7c404-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="7c404-121">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7c404-121">C# language specification</span></span>

<span data-ttu-id="7c404-122">Pour en savoir plus, consultez la rubrique [Code unsafe](~/_csharplang/spec/unsafe-code.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7c404-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7c404-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c404-123">See also</span></span>

- [<span data-ttu-id="7c404-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7c404-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7c404-125">Dangereux</span><span class="sxs-lookup"><span data-stu-id="7c404-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
