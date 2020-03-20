---
title: openGenericCERCall (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
ms.openlocfilehash: 7492a4c0547680a6ace85a5f7c98567770f5575a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181782"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="91e92-102">openGenericCERCall (MDA)</span><span class="sxs-lookup"><span data-stu-id="91e92-102">openGenericCERCall MDA</span></span>

<span data-ttu-id="91e92-103">L’Assistant Débogage managé `openGenericCERCall` est activé pour signaler qu’un graphe de région d’exécution limitée avec des variables de type générique au niveau de la méthode racine est en cours de traitement au moment de la compilation JIT ou de la génération d’images natives, et qu’au moins une des variables de type générique est un type de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="91e92-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>

## <a name="symptoms"></a><span data-ttu-id="91e92-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="91e92-104">Symptoms</span></span>

<span data-ttu-id="91e92-105">Le code de la région d’exécution limitée ne s’exécute pas quand un thread est abandonné ou quand un domaine d’application est déchargé.</span><span class="sxs-lookup"><span data-stu-id="91e92-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>

## <a name="cause"></a><span data-ttu-id="91e92-106">Cause :</span><span class="sxs-lookup"><span data-stu-id="91e92-106">Cause</span></span>

<span data-ttu-id="91e92-107">Au moment de la compilation JIT, une instanciation contenant un type de référence d’objet est seulement représentative, car le code obtenu est partagé et chacune des variables de type de référence d’objet peut être n’importe quel type de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="91e92-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="91e92-108">Ceci peut empêcher la préparation de certaines ressources préalablement à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="91e92-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>

<span data-ttu-id="91e92-109">En particulier, les méthodes avec des variables de type générique peuvent allouer tardivement des ressources en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="91e92-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="91e92-110">Celles-ci sont appelées des entrées de dictionnaire génériques.</span><span class="sxs-lookup"><span data-stu-id="91e92-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="91e92-111">Par exemple, pour `List<T> list = new List<T>();` `T` l’énoncé où est une variable de type générique, le temps d’exécution doit lever les 200 heures et peut-être créer l’instantanéisation exacte au moment de l’exécution, par exemple, `List<Object>, List<String>`et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="91e92-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`, and so forth.</span></span> <span data-ttu-id="91e92-112">Cette opération peut échouer pour différentes raisons qui échappent au contrôle du développeur, comme l’insuffisance de mémoire.</span><span class="sxs-lookup"><span data-stu-id="91e92-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>

<span data-ttu-id="91e92-113">Cet Assistant Débogage managé doit être activé seulement au moment de la compilation JIT, et non pas quand il existe une instanciation exacte.</span><span class="sxs-lookup"><span data-stu-id="91e92-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>

<span data-ttu-id="91e92-114">Quand cet Assistant Débogage managé est activé, les symptômes probables sont que les régions d’exécution limitée ne sont pas fonctionnelles pour les instanciations incorrectes.</span><span class="sxs-lookup"><span data-stu-id="91e92-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="91e92-115">En fait, le runtime n’a pas tenté implémenter une région d’exécution limitée dans les circonstances qui ont provoqué l’activation de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="91e92-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="91e92-116">Par conséquent, si le développeur utilise une instanciation partagée de la région d’exécution limitée, les erreurs de compilation JIT, les erreurs de chargement de types génériques ou les abandons de threads dans la région d’exécution limitée prévue ne sont pas interceptées.</span><span class="sxs-lookup"><span data-stu-id="91e92-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>

## <a name="resolution"></a><span data-ttu-id="91e92-117">Résolution</span><span class="sxs-lookup"><span data-stu-id="91e92-117">Resolution</span></span>

<span data-ttu-id="91e92-118">N’utilisez pas de variables de type générique qui sont du type de référence d’objet pour les méthodes qui peuvent contenir une région d’exécution limitée.</span><span class="sxs-lookup"><span data-stu-id="91e92-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="91e92-119">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="91e92-119">Effect on the Runtime</span></span>

<span data-ttu-id="91e92-120">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="91e92-120">This MDA has no effect on the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="91e92-121">Output</span><span class="sxs-lookup"><span data-stu-id="91e92-121">Output</span></span>

<span data-ttu-id="91e92-122">Voici un échantillon de sortie de cette MDA :</span><span class="sxs-lookup"><span data-stu-id="91e92-122">The following is a sample of output from this MDA:</span></span>
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution.
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a><span data-ttu-id="91e92-123">Configuration</span><span class="sxs-lookup"><span data-stu-id="91e92-123">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a><span data-ttu-id="91e92-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="91e92-124">Example</span></span>

<span data-ttu-id="91e92-125">Le code de la région d’exécution limitée n’est pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="91e92-125">The CER code is not executed.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.CompilerServices;

class Program
{
    static void Main(string[] args)
    {
        CallGenericMethods();
    }
    static void CallGenericMethods()
    {
        // This call is correct. The instantiation of the method
        // contains only nonreference types.
        MyClass.GenericMethodWithCer<int>();

        // This call is incorrect. A shared version of the method that
        // cannot be completely analyzed will be JIT-compiled. The
        // MDA will be activated at JIT-compile time, not at run time.
        MyClass.GenericMethodWithCer<String>();
    }
}

class MyClass
{
    public static void GenericMethodWithCer<T>()
    {
        RuntimeHelpers.PrepareConstrainedRegions();
        try
        {

        }
        finally
        {
            // This is the start of the CER.
            Console.WriteLine("In finally block.");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="91e92-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91e92-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="91e92-127">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="91e92-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
