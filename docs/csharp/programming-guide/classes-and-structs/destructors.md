---
title: Finaliseurs - Guide de programmation C#
description: Les finaliseurs en C#, qui sont également appelés destructeurs, exécutent tout nettoyage final nécessaire lorsqu’une instance de classe est collectée par le garbage collector.
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 61a00e766b0f975691b9f2a7c7561bb4f1d33c02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174301"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="b72b7-103">Finaliseurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b72b7-103">Finalizers (C# Programming Guide)</span></span>

<span data-ttu-id="b72b7-104">Les finaliseurs (également appelés **destructeurs**) servent à effectuer les derniers nettoyages nécessaires lorsqu’une instance de classe est collectée par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="b72b7-104">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b72b7-105">Notes</span><span class="sxs-lookup"><span data-stu-id="b72b7-105">Remarks</span></span>  
  
- <span data-ttu-id="b72b7-106">Les finaliseurs ne peuvent pas être définis dans des structs.</span><span class="sxs-lookup"><span data-stu-id="b72b7-106">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="b72b7-107">Ils sont utilisés uniquement avec les classes.</span><span class="sxs-lookup"><span data-stu-id="b72b7-107">They are only used with classes.</span></span>  
  
- <span data-ttu-id="b72b7-108">Une classe ne peut avoir qu’un seul finaliseur.</span><span class="sxs-lookup"><span data-stu-id="b72b7-108">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="b72b7-109">Les finaliseurs ne peuvent pas être hérités ou surchargés.</span><span class="sxs-lookup"><span data-stu-id="b72b7-109">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="b72b7-110">Les finaliseurs ne peuvent pas être appelés.</span><span class="sxs-lookup"><span data-stu-id="b72b7-110">Finalizers cannot be called.</span></span> <span data-ttu-id="b72b7-111">Ils sont appelés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b72b7-111">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="b72b7-112">Un finaliseur ne prend pas de modificateur et n’a pas de paramètre.</span><span class="sxs-lookup"><span data-stu-id="b72b7-112">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="b72b7-113">Par exemple, voici une déclaration de finaliseur pour la classe `Car`.</span><span class="sxs-lookup"><span data-stu-id="b72b7-113">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="b72b7-114">Un finaliseur peut aussi être implémenté en tant que définition de corps d’expression, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b72b7-114">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="b72b7-115">Le finaliseur appelle implicitement <xref:System.Object.Finalize%2A> sur la classe de base de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b72b7-115">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="b72b7-116">Ainsi, un appel à un finaliseur est traduit implicitement en ce code :</span><span class="sxs-lookup"><span data-stu-id="b72b7-116">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="b72b7-117">Cette conception signifie que la `Finalize` méthode est appelée de manière récursive pour toutes les instances dans la chaîne d’héritage, de la plus dérivée à la moins dérivée.</span><span class="sxs-lookup"><span data-stu-id="b72b7-117">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b72b7-118">Les finaliseurs vides ne doivent pas être utilisés.</span><span class="sxs-lookup"><span data-stu-id="b72b7-118">Empty finalizers should not be used.</span></span> <span data-ttu-id="b72b7-119">Quand une classe contient un finaliseur, une entrée est créée dans la file d’attente `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="b72b7-119">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="b72b7-120">Quand le finaliseur est appelé, le récupérateur de mémoire est appelé pour traiter la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="b72b7-120">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="b72b7-121">Un finaliseur vide entraîne une perte de performances inutile.</span><span class="sxs-lookup"><span data-stu-id="b72b7-121">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="b72b7-122">Le programmeur n’a aucun contrôle sur le moment où le finaliseur est appelé ; le garbage collector décide quand l’appeler.</span><span class="sxs-lookup"><span data-stu-id="b72b7-122">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="b72b7-123">Le récupérateur de mémoire recherche les objets qui ne sont plus utilisés par l’application.</span><span class="sxs-lookup"><span data-stu-id="b72b7-123">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="b72b7-124">S’il considère qu’un objet peut être finalisé, il appelle le finaliseur (s’il y en a un) et libère la mémoire utilisée pour stocker l’objet.</span><span class="sxs-lookup"><span data-stu-id="b72b7-124">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="b72b7-125">Dans les applications .NET Framework (mais pas dans les applications .NET Core), les finaliseurs sont également appelés quand le programme se termine.</span><span class="sxs-lookup"><span data-stu-id="b72b7-125">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="b72b7-126">Il est possible de forcer l’garbage collection en appelant <xref:System.GC.Collect%2A> , mais la plupart du temps, cet appel doit être évité, car il peut créer des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="b72b7-126">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="b72b7-127">Utiliser des finaliseurs pour libérer des ressources</span><span class="sxs-lookup"><span data-stu-id="b72b7-127">Using finalizers to release resources</span></span>  

 <span data-ttu-id="b72b7-128">En général, C# ne nécessite pas autant de gestion de la mémoire de la part du développeur que de langages qui ne ciblent pas un Runtime avec garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b72b7-128">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="b72b7-129">Cela est dû au fait que le garbage collector .NET gère implicitement l’allocation et la libération de mémoire pour vos objets.</span><span class="sxs-lookup"><span data-stu-id="b72b7-129">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="b72b7-130">Toutefois, quand votre application encapsule des ressources non managées, telles que des fenêtres, des fichiers et des connexions réseau, vous devez utiliser des finaliseurs pour libérer ces ressources.</span><span class="sxs-lookup"><span data-stu-id="b72b7-130">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="b72b7-131">Quand l’objet peut être finalisé, le récupérateur de mémoire exécute la méthode `Finalize` de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b72b7-131">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="b72b7-132">Libération explicite de ressources</span><span class="sxs-lookup"><span data-stu-id="b72b7-132">Explicit release of resources</span></span>  

 <span data-ttu-id="b72b7-133">Si votre application utilise une ressource externe coûteuse, nous vous recommandons également de proposer un moyen de libérer explicitement la ressource avant que le récupérateur de mémoire ne libère l’objet.</span><span class="sxs-lookup"><span data-stu-id="b72b7-133">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="b72b7-134">Pour libérer la ressource, implémentez une `Dispose` méthode à partir de l' <xref:System.IDisposable> interface qui effectue le nettoyage nécessaire pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="b72b7-134">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="b72b7-135">Cela peut améliorer considérablement les performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="b72b7-135">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="b72b7-136">Même avec ce contrôle explicite sur les ressources, le finaliseur devient un dispositif de protection pour nettoyer les ressources si l’appel à la `Dispose` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="b72b7-136">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="b72b7-137">Pour plus d’informations sur le nettoyage des ressources, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="b72b7-137">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="b72b7-138">Nettoyage de ressources non managées</span><span class="sxs-lookup"><span data-stu-id="b72b7-138">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="b72b7-139">Implémentation d’une méthode dispose</span><span class="sxs-lookup"><span data-stu-id="b72b7-139">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="b72b7-140">using, instruction</span><span class="sxs-lookup"><span data-stu-id="b72b7-140">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="b72b7-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="b72b7-141">Example</span></span>  

 <span data-ttu-id="b72b7-142">L’exemple suivant crée trois classes qui forment une chaîne d’héritage.</span><span class="sxs-lookup"><span data-stu-id="b72b7-142">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="b72b7-143">La classe `First` est la classe de base, `Second` est dérivée de `First`, et `Third` est dérivée de `Second`.</span><span class="sxs-lookup"><span data-stu-id="b72b7-143">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="b72b7-144">Toutes trois ont des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="b72b7-144">All three have finalizers.</span></span> <span data-ttu-id="b72b7-145">Dans `Main`, une instance de la classe la plus dérivée est créée.</span><span class="sxs-lookup"><span data-stu-id="b72b7-145">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="b72b7-146">Quand le programme s’exécute, notez que les finaliseurs des trois classes sont appelés automatiquement, et dans l’ordre, de la plus dérivée à la moins dérivée.</span><span class="sxs-lookup"><span data-stu-id="b72b7-146">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b72b7-147">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b72b7-147">C# language specification</span></span>  

<span data-ttu-id="b72b7-148">Pour plus d’informations, voir la section [Destructeurs](~/_csharplang/spec/classes.md#destructors) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b72b7-148">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b72b7-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b72b7-149">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="b72b7-150">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b72b7-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b72b7-151">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="b72b7-151">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b72b7-152">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="b72b7-152">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
