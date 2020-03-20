---
title: "Comment : effectuer une initialisation tardive d'objets"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
ms.openlocfilehash: d89d19a7a3edb57dcd6c0e37e6688701da8b3713
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180602"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="99123-102">Comment : effectuer une initialisation tardive d'objets</span><span class="sxs-lookup"><span data-stu-id="99123-102">How to: Perform Lazy Initialization of Objects</span></span>
<span data-ttu-id="99123-103">La classe <xref:System.Lazy%601?displayProperty=nameWithType> simplifie les opérations d’initialisation tardive et d’instanciation des objets.</span><span class="sxs-lookup"><span data-stu-id="99123-103">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="99123-104">L’initialisation des objets de manière tardive vous évite d’avoir à créer inutilement des objets non nécessaires, ou vous permet de différer l’initialisation des objets jusqu’à ce qu’ils commencent à être utilisés.</span><span class="sxs-lookup"><span data-stu-id="99123-104">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="99123-105">Pour plus d’informations, consultez [Initialisation tardive](lazy-initialization.md).</span><span class="sxs-lookup"><span data-stu-id="99123-105">For more information, see [Lazy Initialization](lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99123-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="99123-106">Example</span></span>  
 <span data-ttu-id="99123-107">L’exemple suivant montre comment initialiser une valeur avec <xref:System.Lazy%601>.</span><span class="sxs-lookup"><span data-stu-id="99123-107">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="99123-108">Il suppose que la variable tardive peut ne pas être nécessaire, selon que la variable `someCondition` est définie sur true ou false dans un autre code.</span><span class="sxs-lookup"><span data-stu-id="99123-108">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
  {  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
  }  
```  
  
## <a name="example"></a><span data-ttu-id="99123-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="99123-109">Example</span></span>  
 <span data-ttu-id="99123-110">L’exemple suivant montre comment utiliser la classe <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> pour initialiser un type qui est visible uniquement pour l’instance d’objet qui est exécutée sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="99123-110">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="99123-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99123-111">See also</span></span>

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [<span data-ttu-id="99123-112">Initialisation tardive</span><span class="sxs-lookup"><span data-stu-id="99123-112">Lazy Initialization</span></span>](lazy-initialization.md)
