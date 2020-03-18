---
title: instruction lock - référence C#
description: Utilisez l’instruction lock en C# pour synchroniser l’accès des threads à une ressource partagée
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 467881dd36c97b6b18b7f31d4e4af25152b0d012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713387"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="0ea9b-103">instruction lock (référence C#)</span><span class="sxs-lookup"><span data-stu-id="0ea9b-103">lock statement (C# reference)</span></span>

<span data-ttu-id="0ea9b-104">L’instruction `lock` obtient le verrou d’exclusion mutuelle d’un objet donné, exécute un bloc d’instructions, puis libère le verrou.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="0ea9b-105">Tant qu’un verrou est maintenu, le thread qui contient le verrou peut à nouveau obtenir et libérer le verrou.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="0ea9b-106">Tout autre thread se voit bloquer l’obtention du verrou et attend que ce dernier soit libéré.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="0ea9b-107">L’instruction `lock` se présente sous la forme</span><span class="sxs-lookup"><span data-stu-id="0ea9b-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="0ea9b-108">où `x` est une expression de [type référence](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="0ea9b-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="0ea9b-109">Elle équivaut précisément à</span><span class="sxs-lookup"><span data-stu-id="0ea9b-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="0ea9b-110">Dans la mesure où le code utilise un bloc [try...finally](try-finally.md), le verrou est libéré même si une exception est levée dans le corps d’une instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="0ea9b-111">Vous ne pouvez pas utiliser l’[opérateur await](../operators/await.md) dans le corps d’une instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ea9b-112">Notes </span><span class="sxs-lookup"><span data-stu-id="0ea9b-112">Remarks</span></span>

<span data-ttu-id="0ea9b-113">Quand vous synchronisez l’accès des threads à une ressource partagée, verrouillez une instance d’objet dédiée (par exemple `private readonly object balanceLock = new object();`) ou toute autre instance peu susceptible d’être utilisée comme objet de verrouillage par des parties du code non associées.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="0ea9b-114">Évitez d’utiliser la même instance d’objet de verrouillage pour différentes ressources partagées, car cela peut entraîner une contention d’interblocage ou de verrouillage.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="0ea9b-115">En particulier, évitez d’utiliser les éléments suivants en tant qu’objets de verrouillage :</span><span class="sxs-lookup"><span data-stu-id="0ea9b-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="0ea9b-116">`this`, qui peut être utilisé en tant que verrou par les appelants.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="0ea9b-117">Les instances de <xref:System.Type>, qui peuvent être obtenues par l’opérateur [typeof](../operators/type-testing-and-cast.md#typeof-operator) ou par réflexion.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="0ea9b-118">Les instances de chaîne, notamment les littéraux de chaîne, qui peuvent être [internés](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="0ea9b-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="0ea9b-119"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0ea9b-119">Example</span></span>

<span data-ttu-id="0ea9b-120">L’exemple suivant définit une classe `Account`, qui synchronise l’accès à son champ `balance` privé en verrouillant une instance `balanceLock` dédiée.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="0ea9b-121">L’utilisation de la même instance pour le verrouillage permet de garantir que le champ `balance` ne peut pas être mis à jour simultanément par deux threads qui tentent d’appeler les méthodes `Debit` ou `Credit` en même temps.</span><span class="sxs-lookup"><span data-stu-id="0ea9b-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="0ea9b-122">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="0ea9b-122">C# language specification</span></span>

<span data-ttu-id="0ea9b-123">Pour plus d’informations, voir la section [Instruction lock](~/_csharplang/spec/statements.md#the-lock-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0ea9b-123">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ea9b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ea9b-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="0ea9b-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="0ea9b-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0ea9b-126">Mots-clés CMD</span><span class="sxs-lookup"><span data-stu-id="0ea9b-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="0ea9b-127">Vue d’ensemble des primitives de synchronisation</span><span class="sxs-lookup"><span data-stu-id="0ea9b-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
