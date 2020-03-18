---
title: when, mot clé contextuel - Référence C#
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712830"
---
# <a name="when-c-reference"></a><span data-ttu-id="1de1b-102">when (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1de1b-102">when (C# Reference)</span></span>

<span data-ttu-id="1de1b-103">Vous pouvez utiliser le mot clé contextuel `when` pour spécifier une condition de filtre dans deux contextes :</span><span class="sxs-lookup"><span data-stu-id="1de1b-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="1de1b-104">dans l’instruction `catch` d’un bloc [try/catch](try-catch.md) ou [try/catch/finally](try-catch-finally.md) ;</span><span class="sxs-lookup"><span data-stu-id="1de1b-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="1de1b-105">dans l’étiquette `case` d’une instruction [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="1de1b-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="1de1b-106">`when` dans une instruction `catch`</span><span class="sxs-lookup"><span data-stu-id="1de1b-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="1de1b-107">Depuis C# 6, `when` peut être utilisé dans une instruction `catch` pour spécifier une condition qui doit avoir la valeur True pour que le gestionnaire d’une exception spécifique soit exécuté.</span><span class="sxs-lookup"><span data-stu-id="1de1b-107">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="1de1b-108">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1de1b-108">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="1de1b-109">où *expr* est une expression qui prend une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="1de1b-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="1de1b-110">Si la valeur retournée est `true`, le gestionnaire de l’exception est exécuté ; si la valeur retournée est `false`, il n’est pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="1de1b-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="1de1b-111">L’exemple suivant utilise le mot clé `when` afin d’exécuter conditionnellement des gestionnaires pour une exception <xref:System.Net.Http.HttpRequestException> selon le texte du message d’exception.</span><span class="sxs-lookup"><span data-stu-id="1de1b-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="1de1b-112">`when` dans une instruction `switch`</span><span class="sxs-lookup"><span data-stu-id="1de1b-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="1de1b-113">Depuis C# 7.0, les étiquettes `case` n’ont plus besoin de s’exclure mutuellement et l’ordre dans lequel les étiquettes `case` s’affichent dans une instruction `switch` peut déterminer le bloc switch exécuté.</span><span class="sxs-lookup"><span data-stu-id="1de1b-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="1de1b-114">Le mot clé `when` peut être utilisé pour spécifier une condition de filtre qui fait que son étiquette case associée a la valeur True uniquement si la condition de filtre a également la valeur True.</span><span class="sxs-lookup"><span data-stu-id="1de1b-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="1de1b-115">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1de1b-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="1de1b-116">où *expr* est un modèle de constante ou de type qui est comparé à l’expression de correspondance, et *when-condition* représente toute expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="1de1b-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="1de1b-117">L’exemple suivant utilise le mot clé `when` pour tester les objets `Shape` ayant une superficie égale à zéro, ainsi que pour tester divers objets `Shape` ayant une superficie supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="1de1b-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="1de1b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1de1b-118">See also</span></span>

- [<span data-ttu-id="1de1b-119">instruction switch</span><span class="sxs-lookup"><span data-stu-id="1de1b-119">switch statement</span></span>](switch.md)
- [<span data-ttu-id="1de1b-120">try/catch, instruction</span><span class="sxs-lookup"><span data-stu-id="1de1b-120">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="1de1b-121">essayer/attraper/enfin la déclaration</span><span class="sxs-lookup"><span data-stu-id="1de1b-121">try/catch/finally statement</span></span>](try-catch-finally.md)
