---
title: Exceptions générées par le compilateur - Guide de programmation C#
description: En savoir plus sur les exceptions générées par le compilateur. Passez en revue la liste des exceptions levées automatiquement et leurs conditions d’erreur.
ms.date: 12/09/2020
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 43bacbb1025bc0af3a5f21979315b3d1b0d61066
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110349"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="494e4-104">Exceptions générées par le compilateur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="494e4-104">Compiler-Generated Exceptions (C# Programming Guide)</span></span>

<span data-ttu-id="494e4-105">Certaines exceptions sont levées automatiquement par le Runtime .NET lors de l’échec des opérations de base.</span><span class="sxs-lookup"><span data-stu-id="494e4-105">Some exceptions are thrown automatically by the .NET runtime when basic operations fail.</span></span> <span data-ttu-id="494e4-106">Ces exceptions et leurs conditions d’erreur sont répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="494e4-106">These exceptions and their error conditions are listed in the following table.</span></span>

|<span data-ttu-id="494e4-107">Exception</span><span class="sxs-lookup"><span data-stu-id="494e4-107">Exception</span></span>|<span data-ttu-id="494e4-108">Description</span><span class="sxs-lookup"><span data-stu-id="494e4-108">Description</span></span>|
|---------------|-----------------|
|<xref:System.ArithmeticException>|<span data-ttu-id="494e4-109">Classe de base pour les exceptions qui se produisent pendant des opérations arithmétiques, telles que <xref:System.DivideByZeroException> et <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="494e4-109">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="494e4-110">Levée lorsqu’un tableau ne peut pas stocker un élément donné parce que le type réel de l’élément est incompatible avec le type réel du tableau.</span><span class="sxs-lookup"><span data-stu-id="494e4-110">Thrown when an array can't store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|
|<xref:System.DivideByZeroException>|<span data-ttu-id="494e4-111">Levée lors d’une tentative de division d’une valeur intégrale par zéro.</span><span class="sxs-lookup"><span data-stu-id="494e4-111">Thrown when an attempt is made to divide an integral value by zero.</span></span>|
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="494e4-112">Levée lors d’une tentative d’indexation d’un tableau à l’aide d’un index qui est inférieur à zéro ou en dehors des limites du tableau.</span><span class="sxs-lookup"><span data-stu-id="494e4-112">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|
|<xref:System.InvalidCastException>|<span data-ttu-id="494e4-113">Levée quand une conversion explicite d’un type de base en interface ou en un type dérivé échoue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="494e4-113">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|
|<xref:System.NullReferenceException>|<span data-ttu-id="494e4-114">Levée lorsqu’une tentative est faite pour référencer un objet dont la valeur est [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="494e4-114">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|
|<xref:System.OutOfMemoryException>|<span data-ttu-id="494e4-115">Levée quand une tentative d’allocation de mémoire à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md) échoue.</span><span class="sxs-lookup"><span data-stu-id="494e4-115">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="494e4-116">Cette exception indique que la mémoire disponible pour le common language runtime est épuisée.</span><span class="sxs-lookup"><span data-stu-id="494e4-116">This exception indicates that the memory available to the common language runtime has been exhausted.</span></span>|
|<xref:System.OverflowException>|<span data-ttu-id="494e4-117">Levée quand une opération dans un contexte `checked` engendre un dépassement.</span><span class="sxs-lookup"><span data-stu-id="494e4-117">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|
|<xref:System.StackOverflowException>|<span data-ttu-id="494e4-118">Levée quand la pile d’exécution est épuisée par un trop grand nombre d’appels de méthode en attente ; cela indique généralement une récurrence très profonde ou infinie.</span><span class="sxs-lookup"><span data-stu-id="494e4-118">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|
|<xref:System.TypeInitializationException>|<span data-ttu-id="494e4-119">Levée quand un constructeur statique lève une exception et qu’il n’existe aucune clause `catch` pour l’intercepter.</span><span class="sxs-lookup"><span data-stu-id="494e4-119">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|

## <a name="see-also"></a><span data-ttu-id="494e4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="494e4-120">See also</span></span>

- [<span data-ttu-id="494e4-121">try-catch</span><span class="sxs-lookup"><span data-stu-id="494e4-121">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="494e4-122">try-finally</span><span class="sxs-lookup"><span data-stu-id="494e4-122">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="494e4-123">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="494e4-123">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
