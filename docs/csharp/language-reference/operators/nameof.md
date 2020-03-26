---
title: nameof expression - Référence C
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507137"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="eae39-102">nameof expression (référence C)</span><span class="sxs-lookup"><span data-stu-id="eae39-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="eae39-103">Une `nameof` expression produit le nom d’une variable, d’un type ou d’un membre comme constante de la chaîne :</span><span class="sxs-lookup"><span data-stu-id="eae39-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="eae39-104">Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="eae39-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="eae39-105">Une `nameof` expression est évaluée au moment de la compilation et n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="eae39-105">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="eae39-106">Vous pouvez `nameof` utiliser une expression pour rendre le code de vérification des arguments plus maintenable :</span><span class="sxs-lookup"><span data-stu-id="eae39-106">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="eae39-107">Une `nameof` expression est disponible en C 6 et plus tard.</span><span class="sxs-lookup"><span data-stu-id="eae39-107">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eae39-108">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="eae39-108">C# language specification</span></span>

<span data-ttu-id="eae39-109">Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="eae39-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eae39-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eae39-110">See also</span></span>

- [<span data-ttu-id="eae39-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="eae39-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="eae39-112">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="eae39-112">C# operators</span></span>](index.md)
