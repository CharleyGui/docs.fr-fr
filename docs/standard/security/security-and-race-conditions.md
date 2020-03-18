---
title: Sécurité et conditions de concurrence
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186779"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="c25c6-102">Sécurité et conditions de concurrence</span><span class="sxs-lookup"><span data-stu-id="c25c6-102">Security and Race Conditions</span></span>
<span data-ttu-id="c25c6-103">Un autre sujet de préoccupation est le potentiel de failles de sécurité exploitées par les conditions de course.</span><span class="sxs-lookup"><span data-stu-id="c25c6-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="c25c6-104">Il y a plusieurs façons de cela.</span><span class="sxs-lookup"><span data-stu-id="c25c6-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="c25c6-105">Les sous-produits qui suivent décrivent quelques-uns des principaux pièges que le développeur doit éviter.</span><span class="sxs-lookup"><span data-stu-id="c25c6-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="c25c6-106">Conditions de course dans la méthode disposer</span><span class="sxs-lookup"><span data-stu-id="c25c6-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="c25c6-107">Si la méthode **dispose d’une** classe (pour plus d’informations, voir [Collection d’ordures](../../../docs/standard/garbage-collection/index.md)) n’est pas synchronisée, il est possible que le code de nettoyage à l’intérieur **de Dispose** puisse être exécuté plus d’une fois, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c25c6-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()
{  
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="c25c6-108">Parce que cette implémentation **Dispose** n’est pas synchronisée, il est possible `Cleanup` pour être appelé par un premier thread, puis un deuxième thread avant `_myObj` est configuré à **null.**</span><span class="sxs-lookup"><span data-stu-id="c25c6-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="c25c6-109">La question de savoir s’il `Cleanup` s’agit d’une préoccupation de sécurité dépend de ce qui se passe lorsque le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="c25c6-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="c25c6-110">Un problème majeur avec les implémentations **de disposition** non synchronisées concerne l’utilisation de poignées de ressources telles que les fichiers.</span><span class="sxs-lookup"><span data-stu-id="c25c6-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="c25c6-111">Une mauvaise élimination peut entraîner l’utilisation d’une mauvaise poignée, ce qui entraîne souvent des failles de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c25c6-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="c25c6-112">Conditions de course dans les constructeurs</span><span class="sxs-lookup"><span data-stu-id="c25c6-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="c25c6-113">Dans certaines applications, il pourrait être possible pour d’autres threads d’accéder aux membres de la classe avant que leurs constructeurs de classe ont complètement exécuté.</span><span class="sxs-lookup"><span data-stu-id="c25c6-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="c25c6-114">Vous devez passer en revue tous les constructeurs de classe pour vous assurer qu’il n’y a pas de problèmes de sécurité si cela devait se produire, ou synchroniser les threads si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c25c6-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="c25c6-115">Conditions de course avec objets caches</span><span class="sxs-lookup"><span data-stu-id="c25c6-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="c25c6-116">Le code qui cache les informations de sécurité ou utilise l’opération de sécurité [d’accès](../../../docs/framework/misc/using-the-assert-method.md) au code Assert peut également être vulnérable aux conditions de course si d’autres parties de la classe ne sont pas synchronisées de manière appropriée, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c25c6-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()
{  
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
    {  
        DoSomethingTrusted();  
    }  
    else
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="c25c6-117">S’il y `DoOtherWork` a d’autres chemins à qui peut être appelé à partir d’un autre thread avec le même objet, un appelant non fiable peut glisser au-delà d’une demande.</span><span class="sxs-lookup"><span data-stu-id="c25c6-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="c25c6-118">Si votre code cache des informations de sécurité, assurez-vous de les examiner pour cette vulnérabilité.</span><span class="sxs-lookup"><span data-stu-id="c25c6-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="c25c6-119">Conditions de course dans finalizers</span><span class="sxs-lookup"><span data-stu-id="c25c6-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="c25c6-120">Les conditions de course peuvent également se produire dans un objet qui fait référence à une ressource statique ou non mentée qu’il libère ensuite dans son finalisateur.</span><span class="sxs-lookup"><span data-stu-id="c25c6-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="c25c6-121">Si plusieurs objets partagent une ressource qui est manipulée dans le finalisateur d’une classe, les objets doivent synchroniser tout accès à cette ressource.</span><span class="sxs-lookup"><span data-stu-id="c25c6-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25c6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c25c6-122">See also</span></span>

- [<span data-ttu-id="c25c6-123">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="c25c6-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
