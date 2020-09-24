---
description: Directives de préprocesseur C#
title: Directives de préprocesseur C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 210a024a8062f5070b2a500384f51b37c9d802c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157952"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="f649f-103">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="f649f-103">C# preprocessor directives</span></span>

<span data-ttu-id="f649f-104">Cette section contient des informations sur les directives de préprocesseur C# :</span><span class="sxs-lookup"><span data-stu-id="f649f-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="f649f-105">#if</span><span class="sxs-lookup"><span data-stu-id="f649f-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="f649f-106">#else</span><span class="sxs-lookup"><span data-stu-id="f649f-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="f649f-107">#elif</span><span class="sxs-lookup"><span data-stu-id="f649f-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="f649f-108">#endif</span><span class="sxs-lookup"><span data-stu-id="f649f-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="f649f-109">#define</span><span class="sxs-lookup"><span data-stu-id="f649f-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="f649f-110">#undef</span><span class="sxs-lookup"><span data-stu-id="f649f-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="f649f-111">#warning</span><span class="sxs-lookup"><span data-stu-id="f649f-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="f649f-112">#error</span><span class="sxs-lookup"><span data-stu-id="f649f-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="f649f-113">#line</span><span class="sxs-lookup"><span data-stu-id="f649f-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="f649f-114">#region</span><span class="sxs-lookup"><span data-stu-id="f649f-114">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="f649f-115">#endregion</span><span class="sxs-lookup"><span data-stu-id="f649f-115">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="f649f-116">#pragma</span><span class="sxs-lookup"><span data-stu-id="f649f-116">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="f649f-117">AVERTISSEMENT #pragma</span><span class="sxs-lookup"><span data-stu-id="f649f-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="f649f-118">somme de contrôle #pragma</span><span class="sxs-lookup"><span data-stu-id="f649f-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="f649f-119">Pour plus d’informations et des exemples, consultez les rubriques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f649f-119">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="f649f-120">Bien que le compilateur n’ait pas de préprocesseur distinct, les directives décrites dans cette section sont traitées comme si c’était le cas.</span><span class="sxs-lookup"><span data-stu-id="f649f-120">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="f649f-121">Elles sont utilisées pour faciliter la compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="f649f-121">They are used to help in conditional compilation.</span></span> <span data-ttu-id="f649f-122">Contrairement aux directives C et C++, vous ne pouvez pas les utiliser pour créer des macros.</span><span class="sxs-lookup"><span data-stu-id="f649f-122">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="f649f-123">Une directive de préprocesseur doit être la seule instruction sur une ligne.</span><span class="sxs-lookup"><span data-stu-id="f649f-123">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="f649f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f649f-124">See also</span></span>

- [<span data-ttu-id="f649f-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f649f-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f649f-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f649f-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
