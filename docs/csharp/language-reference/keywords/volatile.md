---
title: volatile - Référence C#
ms.custom: seodec18
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: e72173ba1b91f03ccb1c15ca6451ac997666bc7f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422128"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="d1f48-102">volatile (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d1f48-102">volatile (C# Reference)</span></span>

<span data-ttu-id="d1f48-103">Le mot clé `volatile` indique qu’un champ peut être modifié par plusieurs threads qui s’exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="d1f48-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="d1f48-104">Le compilateur, le système de runtime et même le matériel sont susceptibles de réorganiser les lectures et les écritures sur des emplacements de mémoire pour des raisons de performances.</span><span class="sxs-lookup"><span data-stu-id="d1f48-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="d1f48-105">Les champs déclarés `volatile` ne sont pas soumis à ces optimisations.</span><span class="sxs-lookup"><span data-stu-id="d1f48-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="d1f48-106">Le fait d’ajouter le modificateur `volatile` permet de garantir que tous les threads observent les écritures volatiles effectuées par un autre thread dans l’ordre dans lequel elles ont été effectuées.</span><span class="sxs-lookup"><span data-stu-id="d1f48-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="d1f48-107">Rien ne garantit que les écritures volatiles présentent un ordre total unique, tel que le voient tous les threads d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d1f48-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="d1f48-108">Le mot clé `volatile` peut être appliqué aux champs des types suivants :</span><span class="sxs-lookup"><span data-stu-id="d1f48-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="d1f48-109">Types référence.</span><span class="sxs-lookup"><span data-stu-id="d1f48-109">Reference types.</span></span>
- <span data-ttu-id="d1f48-110">Types pointeur (dans un contexte unsafe).</span><span class="sxs-lookup"><span data-stu-id="d1f48-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="d1f48-111">Notez que, même si le pointeur lui-même peut être volatile, l’objet sur lequel il pointe ne le peut pas.</span><span class="sxs-lookup"><span data-stu-id="d1f48-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="d1f48-112">En d’autres termes, vous ne pouvez pas déclarer un pointeur vers un objet volatile.</span><span class="sxs-lookup"><span data-stu-id="d1f48-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="d1f48-113">Types simples comme `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float` et `bool`.</span><span class="sxs-lookup"><span data-stu-id="d1f48-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="d1f48-114">Type `enum` avec l’un des types de base suivants : `byte`, `sbyte`, `short`, `ushort`, `int` ou `uint`.</span><span class="sxs-lookup"><span data-stu-id="d1f48-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="d1f48-115">Paramètres de type générique connus comme des types référence.</span><span class="sxs-lookup"><span data-stu-id="d1f48-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="d1f48-116">Voir <xref:System.IntPtr> et <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="d1f48-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="d1f48-117">Les autres types, notamment `double` et `long`, ne peuvent pas être marqués `volatile`, car il n’y a aucune garantie que les lectures et écritures sur des champs de ce type soient atomiques.</span><span class="sxs-lookup"><span data-stu-id="d1f48-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="d1f48-118">Pour protéger l’accès multithread à ces types de champs, utilisez les membres de classe <xref:System.Threading.Interlocked> ou l’instruction [`lock`](lock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d1f48-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="d1f48-119">Le mot clé `volatile` ne peut s’appliquer qu’aux champs d’une `class` ou d’un `struct`.</span><span class="sxs-lookup"><span data-stu-id="d1f48-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="d1f48-120">Les variables locales ne peuvent pas être déclarées `volatile`.</span><span class="sxs-lookup"><span data-stu-id="d1f48-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="d1f48-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1f48-121">Example</span></span>

<span data-ttu-id="d1f48-122">L’exemple ci-dessous montre comment déclarer une variable de champ public comme `volatile`.</span><span class="sxs-lookup"><span data-stu-id="d1f48-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="d1f48-123">L’exemple suivant montre comment il est possible de créer un thread auxiliaire ou de travail et de l’utiliser pour effectuer le traitement en parallèle avec le thread principal.</span><span class="sxs-lookup"><span data-stu-id="d1f48-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="d1f48-124">Pour plus d'informations sur le multithreading, voir [Threading managé](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1f48-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="d1f48-125">Si vous ajoutez le modificateur `volatile` à la déclaration de `_shouldStop` en place, vous obtiendrez toujours les mêmes résultats (similaires à l’extrait indiqué dans le code précédent).</span><span class="sxs-lookup"><span data-stu-id="d1f48-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="d1f48-126">Sans ce modificateur sur le membre `_shouldStop` en revanche, le comportement est imprévisible.</span><span class="sxs-lookup"><span data-stu-id="d1f48-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="d1f48-127">La méthode `DoWork` peut optimiser l’accès au membre, ce qui entraîne la lecture de données périmées.</span><span class="sxs-lookup"><span data-stu-id="d1f48-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="d1f48-128">En raison de la nature de la programmation multithread, le nombre de lectures obsolètes est imprévisible.</span><span class="sxs-lookup"><span data-stu-id="d1f48-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="d1f48-129">Différentes exécutions du programme produiront des résultats légèrement différents.</span><span class="sxs-lookup"><span data-stu-id="d1f48-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d1f48-130">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d1f48-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d1f48-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1f48-131">See also</span></span>

- [<span data-ttu-id="d1f48-132">Spécification du langage C# : mot clé volatile</span><span class="sxs-lookup"><span data-stu-id="d1f48-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="d1f48-133">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="d1f48-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d1f48-134">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d1f48-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d1f48-135">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="d1f48-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d1f48-136">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="d1f48-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d1f48-137">lock, instruction</span><span class="sxs-lookup"><span data-stu-id="d1f48-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
