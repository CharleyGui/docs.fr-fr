---
title: "Comment : effectuer une initialisation tardive d'objets"
description: Découvrez comment effectuer une initialisation tardive des objets à l’aide de la classe System. Lazy <T> . L’initialisation tardive signifie que les objets ne sont pas créés s’ils ne sont jamais nécessaires.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
ms.openlocfilehash: dbee0d8a5c3075ad7429feb92b87a566fdd35454
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309727"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="e2291-104">Comment : effectuer une initialisation tardive d'objets</span><span class="sxs-lookup"><span data-stu-id="e2291-104">How to: Perform Lazy Initialization of Objects</span></span>
<span data-ttu-id="e2291-105">La classe <xref:System.Lazy%601?displayProperty=nameWithType> simplifie les opérations d’initialisation tardive et d’instanciation des objets.</span><span class="sxs-lookup"><span data-stu-id="e2291-105">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="e2291-106">L’initialisation des objets de manière tardive vous évite d’avoir à créer inutilement des objets non nécessaires, ou vous permet de différer l’initialisation des objets jusqu’à ce qu’ils commencent à être utilisés.</span><span class="sxs-lookup"><span data-stu-id="e2291-106">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="e2291-107">Pour plus d’informations, consultez [Initialisation tardive](lazy-initialization.md).</span><span class="sxs-lookup"><span data-stu-id="e2291-107">For more information, see [Lazy Initialization](lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2291-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2291-108">Example</span></span>  
 <span data-ttu-id="e2291-109">L’exemple suivant montre comment initialiser une valeur avec <xref:System.Lazy%601>.</span><span class="sxs-lookup"><span data-stu-id="e2291-109">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="e2291-110">Il suppose que la variable tardive peut ne pas être nécessaire, selon que la variable `someCondition` est définie sur true ou false dans un autre code.</span><span class="sxs-lookup"><span data-stu-id="e2291-110">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e2291-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2291-111">Example</span></span>  
 <span data-ttu-id="e2291-112">L’exemple suivant montre comment utiliser la classe <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> pour initialiser un type qui est visible uniquement pour l’instance d’objet qui est exécutée sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="e2291-112">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="e2291-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2291-113">See also</span></span>

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [<span data-ttu-id="e2291-114">Initialisation tardive</span><span class="sxs-lookup"><span data-stu-id="e2291-114">Lazy Initialization</span></span>](lazy-initialization.md)
