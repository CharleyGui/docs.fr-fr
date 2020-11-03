---
title: Meilleures pratiques pour le threading managé
description: Découvrez les meilleures pratiques de Threading managé dans .NET. Travaillez avec des situations difficiles, telles que la coordination de nombreux threads ou la gestion des threads de blocage.
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET], design guidelines
- threading [.NET], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
ms.openlocfilehash: 88e1f34388cd58fef59bc4005bcaf630c59a661e
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189002"
---
# <a name="managed-threading-best-practices"></a>Bonnes pratiques pour le threading managé

Le multithreading nécessite une programmation attentive. Pour réduire la complexité de la plupart des tâches, il vous suffit de mettre en file d’attente les requêtes à exécuter par les threads d’un pool de threads. Cet article vous permet de remédier aux situations plus complexes, telles que la coordination du travail de plusieurs threads ou la gestion des threads bloqués.  
  
> [!NOTE]
> À partir de .NET Framework 4, la bibliothèque parallèle de tâches et PLINQ fournissent des API qui réduisent la complexité et les risques de la programmation multithread. Pour plus d’informations, consultez la page [Programmation parallèle dans .NET](../parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Interblocages et conditions de concurrence  
 Le multithreading résout les problèmes de débit et de réactivité, mais, ce faisant, occasionne de nouveaux problèmes : les interblocages et les conditions de concurrence.  
  
### <a name="deadlocks"></a>Blocages  
 Un interblocage se produit lorsque chacun des deux threads tente de verrouiller une ressource déjà verrouillée par l’autre thread. Aucun des deux threads ne peut donc poursuivre l’exécution.  
  
 De nombreuses méthodes des classes de threading managé fournissent des délais d’expiration conçus pour faciliter la détection des interblocages. Par exemple, le code ci-après tente d’acquérir un verrou sur un objet nommé `lockObject`. Si le verrou n’est pas obtenu en 300 millisecondes, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retourne `false`.  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a>Conditions de concurrence  
 Une condition de concurrence est un bogue qui survient lorsque le résultat d’un programme dépend du thread qui atteint le premier un bloc de code spécifique. L’exécution du programme à plusieurs reprises produit des résultats différents, et le résultat d’une exécution donnée n’est donc pas prévisible.  
  
 Un exemple simple de condition de concurrence correspond à l’incrémentation d’un champ. Supposons qu’une classe comporte un champ **static** privé ( **Shared** en Visual Basic) qui est incrémenté chaque fois qu’une instance de la classe est créée, à l’aide d’un code tel que `objCt++;` (C#) ou `objCt += 1` (Visual Basic). Cette opération nécessite le chargement de la valeur de `objCt` dans un registre, l’incrémentation de la valeur, puis son stockage dans `objCt`.  
  
 Dans une application multithread, il est possible qu’un thread ayant chargé et incrémenté la valeur soit devancé par un autre thread qui exécute ces trois étapes ; lorsque le premier thread reprend l’exécution et stocke sa valeur, il remplace alors la valeur de `objCt` sans tenir compte du fait qu’elle a changé dans l’intervalle.  
  
 Cette condition de concurrence particulière est facile à éviter en utilisant des méthodes de la classe <xref:System.Threading.Interlocked>, telles que <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>. Pour découvrir d’autres techniques de synchronisation des données entre plusieurs threads, consultez l’article [Synchronisation des données pour le multithreading](synchronizing-data-for-multithreading.md).  
  
 Des conditions de concurrence peuvent également survenir lorsque vous synchronisez les activités de plusieurs threads. Chaque fois que vous écrivez une ligne de code, vous devez prendre en compte ce qui peut se produire si un thread est devancé par un autre thread avant d’avoir exécuté la ligne (ou avant toute instruction machine individuelle composant la ligne).  
  
## <a name="static-members-and-static-constructors"></a>Membres static et constructeurs static  
 Une classe n’est pas initialisée tant que son constructeur de classe (constructeur `static` en C#, `Shared Sub New` en Visual Basic) n’a pas fini de s’exécuter. Pour empêcher l’exécution de code sur un type qui n’est pas initialisé, le common language runtime bloque tous les appels d’autres threads aux membres `static` de la classe (membres `Shared` en Visual Basic) jusqu’à la fin de l’exécution du constructeur de classe.  
  
 Par exemple, si un constructeur de classe démarre un nouveau thread, et que la procédure de thread appelle un membre `static` de la classe, le nouveau thread se bloque jusqu’à la fin du constructeur de classe.  
  
 Cela s’applique à n’importe quel type pouvant comporter un constructeur `static`.  

## <a name="number-of-processors"></a>Nombre de processeurs

Le fait que plusieurs processeurs ou un seul soient disponibles sur un système peut influencer l’architecture multithread. Pour plus d’informations, consultez [Nombre de processeurs](/previous-versions/dotnet/netframework-1.1/1c9txz50(v=vs.71)#number-of-processors).

Utilisez la <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> propriété pour déterminer le nombre de processeurs disponibles au moment de l’exécution.
  
## <a name="general-recommendations"></a>Recommandations générales  
 Lorsque vous utilisez plusieurs threads, tenez compte des recommandations suivantes :  
  
- N’utilisez pas <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour mettre fin à d’autres threads. L’appel de la méthode **Abort** sur un autre thread équivaut à lever une exception sur ce dernier sans connaître le stade précis du traitement atteint par ce thread.  
  
- N’utilisez pas <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> pour synchroniser les activités de plusieurs threads. Utilisez <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.Monitor>.  
  
- Ne contrôlez pas l’exécution des threads de travail à partir de votre programme principal (à l’aide d’événements, par exemple). Concevez plutôt votre programme pour que les threads de travail soient chargés d’attendre que le travail devienne disponible, d’exécuter ce travail, puis d’en informer les autres parties de votre programme lorsqu’ils ont terminé. Si vos threads de travail ne se bloquent pas, envisagez d’utiliser les threads d’un pool de threads. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> est utile dans les situations où les threads de travail se bloquent.  
  
- N’utilisez pas de types en tant qu’objets de verrou. Autrement dit, évitez un code tel que `lock(typeof(X))` en C# ou `SyncLock(GetType(X))` en Visual Basic, ou l’utilisation de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> avec des objets <xref:System.Type>. Pour un type donné, il existe une seule instance de <xref:System.Type?displayProperty=nameWithType> par domaine d’application. Si le type sur lequel vous utilisez un verrou est public, un code différent du vôtre peut utiliser des verrous sur ce type, entraînant ainsi des interblocages. Pour découvrir les autres problèmes, consultez l’article [Meilleures pratiques pour la fiabilité](../../framework/performance/reliability-best-practices.md).  
  
- Procédez avec précaution lorsque vous utilisez des verrous sur des instances, par exemple `lock(this)` en C# ou `SyncLock(Me)` en Visual Basic. Si un autre code de votre application, externe au type, utilise un verrou sur l’objet, des interblocages risquent de se produire.  
  
- Assurez-vous qu’un thread entré dans un moniteur quitte toujours ce dernier, même si une exception se produit pendant que le thread se trouve dans le moniteur. L’instruction C# [lock](../../csharp/language-reference/keywords/lock-statement.md) et l’instruction Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) assurent automatiquement ce comportement, en employant un bloc **finally** pour garantir l’appel de la méthode <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>. Si vous n’êtes pas en mesure de garantir l’appel de la méthode **Exit** , vous pouvez modifier votre conception de façon à utiliser **Mutex** . Un mutex est automatiquement libéré lorsque le thread auquel il appartient a terminé.  
  
- Utilisez plusieurs threads pour les tâches qui nécessitent des ressources différentes, et évitez d’attribuer plusieurs threads à une même ressource. Par exemple, vous tirerez avantage du fait que les tâches impliquant des E/S disposent de leur propre thread, car ce thread se bloquera lors des opérations d’E/S et permettra ainsi à d’autres threads de s’exécuter. L’entrée utilisateur est une autre ressource tirant profit d’un thread dédié. Sur un ordinateur monoprocesseur, une tâche qui exige de multiples calculs coexiste avec l’entrée utilisateur et avec les tâches qui impliquent des E/S, mais plusieurs tâches nécessitant de nombreux calculs entrent en concurrence les unes avec les autres.  
  
- Envisagez d’utiliser les méthodes de la classe <xref:System.Threading.Interlocked> pour les modifications d’état simples, plutôt que de recourir à l’instruction `lock` (`SyncLock` en Visual Basic). L’instruction `lock` est un outil à usage général efficace, mais la classe <xref:System.Threading.Interlocked> offre de meilleures performances pour les mises à jour qui doivent être atomiques. En interne, elle exécute un seul préfixe de verrou s’il n’existe aucun conflit. Lors des phases de révision du code, examinez le code semblable à celui des exemples ci-dessous. Dans le premier exemple, une variable d’état est incrémentée :  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)
    {  
        myField++;  
    }  
    ```  
  
     Vous pouvez améliorer les performances en utilisant la méthode <xref:System.Threading.Interlocked.Increment%2A> au lieu de l’instruction`lock`, comme suit :  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > Utilisez la <xref:System.Threading.Interlocked.Add%2A> méthode pour les incréments atomiques supérieurs à 1.  
  
     Dans le second exemple, une variable de type référence est uniquement mise à jour s’il s’agit d’une référence null (`Nothing` en Visual Basic).  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            x ??= y;
        }  
    }  
    ```  
  
     Les performances peuvent être améliorées en utilisant à la place la méthode <xref:System.Threading.Interlocked.CompareExchange%2A> comme suit :  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > La <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> surcharge de méthode fournit une alternative de type sécurisé pour les types référence.
  
## <a name="recommendations-for-class-libraries"></a>Recommandations relatives aux bibliothèques de classes  
 Lorsque vous concevez des bibliothèques de classes pour le multithreading, tenez compte des recommandations suivantes :  
  
- Dans la mesure du possible, évitez toute nécessité de synchronisation. Cette consigne s’applique tout particulièrement pour le code très sollicité. Par exemple, un algorithme peut être ajusté de façon à tolérer une condition de concurrence plutôt que de l’éliminer. Une synchronisation inutile dégrade les performances et entraîne un risque d’interblocages et de conditions de concurrence.  
  
- Définissez les données static (`Shared` en Visual Basic) comme thread-safe par défaut.  
  
- Ne définissez pas les données d’instance comme thread-safe par défaut. L’ajout de verrous pour créer un code thread-safe diminue les performances, multiplie les conflits de verrou et occasionne un risque d’interblocages. Dans les modèles d’application communs, le code utilisateur n’est exécuté que par un seul thread à la fois, ce qui minimise la nécessité d’une cohérence de thread. Pour cette raison, les bibliothèques de classes .NET ne sont pas thread-safe par défaut.  
  
- Évitez de fournir des méthodes statiques qui modifient l’état statique. Dans les scénarios de serveur courants, l’état statique est partagé entre les requêtes, ce qui signifie que plusieurs threads peuvent exécuter ce code en même temps. Ceci occasionne un risque de bogues de threading. Envisagez d’utiliser un modèle de conception qui encapsule les données dans des instances non partagées entre les requêtes. En outre, si les données static sont synchronisées, les appels entre les méthodes statiques qui modifient l’état peuvent entraîner des interblocages ou une synchronisation redondante et dégrader ainsi les performances.  
  
## <a name="see-also"></a>Voir aussi

- [Thread](index.md)
- [Threads et threading](threads-and-threading.md)
