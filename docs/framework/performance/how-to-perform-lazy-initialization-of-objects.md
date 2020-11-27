---
title: 'Procédure : Effectuer une initialisation tardive d’objets'
description: Découvrez comment effectuer une initialisation tardive des objets à l’aide de la classe System. Lazy <T> . L’initialisation tardive signifie que les objets ne sont pas créés s’ils ne sont jamais nécessaires.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
ms.openlocfilehash: 3de0d8ea8266931c2bcda5c59c1fef97602673d5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278126"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Procédure : Effectuer une initialisation tardive d’objets

La classe <xref:System.Lazy%601?displayProperty=nameWithType> simplifie les opérations d’initialisation tardive et d’instanciation des objets. L’initialisation des objets de manière tardive vous évite d’avoir à créer inutilement des objets non nécessaires, ou vous permet de différer l’initialisation des objets jusqu’à ce qu’ils commencent à être utilisés. Pour plus d’informations, consultez [Initialisation tardive](lazy-initialization.md).  
  
## <a name="example"></a> Exemple  

 L’exemple suivant montre comment initialiser une valeur avec <xref:System.Lazy%601>. Il suppose que la variable tardive peut ne pas être nécessaire, selon que la variable `someCondition` est définie sur true ou false dans un autre code.  
  
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
  
## <a name="example"></a> Exemple  

 L’exemple suivant montre comment utiliser la classe <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> pour initialiser un type qui est visible uniquement pour l’instance d’objet qui est exécutée sur le thread actuel.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [Initialisation tardive](lazy-initialization.md)
