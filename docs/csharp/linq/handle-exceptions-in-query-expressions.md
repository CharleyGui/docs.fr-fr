---
title: Gérer des exceptions dans des expressions de requête (LINQ en C#)
description: Découvrez comment gérer des exceptions dans des expressions de requête LINQ en C#.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688499"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="3b237-103">Gérer des exceptions dans des expressions de requête</span><span class="sxs-lookup"><span data-stu-id="3b237-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="3b237-104">Dans le contexte d’une expression de requête, vous pouvez appeler n’importe quelle méthode.</span><span class="sxs-lookup"><span data-stu-id="3b237-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="3b237-105">Toutefois, nous vous recommandons d’éviter d’appeler une méthode dans une expression de requête susceptible de créer un effet secondaire, tel que la modification du contenu de la source de données ou la levée d’une exception.</span><span class="sxs-lookup"><span data-stu-id="3b237-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="3b237-106">Cet exemple montre comment éviter la levée d’exceptions lorsque vous appelez des méthodes dans une expression de requête, en respectant les directives générales .NET relatives à la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="3b237-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="3b237-107">Selon ces directives, il est acceptable d’intercepter une exception spécifique si vous comprenez pourquoi elle est levée dans un contexte donné.</span><span class="sxs-lookup"><span data-stu-id="3b237-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="3b237-108">Pour plus d’informations, voir [Meilleures pratiques pour les exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="3b237-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="3b237-109">Le dernier exemple montre comment gérer les cas où vous devez lever une exception pendant l’exécution d’une requête.</span><span class="sxs-lookup"><span data-stu-id="3b237-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="3b237-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3b237-110">Example</span></span>

<span data-ttu-id="3b237-111">L’exemple suivant montre comment déplacer du code de gestion des exceptions en dehors d’une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="3b237-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="3b237-112">Ceci est possible uniquement lorsque la méthode ne dépend pas des variables locales de la requête.</span><span class="sxs-lookup"><span data-stu-id="3b237-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="3b237-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3b237-113">Example</span></span>

<span data-ttu-id="3b237-114">Dans certains cas, la meilleure réponse à la levée d’une exception à l’intérieur d’une requête consiste à arrêter immédiatement l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="3b237-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="3b237-115">L’exemple suivant montre comment gérer les exceptions pouvant être levées dans le corps d’une requête.</span><span class="sxs-lookup"><span data-stu-id="3b237-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="3b237-116">Supposons que `SomeMethodThatMightThrow` puisse provoquer la levée d’une exception qui nécessite l’arrêt de l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="3b237-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="3b237-117">Notez que le bloc `try` englobe la boucle `foreach` et non la requête.</span><span class="sxs-lookup"><span data-stu-id="3b237-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="3b237-118">Ceci s’explique par le fait que c’est au niveau de la boucle `foreach` que la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="3b237-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="3b237-119">Pour plus d’informations, consultez [Introduction aux requêtes LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="3b237-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="3b237-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b237-120">See also</span></span>

- [<span data-ttu-id="3b237-121">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3b237-121">Language Integrated Query (LINQ)</span></span>](index.md)
