---
title: Pointeurs et code unsafe - Guide de programmation C#
Description: En savoir plus sur le code et les pointeurs non sécurisés. C# ne prend pas en charge les pointeurs, mais vous pouvez définir un contexte unsafe dans lequel les pointeurs peuvent être utilisés avec un mot clé unsafe.
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
ms.openlocfilehash: 5684a97ed6f7b6632d8fe3d52747d9187c4b8cbc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381773"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="0535a-104">Pointeurs et code unsafe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="0535a-104">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="0535a-105">Pour conserver la sécurité des types, par défaut, C# ne prend pas en charge les opérations arithmétiques sur les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="0535a-105">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="0535a-106">Cependant, en utilisant le mot clé [unsafe](../../language-reference/keywords/unsafe.md), vous pouvez définir un contexte non sécurisé dans lequel des pointeurs peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="0535a-106">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="0535a-107">Pour en savoir plus sur les pointeurs, consultez la rubrique [Types de pointeur](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="0535a-107">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0535a-108">Dans le common language runtime (CLR), le code non sécurisé est appelé « code non vérifiable ».</span><span class="sxs-lookup"><span data-stu-id="0535a-108">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="0535a-109">Le code non sécurisé en C# n’est pas nécessairement dangereux : il s’agit simplement de code dont la sécurité ne peut pas être vérifiée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="0535a-109">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="0535a-110">Le CLR exécute du code non sécurisé seulement s’il se trouve dans un assembly entièrement fiable.</span><span class="sxs-lookup"><span data-stu-id="0535a-110">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="0535a-111">Si vous utilisez du code non sécurisé, il vous incombe de vérifier que votre code n’introduit pas de risques de sécurité ni d’erreurs de pointeur.</span><span class="sxs-lookup"><span data-stu-id="0535a-111">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="0535a-112">Vue d’ensemble du code unsafe</span><span class="sxs-lookup"><span data-stu-id="0535a-112">Unsafe code overview</span></span>

<span data-ttu-id="0535a-113">Le code non sécurisé a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="0535a-113">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="0535a-114">Les méthodes, les types et les blocs de code peuvent être définis comme non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="0535a-114">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="0535a-115">Dans certains cas, le code non sécurisé peut augmenter les performances d’une application en supprimant les vérifications des limites des tableaux.</span><span class="sxs-lookup"><span data-stu-id="0535a-115">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="0535a-116">Du code non sécurisé est obligatoire quand vous appelez des fonctions natives nécessitant des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="0535a-116">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="0535a-117">L’utilisation de code non sécurisé introduit des risques pour la sécurité et la stabilité.</span><span class="sxs-lookup"><span data-stu-id="0535a-117">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="0535a-118">Le code qui contient des blocs unsafe doit être compilé avec l’option de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="0535a-118">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="0535a-119">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0535a-119">Related sections</span></span>

<span data-ttu-id="0535a-120">Pour plus d’informations, consultez :</span><span class="sxs-lookup"><span data-stu-id="0535a-120">For more information, see:</span></span>

- [<span data-ttu-id="0535a-121">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="0535a-121">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="0535a-122">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="0535a-122">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="0535a-123">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="0535a-123">C# language specification</span></span>

<span data-ttu-id="0535a-124">Pour en savoir plus, consultez la rubrique [Code unsafe](~/_csharplang/spec/unsafe-code.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0535a-124">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0535a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0535a-125">See also</span></span>

- [<span data-ttu-id="0535a-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0535a-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0535a-127">unsafe</span><span class="sxs-lookup"><span data-stu-id="0535a-127">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
