---
title: Finaliseurs - Guide de programmation C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 62fc531a8064a8a5cb144a89aa9975b3199db976
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990114"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="2f1f7-102">Finaliseurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2f1f7-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="2f1f7-103">Les finaliseurs (également appelés **destructeurs**) servent à effectuer les derniers nettoyages nécessaires lorsqu’une instance de classe est collectée par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f1f7-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="2f1f7-104">Remarks</span></span>  
  
- <span data-ttu-id="2f1f7-105">Les finaliseurs ne peuvent pas être définis dans des structs.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="2f1f7-106">Ils sont utilisés uniquement avec les classes.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="2f1f7-107">Une classe ne peut avoir qu’un seul finaliseur.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="2f1f7-108">Les finaliseurs ne peuvent pas être hérités ou surchargés.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="2f1f7-109">Les finaliseurs ne peuvent pas être appelés.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-109">Finalizers cannot be called.</span></span> <span data-ttu-id="2f1f7-110">Ils sont appelés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="2f1f7-111">Un finaliseur ne prend pas de modificateur et n’a pas de paramètre.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="2f1f7-112">Par exemple, voici une déclaration de finaliseur pour la classe `Car`.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="2f1f7-113">Un finaliseur peut aussi être implémenté en tant que définition de corps d’expression, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="2f1f7-114">Le finaliseur appelle implicitement <xref:System.Object.Finalize%2A> sur la classe de base de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="2f1f7-115">Ainsi, un appel à un finaliseur est traduit implicitement en ce code :</span><span class="sxs-lookup"><span data-stu-id="2f1f7-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="2f1f7-116">Cette conception signifie que la `Finalize` méthode est appelée de manière récursive pour toutes les instances dans la chaîne d’héritage, de la plus dérivée à la moins dérivée.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-116">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f1f7-117">Les finaliseurs vides ne doivent pas être utilisés.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="2f1f7-118">Quand une classe contient un finaliseur, une entrée est créée dans la file d’attente `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="2f1f7-119">Quand le finaliseur est appelé, le récupérateur de mémoire est appelé pour traiter la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="2f1f7-120">Un finaliseur vide entraîne une perte de performances inutile.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="2f1f7-121">Le programmeur n’a aucun contrôle sur le moment où le finaliseur est appelé ; le garbage collector décide quand l’appeler.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-121">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="2f1f7-122">Le récupérateur de mémoire recherche les objets qui ne sont plus utilisés par l’application.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="2f1f7-123">S’il considère qu’un objet peut être finalisé, il appelle le finaliseur (s’il y en a un) et libère la mémoire utilisée pour stocker l’objet.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="2f1f7-124">Dans les applications .NET Framework (mais pas dans les applications .NET Core), les finaliseurs sont également appelés quand le programme se termine.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="2f1f7-125">Il est possible de forcer l’garbage collection en appelant <xref:System.GC.Collect%2A> , mais la plupart du temps, cet appel doit être évité, car il peut créer des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-125">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="2f1f7-126">Utiliser des finaliseurs pour libérer des ressources</span><span class="sxs-lookup"><span data-stu-id="2f1f7-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="2f1f7-127">En général, C# ne nécessite pas autant de gestion de la mémoire de la part du développeur que de langages qui ne ciblent pas un Runtime avec garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-127">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="2f1f7-128">Cela est dû au fait que le garbage collector .NET gère implicitement l’allocation et la libération de mémoire pour vos objets.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-128">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="2f1f7-129">Toutefois, quand votre application encapsule des ressources non managées, telles que des fenêtres, des fichiers et des connexions réseau, vous devez utiliser des finaliseurs pour libérer ces ressources.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-129">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="2f1f7-130">Quand l’objet peut être finalisé, le récupérateur de mémoire exécute la méthode `Finalize` de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="2f1f7-131">Libération explicite de ressources</span><span class="sxs-lookup"><span data-stu-id="2f1f7-131">Explicit release of resources</span></span>  
 <span data-ttu-id="2f1f7-132">Si votre application utilise une ressource externe coûteuse, nous vous recommandons également de proposer un moyen de libérer explicitement la ressource avant que le récupérateur de mémoire ne libère l’objet.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="2f1f7-133">Pour libérer la ressource, implémentez une `Dispose` méthode à partir de l' <xref:System.IDisposable> interface qui effectue le nettoyage nécessaire pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-133">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="2f1f7-134">Cela peut améliorer considérablement les performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="2f1f7-135">Même avec ce contrôle explicite sur les ressources, le finaliseur devient un dispositif de protection pour nettoyer les ressources si l’appel à la `Dispose` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="2f1f7-136">Pour plus d’informations sur le nettoyage des ressources, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="2f1f7-136">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="2f1f7-137">Nettoyage des ressources non managées</span><span class="sxs-lookup"><span data-stu-id="2f1f7-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="2f1f7-138">Implémentation d’une méthode dispose</span><span class="sxs-lookup"><span data-stu-id="2f1f7-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="2f1f7-139">using, instruction</span><span class="sxs-lookup"><span data-stu-id="2f1f7-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="2f1f7-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f1f7-140">Example</span></span>  
 <span data-ttu-id="2f1f7-141">L’exemple suivant crée trois classes qui forment une chaîne d’héritage.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="2f1f7-142">La classe `First` est la classe de base, `Second` est dérivée de `First`, et `Third` est dérivée de `Second`.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="2f1f7-143">Toutes trois ont des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-143">All three have finalizers.</span></span> <span data-ttu-id="2f1f7-144">Dans `Main`, une instance de la classe la plus dérivée est créée.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="2f1f7-145">Quand le programme s’exécute, notez que les finaliseurs des trois classes sont appelés automatiquement, et dans l’ordre, de la plus dérivée à la moins dérivée.</span><span class="sxs-lookup"><span data-stu-id="2f1f7-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2f1f7-146">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="2f1f7-146">C# language specification</span></span>  

<span data-ttu-id="2f1f7-147">Pour plus d’informations, voir la section [Destructeurs](~/_csharplang/spec/classes.md#destructors) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="2f1f7-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2f1f7-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f1f7-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="2f1f7-149">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2f1f7-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2f1f7-150">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="2f1f7-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="2f1f7-151">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="2f1f7-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
