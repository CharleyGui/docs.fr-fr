---
title: SyncLock, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404159"
---
# <a name="synclock-statement"></a><span data-ttu-id="33bff-102">SyncLock, instruction</span><span class="sxs-lookup"><span data-stu-id="33bff-102">SyncLock Statement</span></span>
<span data-ttu-id="33bff-103">Acquiert un verrou exclusif pour un bloc d’instructions avant d’exécuter le bloc.</span><span class="sxs-lookup"><span data-stu-id="33bff-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33bff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33bff-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="33bff-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="33bff-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="33bff-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="33bff-106">Required.</span></span> <span data-ttu-id="33bff-107">Expression qui prend la valeur d’une référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="33bff-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="33bff-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="33bff-108">Optional.</span></span> <span data-ttu-id="33bff-109">Bloc d’instructions à exécuter lorsque le verrou est acquis.</span><span class="sxs-lookup"><span data-stu-id="33bff-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="33bff-110">Met fin à un `SyncLock` bloc.</span><span class="sxs-lookup"><span data-stu-id="33bff-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33bff-111">Notes</span><span class="sxs-lookup"><span data-stu-id="33bff-111">Remarks</span></span>  
 <span data-ttu-id="33bff-112">L' `SyncLock` instruction garantit que plusieurs threads n’exécutent pas le bloc d’instructions en même temps.</span><span class="sxs-lookup"><span data-stu-id="33bff-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="33bff-113">`SyncLock`empêche chaque thread d’entrer dans le bloc jusqu’à ce qu’aucun autre thread l’exécute.</span><span class="sxs-lookup"><span data-stu-id="33bff-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="33bff-114">L’utilisation la plus courante de `SyncLock` est de protéger les données contre la mise à jour simultanée de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="33bff-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="33bff-115">Si les instructions qui manipulent les données doivent se terminer sans interruption, placez-les à l’intérieur d’un `SyncLock` bloc.</span><span class="sxs-lookup"><span data-stu-id="33bff-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="33bff-116">Un bloc d’instructions protégé par un verrou exclusif est parfois appelé une *section critique*.</span><span class="sxs-lookup"><span data-stu-id="33bff-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="33bff-117">Règles</span><span class="sxs-lookup"><span data-stu-id="33bff-117">Rules</span></span>  
  
- <span data-ttu-id="33bff-118">Branche.</span><span class="sxs-lookup"><span data-stu-id="33bff-118">Branching.</span></span> <span data-ttu-id="33bff-119">Vous ne pouvez pas créer de branche dans un `SyncLock` bloc en dehors du bloc.</span><span class="sxs-lookup"><span data-stu-id="33bff-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="33bff-120">Valeur de l’objet Lock.</span><span class="sxs-lookup"><span data-stu-id="33bff-120">Lock Object Value.</span></span> <span data-ttu-id="33bff-121">La valeur de `lockobject` ne peut pas être `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="33bff-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="33bff-122">Vous devez créer l’objet Lock avant de l’utiliser dans une `SyncLock` instruction.</span><span class="sxs-lookup"><span data-stu-id="33bff-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="33bff-123">Vous ne pouvez pas modifier la valeur de `lockobject` lors de l’exécution d’un `SyncLock` bloc.</span><span class="sxs-lookup"><span data-stu-id="33bff-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="33bff-124">Le mécanisme requiert que l’objet Lock reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="33bff-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="33bff-125">Vous ne pouvez pas utiliser l’opérateur [await](../operators/await-operator.md) dans un `SyncLock` bloc.</span><span class="sxs-lookup"><span data-stu-id="33bff-125">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="33bff-126">Comportement</span><span class="sxs-lookup"><span data-stu-id="33bff-126">Behavior</span></span>  
  
- <span data-ttu-id="33bff-127">Procédé.</span><span class="sxs-lookup"><span data-stu-id="33bff-127">Mechanism.</span></span> <span data-ttu-id="33bff-128">Lorsqu’un thread atteint l' `SyncLock` instruction, il évalue l' `lockobject` expression et interrompt l’exécution jusqu’à ce qu’il acquière un verrou exclusif sur l’objet retourné par l’expression.</span><span class="sxs-lookup"><span data-stu-id="33bff-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="33bff-129">Lorsqu’un autre thread atteint l' `SyncLock` instruction, il n’obtient pas de verrou tant que le premier thread n’a pas exécuté l' `End SyncLock` instruction.</span><span class="sxs-lookup"><span data-stu-id="33bff-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="33bff-130">Données protégées.</span><span class="sxs-lookup"><span data-stu-id="33bff-130">Protected Data.</span></span> <span data-ttu-id="33bff-131">Si `lockobject` est une `Shared` variable, le verrou exclusif empêche un thread dans une instance de la classe d’exécuter le `SyncLock` bloc alors que tout autre thread l’exécute.</span><span class="sxs-lookup"><span data-stu-id="33bff-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="33bff-132">Cela protège les données partagées entre toutes les instances.</span><span class="sxs-lookup"><span data-stu-id="33bff-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="33bff-133">Si `lockobject` est une variable d’instance (not `Shared` ), le verrou empêche un thread s’exécutant dans l’instance actuelle d’exécuter le `SyncLock` bloc en même temps qu’un autre thread dans la même instance.</span><span class="sxs-lookup"><span data-stu-id="33bff-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="33bff-134">Cela protège les données gérées par l’instance individuelle.</span><span class="sxs-lookup"><span data-stu-id="33bff-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="33bff-135">Acquisition et mise en version.</span><span class="sxs-lookup"><span data-stu-id="33bff-135">Acquisition and Release.</span></span> <span data-ttu-id="33bff-136">Un `SyncLock` bloc se comporte comme une `Try...Finally` construction dans laquelle le `Try` bloc acquiert un verrou exclusif sur `lockobject` et le bloc le `Finally` libère.</span><span class="sxs-lookup"><span data-stu-id="33bff-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="33bff-137">Pour cette raison, le `SyncLock` Bloc garantit la libération du verrou, quel que soit le mode de sortie du bloc.</span><span class="sxs-lookup"><span data-stu-id="33bff-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="33bff-138">Cela est vrai même dans le cas d’une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="33bff-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="33bff-139">Appels au Framework.</span><span class="sxs-lookup"><span data-stu-id="33bff-139">Framework Calls.</span></span> <span data-ttu-id="33bff-140">Le `SyncLock` bloc acquiert et libère le verrou exclusif en appelant les `Enter` `Exit` méthodes et de la `Monitor` classe dans l' <xref:System.Threading> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="33bff-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="33bff-141">Pratiques de programmation</span><span class="sxs-lookup"><span data-stu-id="33bff-141">Programming Practices</span></span>  
 <span data-ttu-id="33bff-142">L' `lockobject` expression doit toujours prendre la valeur d’un objet qui appartient exclusivement à votre classe.</span><span class="sxs-lookup"><span data-stu-id="33bff-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="33bff-143">Vous devez déclarer une `Private` variable objet pour protéger les données appartenant à l’instance actuelle, ou une `Private Shared` variable objet pour protéger les données communes à toutes les instances.</span><span class="sxs-lookup"><span data-stu-id="33bff-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="33bff-144">Vous ne devez pas utiliser le `Me` mot clé pour fournir un objet Lock pour les données d’instance.</span><span class="sxs-lookup"><span data-stu-id="33bff-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="33bff-145">Si le code externe à votre classe contient une référence à une instance de votre classe, il peut utiliser cette référence comme objet de verrouillage pour un `SyncLock` bloc complètement différent de la vôtre, protégeant les données différentes.</span><span class="sxs-lookup"><span data-stu-id="33bff-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="33bff-146">De cette façon, votre classe et l’autre classe peuvent se bloquer l’exécution de leurs blocs non liés `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="33bff-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="33bff-147">De même, le verrouillage sur une chaîne peut être problématique, car tout autre code dans le processus qui utilise la même chaîne partagera le même verrou.</span><span class="sxs-lookup"><span data-stu-id="33bff-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="33bff-148">Vous ne devez pas non plus utiliser la `Me.GetType` méthode pour fournir un objet Lock pour les données partagées.</span><span class="sxs-lookup"><span data-stu-id="33bff-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="33bff-149">Cela est dû `GetType` au fait que retourne toujours le même `Type` objet pour un nom de classe donné.</span><span class="sxs-lookup"><span data-stu-id="33bff-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="33bff-150">Le code externe peut appeler `GetType` votre classe et obtenir le même objet de verrouillage que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="33bff-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="33bff-151">Cela entraînerait le blocage des deux classes de leurs `SyncLock` blocs.</span><span class="sxs-lookup"><span data-stu-id="33bff-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="33bff-152">Exemples</span><span class="sxs-lookup"><span data-stu-id="33bff-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="33bff-153">Description</span><span class="sxs-lookup"><span data-stu-id="33bff-153">Description</span></span>  
 <span data-ttu-id="33bff-154">L’exemple suivant illustre une classe qui gère une simple liste de messages.</span><span class="sxs-lookup"><span data-stu-id="33bff-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="33bff-155">Elle contient les messages d’un tableau et le dernier élément utilisé de ce tableau dans une variable.</span><span class="sxs-lookup"><span data-stu-id="33bff-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="33bff-156">La `addAnotherMessage` procédure incrémente le dernier élément et stocke le nouveau message.</span><span class="sxs-lookup"><span data-stu-id="33bff-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="33bff-157">Ces deux opérations sont protégées par les `SyncLock` `End SyncLock` instructions et, car une fois que le dernier élément a été incrémenté, le nouveau message doit être stocké avant que tout autre thread puisse incrémenter à nouveau le dernier élément.</span><span class="sxs-lookup"><span data-stu-id="33bff-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="33bff-158">Si la `simpleMessageList` classe a partagé une liste de messages parmi toutes ses instances, les variables `messagesList` et `messagesLast` seraient déclarées comme `Shared` .</span><span class="sxs-lookup"><span data-stu-id="33bff-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="33bff-159">Dans ce cas, la variable `messagesLock` doit également être `Shared` , afin qu’il y ait un seul objet de verrouillage utilisé par chaque instance.</span><span class="sxs-lookup"><span data-stu-id="33bff-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="33bff-160">Code</span><span class="sxs-lookup"><span data-stu-id="33bff-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="33bff-161">Description</span><span class="sxs-lookup"><span data-stu-id="33bff-161">Description</span></span>  
 <span data-ttu-id="33bff-162">L’exemple suivant utilise des threads et `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="33bff-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="33bff-163">Tant que l' `SyncLock` instruction est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="33bff-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="33bff-164">Vous pouvez commenter les `SyncLock` `End SyncLock` instructions et pour voir l’effet de la sortie du `SyncLock` mot clé.</span><span class="sxs-lookup"><span data-stu-id="33bff-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="33bff-165">Code</span><span class="sxs-lookup"><span data-stu-id="33bff-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="33bff-166">Commentaires</span><span class="sxs-lookup"><span data-stu-id="33bff-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33bff-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33bff-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="33bff-168">Vue d’ensemble des primitives de synchronisation</span><span class="sxs-lookup"><span data-stu-id="33bff-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
