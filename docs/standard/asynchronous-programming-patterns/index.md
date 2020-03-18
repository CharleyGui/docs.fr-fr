---
title: Modèles de programmation asynchrone
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: e1efe9c3eb57f317def91e527506c358eb086679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160051"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="d5f1d-102">Modèles de programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="d5f1d-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="d5f1d-103">.NET propose trois modèles d’exécution d’opérations asynchrones :</span><span class="sxs-lookup"><span data-stu-id="d5f1d-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="d5f1d-104">**Modèle asynchrone (TAP) basé sur les tâches**, qui utilise une seule méthode pour représenter l’initiation et l’achèvement d’une opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="d5f1d-105">TAP a été introduit avec le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="d5f1d-106">**Il est recommandé pour la programmation asynchrone dans .NET.**</span><span class="sxs-lookup"><span data-stu-id="d5f1d-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="d5f1d-107">Les mots clés [async](../../csharp/language-reference/keywords/async.md) et [await](../../csharp/language-reference/operators/await.md) en C#, ainsi que les opérateurs [Async](../../visual-basic/language-reference/modifiers/async.md) et [Await](../../visual-basic/language-reference/operators/await-operator.md) en Visual Basic, ajoutent au modèle TAP la prise en charge des langages.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-107">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="d5f1d-108">Pour plus d’informations, consultez [Modèle asynchrone basé sur des tâches (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="d5f1d-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="d5f1d-109">Le **modèle asynchrone basé sur les événements (EAP)**, qui est le modèle hérité basé sur les événements pour fournir un comportement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="d5f1d-110">Il nécessite une méthode avec le suffixe `Async`, ainsi qu’un ou plusieurs événements, des types de délégués de gestionnaire d’événements et des types dérivés de `EventArg`.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="d5f1d-111">Ce modèle a été introduit avec le .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="d5f1d-112">Il n’est plus recommandé pour les nouveaux développements.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="d5f1d-113">Pour plus d'informations, consultez [Modèle asynchrone basé sur des événements (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="d5f1d-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="d5f1d-114">Le **modèle de programmation asynchrone (APM)**, également appelé modèle <xref:System.IAsyncResult>, qui est le modèle hérité qui utilise l’interface <xref:System.IAsyncResult> pour fournir un comportement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="d5f1d-115">Dans ce modèle, les opérations synchrones nécessitent les méthodes `Begin` et `End` (par exemple, `BeginWrite` et `EndWrite` pour implémenter une opération d’écriture asynchrone).</span><span class="sxs-lookup"><span data-stu-id="d5f1d-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="d5f1d-116">Ce modèle n’est plus recommandé pour un futur développement.</span><span class="sxs-lookup"><span data-stu-id="d5f1d-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="d5f1d-117">Pour plus d’informations sur la programmation asynchrone, consultez [Modèle de programmation asynchrone (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="d5f1d-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="d5f1d-118">Comparaison des modèles</span><span class="sxs-lookup"><span data-stu-id="d5f1d-118">Comparison of patterns</span></span>

<span data-ttu-id="d5f1d-119">Pour comprendre rapidement la façon dont chacun des trois modèles modélise les opérations asynchrones, prenons une méthode `Read` qui lit une quantité de données spécifiée dans une mémoire tampon fournie, en commençant à l'offset spécifié :</span><span class="sxs-lookup"><span data-stu-id="d5f1d-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="d5f1d-120">Le modèle TAP de cette méthode exposerait l’unique méthode `ReadAsync` suivante :</span><span class="sxs-lookup"><span data-stu-id="d5f1d-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="d5f1d-121">Le modèle EAP exposerait l'ensemble de types et de membres suivant :</span><span class="sxs-lookup"><span data-stu-id="d5f1d-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="d5f1d-122">Le modèle APM exposerait les méthodes `BeginRead` et `EndRead` :</span><span class="sxs-lookup"><span data-stu-id="d5f1d-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="d5f1d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5f1d-123">See also</span></span>

- [<span data-ttu-id="d5f1d-124">Async en détail</span><span class="sxs-lookup"><span data-stu-id="d5f1d-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="d5f1d-125">Programmation asynchrone en C#</span><span class="sxs-lookup"><span data-stu-id="d5f1d-125">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="d5f1d-126">Programmation asynchrone en F#</span><span class="sxs-lookup"><span data-stu-id="d5f1d-126">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="d5f1d-127">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5f1d-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
