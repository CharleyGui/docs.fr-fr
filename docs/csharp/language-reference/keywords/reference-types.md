---
title: Types référence - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 61b9f8096e1b2093b1ea5589f4336618cd189c34
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422454"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="cce6b-102">Types référence (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="cce6b-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="cce6b-103">Il existe deux genres de types en C# : les types référence et les types valeur.</span><span class="sxs-lookup"><span data-stu-id="cce6b-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="cce6b-104">Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données.</span><span class="sxs-lookup"><span data-stu-id="cce6b-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="cce6b-105">Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable.</span><span class="sxs-lookup"><span data-stu-id="cce6b-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="cce6b-106">Avec les types valeur, chaque variable a sa propre copie des données et les opérations sur une variable ne peuvent pas affecter l’autre (sauf pour les variables de paramètre in, ref et out ; consultez les modificateurs de paramètre [in](in-parameter-modifier.md), [ref](ref.md) et [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="cce6b-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="cce6b-107">Les mots clés suivants sont utilisés pour déclarer des types référence :</span><span class="sxs-lookup"><span data-stu-id="cce6b-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="cce6b-108">class</span><span class="sxs-lookup"><span data-stu-id="cce6b-108">class</span></span>](class.md)

- [<span data-ttu-id="cce6b-109">interface</span><span class="sxs-lookup"><span data-stu-id="cce6b-109">interface</span></span>](interface.md)

- [<span data-ttu-id="cce6b-110">delegate</span><span class="sxs-lookup"><span data-stu-id="cce6b-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="cce6b-111">C# fournit également les types référence intégrés suivants :</span><span class="sxs-lookup"><span data-stu-id="cce6b-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="cce6b-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="cce6b-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="cce6b-113">object</span><span class="sxs-lookup"><span data-stu-id="cce6b-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="cce6b-114">string</span><span class="sxs-lookup"><span data-stu-id="cce6b-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="cce6b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cce6b-115">See also</span></span>

- [<span data-ttu-id="cce6b-116">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="cce6b-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cce6b-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cce6b-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cce6b-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="cce6b-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cce6b-119">Types</span><span class="sxs-lookup"><span data-stu-id="cce6b-119">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="cce6b-120">Types valeur</span><span class="sxs-lookup"><span data-stu-id="cce6b-120">Value Types</span></span>](value-types.md)
