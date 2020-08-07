---
title: expression nameof-référence C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: b00c5f6f97d27290fb3773dcbb422bf9fb4c425b
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916782"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="a9a3c-102">nameof, expression (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a9a3c-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="a9a3c-103">Une `nameof` expression produit le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :</span><span class="sxs-lookup"><span data-stu-id="a9a3c-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

<span data-ttu-id="a9a3c-104">Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="a9a3c-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="a9a3c-105">Dans le cas des [identificateurs textuels](../tokens/verbatim.md), le `@` caractère n’est pas la partie d’un nom, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a9a3c-105">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="a9a3c-106">Une `nameof` expression est évaluée au moment de la compilation et n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a9a3c-106">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="a9a3c-107">Vous pouvez utiliser une `nameof` expression pour rendre le code de vérification des arguments plus gérable :</span><span class="sxs-lookup"><span data-stu-id="a9a3c-107">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="a9a3c-108">Une `nameof` expression est disponible en C# 6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a9a3c-108">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a9a3c-109">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a9a3c-109">C# language specification</span></span>

<span data-ttu-id="a9a3c-110">Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a9a3c-110">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9a3c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9a3c-111">See also</span></span>

- [<span data-ttu-id="a9a3c-112">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="a9a3c-112">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a9a3c-113">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="a9a3c-113">C# operators and expressions</span></span>](index.md)
