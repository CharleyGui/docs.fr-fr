---
title: mot-clé params pour les tableaux de paramètres - référence C
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738841"
---
# <a name="params-c-reference"></a><span data-ttu-id="f3799-102">params (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f3799-102">params (C# Reference)</span></span>

<span data-ttu-id="f3799-103">Avec le mot clé `params`, vous pouvez spécifier un [paramètre de méthode](method-parameters.md) qui prend un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="f3799-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="f3799-104">Le type de paramètre doit être un tableau unidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="f3799-104">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="f3799-105">Dans une déclaration de méthode, vous ne pouvez pas spécifier de paramètre supplémentaire après le mot clé `params` et vous pouvez utiliser un seul mot clé `params`.</span><span class="sxs-lookup"><span data-stu-id="f3799-105">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="f3799-106">Si le type `params` déclaré du paramètre n’est pas un tableau unidimensionnel, l’erreur de compilateur [CS0225](../../misc/cs0225.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="f3799-106">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="f3799-107">Lorsque vous appelez une `params` méthode avec un paramètre, vous pouvez passer dans:</span><span class="sxs-lookup"><span data-stu-id="f3799-107">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="f3799-108">Une liste d’arguments séparés par virgule du type d’éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="f3799-108">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="f3799-109">Un éventail d’arguments du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="f3799-109">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="f3799-110">Aucun argument.</span><span class="sxs-lookup"><span data-stu-id="f3799-110">No arguments.</span></span> <span data-ttu-id="f3799-111">Si vous n’envoyez aucun argument, la longueur de la liste `params` est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="f3799-111">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="f3799-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3799-112">Example</span></span>

<span data-ttu-id="f3799-113">L’exemple suivant montre différentes façons d’envoyer des arguments à un paramètre `params`.</span><span class="sxs-lookup"><span data-stu-id="f3799-113">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="f3799-114">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f3799-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f3799-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3799-115">See also</span></span>

- [<span data-ttu-id="f3799-116">Référence C</span><span class="sxs-lookup"><span data-stu-id="f3799-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f3799-117">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="f3799-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f3799-118">Mots-clés C</span><span class="sxs-lookup"><span data-stu-id="f3799-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f3799-119">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="f3799-119">Method Parameters</span></span>](method-parameters.md)
