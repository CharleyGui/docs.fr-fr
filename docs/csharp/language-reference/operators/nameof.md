---
title: opérateur nameof - Référence C#
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: a734cae8fbb944774a4bd1bda9194a548b3d82bc
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239220"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="5d9af-102">opérateur nameof (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="5d9af-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="5d9af-103">L’opérateur `nameof` obtient le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :</span><span class="sxs-lookup"><span data-stu-id="5d9af-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/snippets/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="5d9af-104">Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="5d9af-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="5d9af-105">L’opérateur `nameof` est évalué au moment de la compilation et n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5d9af-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="5d9af-106">Vous pouvez utiliser l’opérateur `nameof` pour rendre le code de vérification des arguments plus gérable :</span><span class="sxs-lookup"><span data-stu-id="5d9af-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/snippets/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="5d9af-107">L’opérateur `nameof` est disponible dans les versions 6 et ultérieures de C#.</span><span class="sxs-lookup"><span data-stu-id="5d9af-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5d9af-108">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5d9af-108">C# language specification</span></span>

<span data-ttu-id="5d9af-109">Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5d9af-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d9af-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d9af-110">See also</span></span>

- [<span data-ttu-id="5d9af-111">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="5d9af-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5d9af-112">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="5d9af-112">C# operators</span></span>](index.md)
