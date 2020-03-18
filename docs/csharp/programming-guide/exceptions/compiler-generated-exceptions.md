---
title: Exceptions générées par le compilateur - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705312"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="d4e18-102">Exceptions générées par le compilateur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d4e18-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="d4e18-103">Certaines exceptions sont levées automatiquement par le Common Language Runtime (CLR) du .NET Framework en cas d’échec d’opérations de base.</span><span class="sxs-lookup"><span data-stu-id="d4e18-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="d4e18-104">Ces exceptions et leurs conditions d’erreur sont répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d4e18-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="d4e18-105">Exception</span><span class="sxs-lookup"><span data-stu-id="d4e18-105">Exception</span></span>|<span data-ttu-id="d4e18-106">Description</span><span class="sxs-lookup"><span data-stu-id="d4e18-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="d4e18-107">Classe de base pour les exceptions qui se produisent pendant des opérations arithmétiques, telles que <xref:System.DivideByZeroException> et <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="d4e18-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="d4e18-108">Levée quand un tableau ne peut pas stocker un élément donné, car le type réel de l’élément est incompatible avec le type réel du tableau.</span><span class="sxs-lookup"><span data-stu-id="d4e18-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="d4e18-109">Levée lors d’une tentative de division d’une valeur intégrale par zéro.</span><span class="sxs-lookup"><span data-stu-id="d4e18-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="d4e18-110">Levée lors d’une tentative d’indexation d’un tableau à l’aide d’un index qui est inférieur à zéro ou en dehors des limites du tableau.</span><span class="sxs-lookup"><span data-stu-id="d4e18-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="d4e18-111">Levée quand une conversion explicite d’un type de base en interface ou en un type dérivé échoue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d4e18-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="d4e18-112">Jeté lorsqu’une tentative est faite de faire référence à un objet dont la valeur est [nulle](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="d4e18-112">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="d4e18-113">Levée quand une tentative d’allocation de mémoire à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md) échoue.</span><span class="sxs-lookup"><span data-stu-id="d4e18-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="d4e18-114">Cela indique que la mémoire disponible pour le Commun Language Runtime est épuisée.</span><span class="sxs-lookup"><span data-stu-id="d4e18-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="d4e18-115">Levée quand une opération dans un contexte `checked` engendre un dépassement.</span><span class="sxs-lookup"><span data-stu-id="d4e18-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="d4e18-116">Levée quand la pile d’exécution est épuisée par un trop grand nombre d’appels de méthode en attente ; cela indique généralement une récurrence très profonde ou infinie.</span><span class="sxs-lookup"><span data-stu-id="d4e18-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="d4e18-117">Levée quand un constructeur statique lève une exception et qu’il n’existe aucune clause `catch` pour l’intercepter.</span><span class="sxs-lookup"><span data-stu-id="d4e18-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4e18-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4e18-118">See also</span></span>

- [<span data-ttu-id="d4e18-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d4e18-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d4e18-120">Exceptions et gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="d4e18-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="d4e18-121">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="d4e18-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="d4e18-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="d4e18-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="d4e18-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="d4e18-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="d4e18-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="d4e18-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
