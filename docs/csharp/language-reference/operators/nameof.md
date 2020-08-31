---
description: expression nameof-référence C#
title: expression nameof-référence C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 04109cde2a1f9146bf9bb44f301272808797ded0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118310"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="96673-103">nameof, expression (référence C#)</span><span class="sxs-lookup"><span data-stu-id="96673-103">nameof expression (C# reference)</span></span>

<span data-ttu-id="96673-104">Une `nameof` expression produit le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :</span><span class="sxs-lookup"><span data-stu-id="96673-104">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

<span data-ttu-id="96673-105">Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="96673-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="96673-106">Dans le cas des [identificateurs textuels](../tokens/verbatim.md), le `@` caractère n’est pas la partie d’un nom, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="96673-106">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="96673-107">Une `nameof` expression est évaluée au moment de la compilation et n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="96673-107">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="96673-108">Vous pouvez utiliser une `nameof` expression pour rendre le code de vérification des arguments plus gérable :</span><span class="sxs-lookup"><span data-stu-id="96673-108">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="96673-109">Une `nameof` expression est disponible en C# 6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="96673-109">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="96673-110">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="96673-110">C# language specification</span></span>

<span data-ttu-id="96673-111">Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="96673-111">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="96673-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96673-112">See also</span></span>

- [<span data-ttu-id="96673-113">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="96673-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="96673-114">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="96673-114">C# operators and expressions</span></span>](index.md)
