---
title: opérateur délégué - Référence C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: f7cd7caf11d9f076a5d6e82aae696c914bd60e44
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916843"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="396ca-102">opérateur délégué (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="396ca-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="396ca-103">L’opérateur `delegate` crée une méthode anonyme qui peut être convertie en un type délégué :</span><span class="sxs-lookup"><span data-stu-id="396ca-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="396ca-104">À partir C# 3, les expressions lambda offrent un moyen plus concis et plus expressif de créer une fonction anonyme.</span><span class="sxs-lookup"><span data-stu-id="396ca-104">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="396ca-105">Utilisez [=> opérateur](lambda-operator.md) pour construire une expression lambda :</span><span class="sxs-lookup"><span data-stu-id="396ca-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="396ca-106">Pour plus d’informations sur les fonctionnalités des expressions lambda, par exemple la capture de variables externes, consultez [Expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="396ca-106">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="396ca-107">Lorsque vous utilisez l’opérateur `delegate`, vous pouvez omettre la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="396ca-107">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="396ca-108">Dans ce cas, la méthode anonyme créée peut être convertie en un type délégué avec n’importe quelle liste de paramètres, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="396ca-108">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="396ca-109">C’est la seule fonctionnalité des méthodes anonymes qui n’est pas prise en charge par les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="396ca-109">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="396ca-110">Dans tous les autres cas, une expression lambda est le moyen préféré pour écrire du code incorporé.</span><span class="sxs-lookup"><span data-stu-id="396ca-110">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="396ca-111">Vous utilisez également le mot clé `delegate` pour déclarer un [type délégué](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="396ca-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="396ca-112">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="396ca-112">C# language specification</span></span>

<span data-ttu-id="396ca-113">Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="396ca-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="396ca-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="396ca-114">See also</span></span>

- [<span data-ttu-id="396ca-115">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="396ca-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="396ca-116">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="396ca-116">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="396ca-117">=> opérateur</span><span class="sxs-lookup"><span data-stu-id="396ca-117">=> operator</span></span>](lambda-operator.md)
