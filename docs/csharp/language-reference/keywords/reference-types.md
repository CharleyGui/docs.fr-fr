---
title: Types référence - Référence C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744517"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="3c6a7-102">Types référence (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="3c6a7-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="3c6a7-103">Il existe deux genres de types en C# : les types référence et les types valeur.</span><span class="sxs-lookup"><span data-stu-id="3c6a7-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="3c6a7-104">Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données.</span><span class="sxs-lookup"><span data-stu-id="3c6a7-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="3c6a7-105">Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable.</span><span class="sxs-lookup"><span data-stu-id="3c6a7-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="3c6a7-106">Avec les types valeur, chaque variable a sa propre copie des données et les opérations sur une variable ne peuvent pas affecter l’autre (sauf pour les variables de paramètre in, ref et out ; consultez les modificateurs de paramètre [in](in-parameter-modifier.md), [ref](ref.md) et [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="3c6a7-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="3c6a7-107">Les mots clés suivants sont utilisés pour déclarer des types référence :</span><span class="sxs-lookup"><span data-stu-id="3c6a7-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="3c6a7-108">classe</span><span class="sxs-lookup"><span data-stu-id="3c6a7-108">class</span></span>](class.md)

- [<span data-ttu-id="3c6a7-109">interface</span><span class="sxs-lookup"><span data-stu-id="3c6a7-109">interface</span></span>](interface.md)

- [<span data-ttu-id="3c6a7-110">delegate</span><span class="sxs-lookup"><span data-stu-id="3c6a7-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="3c6a7-111">C# fournit également les types référence intégrés suivants :</span><span class="sxs-lookup"><span data-stu-id="3c6a7-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="3c6a7-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="3c6a7-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="3c6a7-113">object</span><span class="sxs-lookup"><span data-stu-id="3c6a7-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="3c6a7-114">string</span><span class="sxs-lookup"><span data-stu-id="3c6a7-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="3c6a7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c6a7-115">See also</span></span>

- [<span data-ttu-id="3c6a7-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3c6a7-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3c6a7-117">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="3c6a7-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3c6a7-118">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="3c6a7-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="3c6a7-119">Types valeur</span><span class="sxs-lookup"><span data-stu-id="3c6a7-119">Value types</span></span>](../builtin-types/value-types.md)
