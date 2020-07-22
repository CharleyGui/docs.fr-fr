---
title: Passage de paramètres - Guide de programmation C#
description: Vous pouvez passer un argument à un paramètre en C# par valeur ou par référence. Les modifications apportées à un argument passé par référence sont conservées. Utilisez ref ou out pour passer par référence.
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 875a42aacf3d7aa4124684aefafdcb07ff4c87d6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864733"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="52de0-105">Passage de paramètres (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="52de0-105">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="52de0-106">En C#, les arguments peuvent être passés aux paramètres par valeur ou par référence.</span><span class="sxs-lookup"><span data-stu-id="52de0-106">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="52de0-107">Avec le passage par référence, les fonctions membres, les méthodes, les propriétés, les indexeurs, les opérateurs et les constructeurs peuvent changer la valeur des paramètres et rendre cette modification persistante dans l’environnement d’appel.</span><span class="sxs-lookup"><span data-stu-id="52de0-107">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="52de0-108">Pour passer un paramètre par référence avec l’intention de changer la valeur, utilisez le mot clé `ref` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="52de0-108">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="52de0-109">Pour passer un paramètre par référence avec l’intention d’éviter la copie, mais de ne pas changer la valeur, utilisez le modificateur `in`.</span><span class="sxs-lookup"><span data-stu-id="52de0-109">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="52de0-110">Pour plus de simplicité, les exemples de cette rubrique utilisent uniquement le mot clé `ref`.</span><span class="sxs-lookup"><span data-stu-id="52de0-110">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="52de0-111">Pour plus d’informations sur la différence entre `in`, `ref` et `out`, consultez [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md) et [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="52de0-111">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="52de0-112">L’exemple suivant illustre la différence entre les paramètres de référence et de valeur.</span><span class="sxs-lookup"><span data-stu-id="52de0-112">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="52de0-113">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="52de0-113">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="52de0-114">Passage de paramètres de type valeur</span><span class="sxs-lookup"><span data-stu-id="52de0-114">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="52de0-115">Passage de paramètres de type référence</span><span class="sxs-lookup"><span data-stu-id="52de0-115">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="52de0-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="52de0-116">C# Language Specification</span></span>  

<span data-ttu-id="52de0-117">Pour plus d’informations, consultez [Liste des arguments](~/_csharplang/spec/expressions.md#argument-lists) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="52de0-117">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="52de0-118">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="52de0-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="52de0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52de0-119">See also</span></span>

- [<span data-ttu-id="52de0-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="52de0-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="52de0-121">Méthodes</span><span class="sxs-lookup"><span data-stu-id="52de0-121">Methods</span></span>](./methods.md)
