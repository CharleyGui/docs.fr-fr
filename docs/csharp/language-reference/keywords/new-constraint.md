---
title: new, contrainte - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 6f6d1b663d03dc9b3adf0e7055dcffacc79d83dc
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795337"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="b4d11-102">new, contrainte (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b4d11-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="b4d11-103">La contrainte `new` spécifie que tout argument de type dans une déclaration de classe générique doit avoir un constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="b4d11-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="b4d11-104">Pour utiliser la contrainte `new`, le type ne doit pas être abstract.</span><span class="sxs-lookup"><span data-stu-id="b4d11-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="b4d11-105">Appliquez la contrainte `new` à un paramètre de type quand une classe générique crée des instances du type, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b4d11-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="b4d11-106">Si vous utilisez la contrainte `new()` avec d’autres contraintes, spécifiez-la en dernier :</span><span class="sxs-lookup"><span data-stu-id="b4d11-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="b4d11-107">Pour plus d’informations, consultez [Contraintes sur les paramètres de type](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b4d11-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="b4d11-108">Vous pouvez également utiliser le mot clé `new` pour [créer une instance d’un type](../operators/new-operator.md) ou l’utiliser comme un [modificateur de déclaration de membre](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="b4d11-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b4d11-109">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b4d11-109">C# language specification</span></span>

<span data-ttu-id="b4d11-110">Pour plus d’informations, consultez la section [Contraintes de paramètre de type](~/_csharplang/spec/classes.md#type-parameter-constraints) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b4d11-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4d11-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4d11-111">See also</span></span>

- [<span data-ttu-id="b4d11-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="b4d11-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b4d11-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b4d11-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b4d11-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="b4d11-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b4d11-115">Génériques</span><span class="sxs-lookup"><span data-stu-id="b4d11-115">Generics</span></span>](../../programming-guide/generics/index.md)
