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
ms.openlocfilehash: 0f430edce99513b0de9ef437d70648a128b336b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352817"
---
# <a name="synclock-statement"></a><span data-ttu-id="1bc68-102">SyncLock, instruction</span><span class="sxs-lookup"><span data-stu-id="1bc68-102">SyncLock Statement</span></span>
<span data-ttu-id="1bc68-103">Acquiert un verrou exclusif pour un bloc d’instructions avant d’exécuter le bloc.</span><span class="sxs-lookup"><span data-stu-id="1bc68-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bc68-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="1bc68-105">Composants</span><span class="sxs-lookup"><span data-stu-id="1bc68-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="1bc68-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="1bc68-106">Required.</span></span> <span data-ttu-id="1bc68-107">Expression qui prend la valeur d’une référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="1bc68-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="1bc68-108">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="1bc68-108">Optional.</span></span> <span data-ttu-id="1bc68-109">Bloc d’instructions à exécuter lorsque le verrou est acquis.</span><span class="sxs-lookup"><span data-stu-id="1bc68-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="1bc68-110">Met fin à un bloc de `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bc68-111">Notes</span><span class="sxs-lookup"><span data-stu-id="1bc68-111">Remarks</span></span>  
 <span data-ttu-id="1bc68-112">L’instruction `SyncLock` garantit que plusieurs threads n’exécutent pas le bloc d’instructions en même temps.</span><span class="sxs-lookup"><span data-stu-id="1bc68-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="1bc68-113">`SyncLock` empêche chaque thread d’entrer dans le bloc jusqu’à ce qu’aucun autre thread l’exécute.</span><span class="sxs-lookup"><span data-stu-id="1bc68-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="1bc68-114">L’utilisation la plus courante de `SyncLock` consiste à empêcher la mise à jour des données par plusieurs threads simultanément.</span><span class="sxs-lookup"><span data-stu-id="1bc68-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="1bc68-115">Si les instructions qui manipulent les données doivent se terminer sans interruption, placez-les à l’intérieur d’un bloc de `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="1bc68-116">Un bloc d’instructions protégé par un verrou exclusif est parfois appelé une *section critique*.</span><span class="sxs-lookup"><span data-stu-id="1bc68-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1bc68-117">Règles</span><span class="sxs-lookup"><span data-stu-id="1bc68-117">Rules</span></span>  
  
- <span data-ttu-id="1bc68-118">Branche.</span><span class="sxs-lookup"><span data-stu-id="1bc68-118">Branching.</span></span> <span data-ttu-id="1bc68-119">Vous ne pouvez pas créer de branche dans un bloc `SyncLock` à partir de l’extérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="1bc68-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="1bc68-120">Valeur de l’objet Lock.</span><span class="sxs-lookup"><span data-stu-id="1bc68-120">Lock Object Value.</span></span> <span data-ttu-id="1bc68-121">La valeur de `lockobject` ne peut pas être `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="1bc68-122">Vous devez créer l’objet Lock avant de l’utiliser dans une instruction `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="1bc68-123">Vous ne pouvez pas modifier la valeur de `lockobject` lors de l’exécution d’un bloc `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="1bc68-124">Le mécanisme requiert que l’objet Lock reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="1bc68-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="1bc68-125">Vous ne pouvez pas utiliser l’opérateur [await](../../../visual-basic/language-reference/operators/await-operator.md) dans un bloc `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="1bc68-126">Comportement</span><span class="sxs-lookup"><span data-stu-id="1bc68-126">Behavior</span></span>  
  
- <span data-ttu-id="1bc68-127">Procédé.</span><span class="sxs-lookup"><span data-stu-id="1bc68-127">Mechanism.</span></span> <span data-ttu-id="1bc68-128">Lorsqu’un thread atteint l’instruction `SyncLock`, il évalue l’expression `lockobject` et interrompt l’exécution jusqu’à ce qu’il acquière un verrou exclusif sur l’objet retourné par l’expression.</span><span class="sxs-lookup"><span data-stu-id="1bc68-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="1bc68-129">Lorsqu’un autre thread atteint l’instruction `SyncLock`, il n’obtient pas de verrou tant que le premier thread n’a pas exécuté l’instruction `End SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="1bc68-130">Données protégées.</span><span class="sxs-lookup"><span data-stu-id="1bc68-130">Protected Data.</span></span> <span data-ttu-id="1bc68-131">Si `lockobject` est une variable `Shared`, le verrou exclusif empêche un thread dans une instance de la classe d’exécuter le bloc `SyncLock` alors que tout autre thread l’exécute.</span><span class="sxs-lookup"><span data-stu-id="1bc68-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="1bc68-132">Cela protège les données partagées entre toutes les instances.</span><span class="sxs-lookup"><span data-stu-id="1bc68-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="1bc68-133">Si `lockobject` est une variable d’instance (et non `Shared`), le verrou empêche un thread s’exécutant dans l’instance actuelle d’exécuter le bloc `SyncLock` en même temps qu’un autre thread dans la même instance.</span><span class="sxs-lookup"><span data-stu-id="1bc68-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="1bc68-134">Cela protège les données gérées par l’instance individuelle.</span><span class="sxs-lookup"><span data-stu-id="1bc68-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="1bc68-135">Acquisition et mise en version.</span><span class="sxs-lookup"><span data-stu-id="1bc68-135">Acquisition and Release.</span></span> <span data-ttu-id="1bc68-136">Un bloc `SyncLock` se comporte comme une construction `Try...Finally` dans laquelle le bloc `Try` acquiert un verrou exclusif sur `lockobject` et le bloc `Finally` le libère.</span><span class="sxs-lookup"><span data-stu-id="1bc68-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="1bc68-137">Pour cette raison, le bloc de `SyncLock` garantit la libération du verrou, quelle que soit la façon dont vous quittez le bloc.</span><span class="sxs-lookup"><span data-stu-id="1bc68-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="1bc68-138">Cela est vrai même dans le cas d’une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="1bc68-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="1bc68-139">Appels au Framework.</span><span class="sxs-lookup"><span data-stu-id="1bc68-139">Framework Calls.</span></span> <span data-ttu-id="1bc68-140">Le bloc `SyncLock` acquiert et libère le verrou exclusif en appelant les méthodes `Enter` et `Exit` de la classe `Monitor` dans l’espace de noms <xref:System.Threading>.</span><span class="sxs-lookup"><span data-stu-id="1bc68-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="1bc68-141">Pratiques de programmation</span><span class="sxs-lookup"><span data-stu-id="1bc68-141">Programming Practices</span></span>  
 <span data-ttu-id="1bc68-142">L’expression `lockobject` doit toujours correspondre à un objet qui appartient exclusivement à votre classe.</span><span class="sxs-lookup"><span data-stu-id="1bc68-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="1bc68-143">Vous devez déclarer une variable objet `Private` pour protéger les données appartenant à l’instance actuelle, ou une variable objet `Private Shared` pour protéger les données communes à toutes les instances.</span><span class="sxs-lookup"><span data-stu-id="1bc68-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="1bc68-144">Vous ne devez pas utiliser le mot clé `Me` pour fournir un objet Lock pour les données d’instance.</span><span class="sxs-lookup"><span data-stu-id="1bc68-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="1bc68-145">Si le code externe à votre classe contient une référence à une instance de votre classe, il peut utiliser cette référence comme objet de verrouillage pour un bloc `SyncLock` complètement différent de la vôtre, protégeant des données différentes.</span><span class="sxs-lookup"><span data-stu-id="1bc68-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="1bc68-146">De cette façon, votre classe et l’autre classe peuvent se bloquer l’exécution de leurs blocs `SyncLock` non liés.</span><span class="sxs-lookup"><span data-stu-id="1bc68-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="1bc68-147">De même, le verrouillage sur une chaîne peut être problématique, car tout autre code dans le processus qui utilise la même chaîne partagera le même verrou.</span><span class="sxs-lookup"><span data-stu-id="1bc68-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="1bc68-148">Vous ne devez pas non plus utiliser la méthode `Me.GetType` pour fournir un objet Lock pour les données partagées.</span><span class="sxs-lookup"><span data-stu-id="1bc68-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="1bc68-149">Cela est dû au fait que `GetType` retourne toujours le même objet `Type` pour un nom de classe donné.</span><span class="sxs-lookup"><span data-stu-id="1bc68-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="1bc68-150">Le code externe peut appeler `GetType` sur votre classe et obtenir le même objet de verrouillage que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="1bc68-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="1bc68-151">Cela entraînerait le blocage des deux classes de leurs blocs `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1bc68-152">Exemples</span><span class="sxs-lookup"><span data-stu-id="1bc68-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="1bc68-153">Description</span><span class="sxs-lookup"><span data-stu-id="1bc68-153">Description</span></span>  
 <span data-ttu-id="1bc68-154">L’exemple suivant illustre une classe qui gère une simple liste de messages.</span><span class="sxs-lookup"><span data-stu-id="1bc68-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="1bc68-155">Elle contient les messages d’un tableau et le dernier élément utilisé de ce tableau dans une variable.</span><span class="sxs-lookup"><span data-stu-id="1bc68-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="1bc68-156">La procédure `addAnotherMessage` incrémente le dernier élément et stocke le nouveau message.</span><span class="sxs-lookup"><span data-stu-id="1bc68-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="1bc68-157">Ces deux opérations sont protégées par les instructions `SyncLock` et `End SyncLock`, car une fois que le dernier élément a été incrémenté, le nouveau message doit être stocké avant que tout autre thread puisse incrémenter à nouveau le dernier élément.</span><span class="sxs-lookup"><span data-stu-id="1bc68-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="1bc68-158">Si la classe `simpleMessageList` a partagé une liste de messages parmi toutes ses instances, les variables `messagesList` et `messagesLast` sont déclarées comme `Shared`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="1bc68-159">Dans ce cas, la variable `messagesLock` doit également être `Shared`, afin qu’il y ait un seul objet de verrouillage utilisé par chaque instance.</span><span class="sxs-lookup"><span data-stu-id="1bc68-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1bc68-160">Code</span><span class="sxs-lookup"><span data-stu-id="1bc68-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="1bc68-161">Description</span><span class="sxs-lookup"><span data-stu-id="1bc68-161">Description</span></span>  
 <span data-ttu-id="1bc68-162">L’exemple suivant utilise des threads et des `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="1bc68-163">Tant que l’instruction `SyncLock` est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="1bc68-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="1bc68-164">Vous pouvez commenter les instructions `SyncLock` et `End SyncLock` pour voir l’effet de la sortie du mot clé `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="1bc68-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1bc68-165">Code</span><span class="sxs-lookup"><span data-stu-id="1bc68-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="1bc68-166">Commentaires</span><span class="sxs-lookup"><span data-stu-id="1bc68-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc68-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bc68-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="1bc68-168">Vue d’ensemble des primitives de synchronisation</span><span class="sxs-lookup"><span data-stu-id="1bc68-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
