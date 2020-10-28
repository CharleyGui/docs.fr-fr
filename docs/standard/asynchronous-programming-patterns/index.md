---
title: Modèles de programmation asynchrone
description: En savoir plus sur le modèle asynchrone basé sur les tâches (TAP), le modèle asynchrone basé sur les événements (EAP), & modèle de programmation asynchrone (APM) dans .NET.
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: d8a68295836fb1e87ab82425ab0973fc1b65f4b2
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888761"
---
# <a name="asynchronous-programming-patterns"></a>Modèles de programmation asynchrone

.NET propose trois modèles d’exécution d’opérations asynchrones :  

- **Modèle asynchrone basé sur des tâches (TAP)** , qui utilise une méthode unique pour représenter l’initiation et l’achèvement d’une opération asynchrone. TAP a été introduit dans .NET Framework 4. **Il est recommandé pour la programmation asynchrone dans .NET.** Les mots clés [async](../../csharp/language-reference/keywords/async.md) et [await](../../csharp/language-reference/operators/await.md) en C#, ainsi que les opérateurs [Async](../../visual-basic/language-reference/modifiers/async.md) et [Await](../../visual-basic/language-reference/operators/await-operator.md) en Visual Basic, ajoutent au modèle TAP la prise en charge des langages. Pour plus d’informations, consultez [Modèle asynchrone basé sur des tâches (TAP)](task-based-asynchronous-pattern-tap.md).  

- Le **modèle asynchrone basé sur les événements (EAP)** , qui est le modèle hérité basé sur les événements pour fournir un comportement asynchrone. Il nécessite une méthode avec le suffixe `Async`, ainsi qu’un ou plusieurs événements, des types de délégués de gestionnaire d’événements et des types dérivés de `EventArg`. EAP a été introduit dans .NET Framework 2,0. Il n’est plus recommandé pour les nouveaux développements. Pour plus d'informations, consultez [Modèle asynchrone basé sur des événements (EAP)](event-based-asynchronous-pattern-eap.md).  

- Le **modèle de programmation asynchrone (APM)** , également appelé modèle <xref:System.IAsyncResult>, qui est le modèle hérité qui utilise l’interface <xref:System.IAsyncResult> pour fournir un comportement asynchrone. Dans ce modèle, les opérations synchrones nécessitent les méthodes `Begin` et `End` (par exemple, `BeginWrite` et `EndWrite` pour implémenter une opération d’écriture asynchrone). Ce modèle n’est plus recommandé pour un futur développement. Pour plus d’informations sur la programmation asynchrone, consultez [Modèle de programmation asynchrone (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Comparaison des modèles

Pour comprendre rapidement la façon dont chacun des trois modèles modélise les opérations asynchrones, prenons une méthode `Read` qui lit une quantité de données spécifiée dans une mémoire tampon fournie, en commençant à l'offset spécifié :  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Le modèle TAP de cette méthode exposerait l’unique méthode `ReadAsync` suivante :  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

Le modèle EAP exposerait l'ensemble de types et de membres suivant :  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
Le modèle APM exposerait les méthodes `BeginRead` et `EndRead` :  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a>Voir aussi

- [Async en détail](../async-in-depth.md)
- [Programmation asynchrone en C#](../../csharp/async.md)
- [Programmation asynchrone en F#](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Programmation asynchrone avec Async et Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
