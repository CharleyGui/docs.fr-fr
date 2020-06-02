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
ms.openlocfilehash: 715bf240a5f7f44ba3f914ad6788631074aa41b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291017"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="ef85b-102">Sécurité et conditions de concurrence</span><span class="sxs-lookup"><span data-stu-id="ef85b-102">Security and Race Conditions</span></span>
<span data-ttu-id="ef85b-103">Une autre zone de préoccupation est le potentiel pour les brèches de sécurité exploitées par des conditions de concurrence.</span><span class="sxs-lookup"><span data-stu-id="ef85b-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="ef85b-104">Cela peut se produire de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="ef85b-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="ef85b-105">Les sous-rubriques qui suivent décrivent certains des pièges majeurs que le développeur doit éviter.</span><span class="sxs-lookup"><span data-stu-id="ef85b-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="ef85b-106">Conditions de concurrence dans la méthode dispose</span><span class="sxs-lookup"><span data-stu-id="ef85b-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="ef85b-107">Si la méthode **dispose** d’une classe (pour plus d’informations, consultez [garbage collection](../garbage-collection/index.md)) n’est pas synchronisée, il est possible que le code de nettoyage à l’intérieur de **dispose** puisse être exécuté plusieurs fois, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ef85b-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ef85b-108">Comme cette implémentation de **dispose** n’est pas synchronisée, il est possible que soit `Cleanup` appelé par un premier thread, puis qu’un deuxième thread avant `_myObj` ait la valeur **null**.</span><span class="sxs-lookup"><span data-stu-id="ef85b-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="ef85b-109">Le fait qu’il s’agisse d’un problème de sécurité dépend de ce qui se passe lorsque le `Cleanup` code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ef85b-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="ef85b-110">Un problème majeur avec les implémentations de **suppression** non synchronisées implique l’utilisation de handles de ressources tels que des fichiers.</span><span class="sxs-lookup"><span data-stu-id="ef85b-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="ef85b-111">Une suppression incorrecte peut entraîner l’utilisation d’un mauvais descripteur, ce qui entraîne souvent des failles de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ef85b-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="ef85b-112">Conditions de concurrence dans les constructeurs</span><span class="sxs-lookup"><span data-stu-id="ef85b-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="ef85b-113">Dans certaines applications, il est possible que d’autres threads accèdent à des membres de classe avant l’exécution complète de leurs constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="ef85b-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="ef85b-114">Vous devez examiner tous les constructeurs de classe pour vous assurer qu’il n’existe aucun problème de sécurité si cela se produit, ou synchroniser les threads si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ef85b-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="ef85b-115">Conditions de concurrence critique avec des objets mis en cache</span><span class="sxs-lookup"><span data-stu-id="ef85b-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="ef85b-116">Le code qui met en cache des informations de sécurité ou utilise l’opération d' [assertion](../../framework/misc/using-the-assert-method.md) de sécurité d’accès du code peut également être vulnérable aux conditions de concurrence critique si d’autres parties de la classe ne sont pas correctement synchronisées, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ef85b-116">Code that caches security information or uses the code access security [Assert](../../framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ef85b-117">S’il existe d’autres chemins vers `DoOtherWork` qui peuvent être appelés à partir d’un autre thread avec le même objet, un appelant non fiable peut ignorer une demande.</span><span class="sxs-lookup"><span data-stu-id="ef85b-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="ef85b-118">Si votre code met en cache les informations de sécurité, assurez-vous que vous l’avez révisée pour cette vulnérabilité.</span><span class="sxs-lookup"><span data-stu-id="ef85b-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="ef85b-119">Conditions de concurrence dans les finaliseurs</span><span class="sxs-lookup"><span data-stu-id="ef85b-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="ef85b-120">Des conditions de concurrence critique peuvent également se produire dans un objet qui fait référence à une ressource statique ou non managée qu’il libère ensuite dans son finaliseur.</span><span class="sxs-lookup"><span data-stu-id="ef85b-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="ef85b-121">Si plusieurs objets partagent une ressource qui est manipulée dans le finaliseur d’une classe, les objets doivent synchroniser tous les accès à cette ressource.</span><span class="sxs-lookup"><span data-stu-id="ef85b-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef85b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef85b-122">See also</span></span>

- [<span data-ttu-id="ef85b-123">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="ef85b-123">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
