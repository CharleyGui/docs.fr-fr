---
description: mot clé params pour les tableaux de paramètres-référence C#
title: mot clé params pour les tableaux de paramètres-référence C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134469"
---
# <a name="params-c-reference"></a><span data-ttu-id="a5dbe-103">params (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a5dbe-103">params (C# Reference)</span></span>

<span data-ttu-id="a5dbe-104">Avec le mot clé `params`, vous pouvez spécifier un [paramètre de méthode](method-parameters.md) qui prend un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-104">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="a5dbe-105">Le type de paramètre doit être un tableau unidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-105">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="a5dbe-106">Dans une déclaration de méthode, vous ne pouvez pas spécifier de paramètre supplémentaire après le mot clé `params` et vous pouvez utiliser un seul mot clé `params`.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-106">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="a5dbe-107">Si le type déclaré du `params` paramètre n’est pas un tableau unidimensionnel, l’erreur de compilateur [CS0225](../../misc/cs0225.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-107">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="a5dbe-108">Lorsque vous appelez une méthode avec un `params` paramètre, vous pouvez passer :</span><span class="sxs-lookup"><span data-stu-id="a5dbe-108">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="a5dbe-109">Liste séparée par des virgules des arguments du type des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-109">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="a5dbe-110">Tableau d’arguments du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-110">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="a5dbe-111">Aucun argument.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-111">No arguments.</span></span> <span data-ttu-id="a5dbe-112">Si vous n’envoyez aucun argument, la longueur de la liste `params` est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-112">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="a5dbe-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5dbe-113">Example</span></span>

<span data-ttu-id="a5dbe-114">L’exemple suivant montre différentes façons d’envoyer des arguments à un paramètre `params`.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-114">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="a5dbe-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a5dbe-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a5dbe-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5dbe-116">See also</span></span>

- [<span data-ttu-id="a5dbe-117">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a5dbe-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a5dbe-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a5dbe-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a5dbe-119">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a5dbe-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a5dbe-120">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="a5dbe-120">Method Parameters</span></span>](method-parameters.md)
