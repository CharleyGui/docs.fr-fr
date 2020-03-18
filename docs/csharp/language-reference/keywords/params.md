---
title: params, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: f462ccc2421fef3ea111d263ec035a701cf04775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173547"
---
# <a name="params-c-reference"></a><span data-ttu-id="037d9-102">params (référence C#)</span><span class="sxs-lookup"><span data-stu-id="037d9-102">params (C# Reference)</span></span>

<span data-ttu-id="037d9-103">Avec le mot clé `params`, vous pouvez spécifier un [paramètre de méthode](method-parameters.md) qui prend un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="037d9-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="037d9-104">Vous pouvez envoyer une liste séparée par des virgules d’arguments du type spécifié dans la déclaration du paramètre ou envoyer un tableau d’arguments du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="037d9-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="037d9-105">Vous pouvez aussi ne pas envoyer d’arguments.</span><span class="sxs-lookup"><span data-stu-id="037d9-105">You also can send no arguments.</span></span> <span data-ttu-id="037d9-106">Si vous n’envoyez aucun argument, la longueur de la liste `params` est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="037d9-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="037d9-107">Dans une déclaration de méthode, vous ne pouvez pas spécifier de paramètre supplémentaire après le mot clé `params` et vous pouvez utiliser un seul mot clé `params`.</span><span class="sxs-lookup"><span data-stu-id="037d9-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="037d9-108">Le type déclaré du paramètre `params` doit être un tableau unidimensionnel, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="037d9-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="037d9-109">Sinon, une erreur du compilateur [CS0225](../../misc/cs0225.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="037d9-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="037d9-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="037d9-110">Example</span></span>

<span data-ttu-id="037d9-111">L’exemple suivant montre différentes façons d’envoyer des arguments à un paramètre `params`.</span><span class="sxs-lookup"><span data-stu-id="037d9-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="037d9-112">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="037d9-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="037d9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="037d9-113">See also</span></span>

- [<span data-ttu-id="037d9-114">Référence C</span><span class="sxs-lookup"><span data-stu-id="037d9-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="037d9-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="037d9-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="037d9-116">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="037d9-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="037d9-117">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="037d9-117">Method Parameters</span></span>](method-parameters.md)
