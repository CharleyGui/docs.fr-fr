---
title: Finaliseurs - Guide de programmation C#
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 9936d56582afd160bf3464d18efd3acf47c7af60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924495"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="b7916-102">Finaliseurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b7916-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="b7916-103">Les finaliseurs (également appelés **destructeurs**) servent à effectuer les derniers nettoyages nécessaires lorsqu’une instance de classe est collectée par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="b7916-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7916-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="b7916-104">Remarks</span></span>  
  
- <span data-ttu-id="b7916-105">Les finaliseurs ne peuvent pas être définis dans des structs.</span><span class="sxs-lookup"><span data-stu-id="b7916-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="b7916-106">Ils sont utilisés uniquement avec les classes.</span><span class="sxs-lookup"><span data-stu-id="b7916-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="b7916-107">Une classe ne peut avoir qu’un seul finaliseur.</span><span class="sxs-lookup"><span data-stu-id="b7916-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="b7916-108">Les finaliseurs ne peuvent pas être hérités ou surchargés.</span><span class="sxs-lookup"><span data-stu-id="b7916-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="b7916-109">Les finaliseurs ne peuvent pas être appelés.</span><span class="sxs-lookup"><span data-stu-id="b7916-109">Finalizers cannot be called.</span></span> <span data-ttu-id="b7916-110">Ils sont appelés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b7916-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="b7916-111">Un finaliseur ne prend pas de modificateur et n’a pas de paramètre.</span><span class="sxs-lookup"><span data-stu-id="b7916-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="b7916-112">Par exemple, voici une déclaration de finaliseur pour la classe `Car`.</span><span class="sxs-lookup"><span data-stu-id="b7916-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="b7916-113">Un finaliseur peut aussi être implémenté en tant que définition de corps d’expression, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7916-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="b7916-114">Le finaliseur appelle implicitement <xref:System.Object.Finalize%2A> sur la classe de base de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b7916-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="b7916-115">Ainsi, un appel à un finaliseur est traduit implicitement en ce code :</span><span class="sxs-lookup"><span data-stu-id="b7916-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="b7916-116">Cela signifie que la méthode `Finalize` est appelée de manière récursive pour toutes les instances de la chaîne d’héritage, de la plus dérivée à la moins dérivée.</span><span class="sxs-lookup"><span data-stu-id="b7916-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7916-117">Les finaliseurs vides ne doivent pas être utilisés.</span><span class="sxs-lookup"><span data-stu-id="b7916-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="b7916-118">Quand une classe contient un finaliseur, une entrée est créée dans la file d’attente `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="b7916-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="b7916-119">Quand le finaliseur est appelé, le récupérateur de mémoire est appelé pour traiter la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="b7916-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="b7916-120">Un finaliseur vide entraîne une perte de performances inutile.</span><span class="sxs-lookup"><span data-stu-id="b7916-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="b7916-121">Le programmeur n’a aucun contrôle sur le moment où le finaliseur est appelé, car celui-ci est déterminé par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="b7916-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="b7916-122">Le récupérateur de mémoire recherche les objets qui ne sont plus utilisés par l’application.</span><span class="sxs-lookup"><span data-stu-id="b7916-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="b7916-123">S’il considère qu’un objet peut être finalisé, il appelle le finaliseur (s’il y en a un) et libère la mémoire utilisée pour stocker l’objet.</span><span class="sxs-lookup"><span data-stu-id="b7916-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> 
 
 <span data-ttu-id="b7916-124">Dans les applications .NET Framework (mais pas dans les applications .NET Core), les finaliseurs sont également appelés quand le programme se termine.</span><span class="sxs-lookup"><span data-stu-id="b7916-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span> 
  
 <span data-ttu-id="b7916-125">Il est possible de forcer le nettoyage de la mémoire en appelant <xref:System.GC.Collect%2A>, mais la plupart du temps c’est à éviter car cela peut créer des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="b7916-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="b7916-126">Utiliser des finaliseurs pour libérer des ressources</span><span class="sxs-lookup"><span data-stu-id="b7916-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="b7916-127">En général, C# ne nécessite pas autant de gestion de mémoire que quand vous développez avec un langage qui ne cible pas un runtime avec nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="b7916-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="b7916-128">En effet, le récupérateur de mémoire .NET Framework gère implicitement l’allocation et la libération de la mémoire pour vos objets.</span><span class="sxs-lookup"><span data-stu-id="b7916-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="b7916-129">Toutefois, quand votre application encapsule des ressources non managées, telles que des fenêtres, des fichiers et des connexions réseau, vous devez utiliser des finaliseurs pour libérer ces ressources.</span><span class="sxs-lookup"><span data-stu-id="b7916-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="b7916-130">Quand l’objet peut être finalisé, le récupérateur de mémoire exécute la méthode `Finalize` de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b7916-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="b7916-131">Libération explicite de ressources</span><span class="sxs-lookup"><span data-stu-id="b7916-131">Explicit release of resources</span></span>  
 <span data-ttu-id="b7916-132">Si votre application utilise une ressource externe coûteuse, nous vous recommandons également de proposer un moyen de libérer explicitement la ressource avant que le récupérateur de mémoire ne libère l’objet.</span><span class="sxs-lookup"><span data-stu-id="b7916-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="b7916-133">Pour cela, vous devez implémenter une méthode `Dispose` à partir de l’interface <xref:System.IDisposable> qui effectue le nettoyage nécessaire pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="b7916-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="b7916-134">Cela peut améliorer considérablement les performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="b7916-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="b7916-135">Même avec ce contrôle explicite des ressources, le finaliseur devient un dispositif de protection pour nettoyer les ressources si l’appel à la méthode `Dispose` a échoué.</span><span class="sxs-lookup"><span data-stu-id="b7916-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="b7916-136">Pour plus d’informations sur le nettoyage des ressources, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7916-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="b7916-137">Nettoyage de ressources non managées</span><span class="sxs-lookup"><span data-stu-id="b7916-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="b7916-138">Implémentation d’une méthode dispose</span><span class="sxs-lookup"><span data-stu-id="b7916-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="b7916-139">using, instruction</span><span class="sxs-lookup"><span data-stu-id="b7916-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="b7916-140">Exemples</span><span class="sxs-lookup"><span data-stu-id="b7916-140">Example</span></span>  
 <span data-ttu-id="b7916-141">L’exemple suivant crée trois classes qui forment une chaîne d’héritage.</span><span class="sxs-lookup"><span data-stu-id="b7916-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="b7916-142">La classe `First` est la classe de base, `Second` est dérivée de `First`, et `Third` est dérivée de `Second`.</span><span class="sxs-lookup"><span data-stu-id="b7916-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="b7916-143">Toutes trois ont des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="b7916-143">All three have finalizers.</span></span> <span data-ttu-id="b7916-144">Dans `Main`, une instance de la classe la plus dérivée est créée.</span><span class="sxs-lookup"><span data-stu-id="b7916-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="b7916-145">Quand le programme s’exécute, notez que les finaliseurs des trois classes sont appelés automatiquement, et dans l’ordre, de la plus dérivée à la moins dérivée.</span><span class="sxs-lookup"><span data-stu-id="b7916-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b7916-146">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b7916-146">C# language specification</span></span>  

<span data-ttu-id="b7916-147">Pour plus d’informations, voir la section [Destructeurs](~/_csharplang/spec/classes.md#destructors) de la [spécification du langage C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b7916-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](../../language-reference/language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b7916-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7916-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="b7916-149">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b7916-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b7916-150">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="b7916-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b7916-151">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="b7916-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
