---
title: Assistant Débogage managé asynchronousThreadAbort
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
ms.openlocfilehash: d0c78e6d52ae4a5b3a24e0bb4278b2e8a1b98751
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217582"
---
# <a name="asynchronousthreadabort-mda"></a>Assistant Débogage managé asynchronousThreadAbort
L’Assistant Débogage managé (MDA) `asynchronousThreadAbort` est activé quand un thread tente d’introduire un abandon asynchrone dans un autre thread. Les abandons de threads synchrones n’activent pas l’Assistant Débogage managé `asynchronousThreadAbort`.

## <a name="symptoms"></a>Symptômes
 Une application se bloque avec une exception <xref:System.Threading.ThreadAbortException> non gérée quand le thread d’application principal est abandonné. Si l’application continuait à s’exécuter, les conséquences pourraient être pires qu’un blocage, entraînant éventuellement un endommagement supplémentaire des données.

 Des opérations censées être atomiques ont probablement été interrompues après l’achèvement partiel, laissant les données d’application dans un état imprévisible. Une exception <xref:System.Threading.ThreadAbortException> peut être générée à partir de points apparemment aléatoires dans l’exécution du code, souvent à des endroits à partir desquels une exception n’est pas censée se produire. Le code n’est peut-être pas capable de gérer cette exception, entraînant un état endommagé.

 Les symptômes peuvent varier considérablement en raison du caractère aléatoire du problème.

## <a name="cause"></a>Cause :
 Le code dans un thread a appelé la méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> sur un thread cible pour introduire un abandon de thread asynchrone. L’abandon de thread est asynchrone, car le code qui effectue l’appel à <xref:System.Threading.Thread.Abort%2A> s’exécute sur un thread différent de la cible de l’opération d’abandon. Les abandons de threads synchrones ne doivent pas provoquer de problème, car le thread exécutant <xref:System.Threading.Thread.Abort%2A> doit l’avoir fait uniquement à un point de contrôle sécurisé où l’état de l’application est cohérent.

 Les abandons de threads asynchrones présentent un problème, car ils sont traités à des points inattendus dans l’exécution du thread cible. Pour éviter cela, le code écrit pour s’exécuter sur un thread susceptible d’être abandonné de cette manière aurait besoin de gérer une exception <xref:System.Threading.ThreadAbortException> presque à chaque ligne de code, en prenant soin de remettre les données d’application dans un état cohérent. Il n’est pas réaliste de s’attendre à ce que le code soit écrit avec ce problème à l’esprit, ni d’écrire du code qui protège contre tous les cas possibles.

 Les appels dans le code non managé et les blocs `finally` ne seront pas abandonnés de façon asynchrone, mais dès la sortie de l’une de ces catégories.

 La cause peut être difficile à déterminer en raison du caractère aléatoire du problème.

## <a name="resolution"></a>Résolution
 Évitez les conceptions du code qui exigent l’utilisation d’abandons de threads asynchrones. Il existe plusieurs approches plus appropriées pour l’interruption d’un thread cible qui ne nécessitent pas d’appel à <xref:System.Threading.Thread.Abort%2A>. La plus sûre consiste à introduire un mécanisme, par exemple une propriété commune, qui envoie un signal au thread cible pour demander une interruption. Le thread cible vérifie ce signal à certains points de contrôle sécurisés. S’il remarque qu’une interruption a été demandée, il peut s’arrêter correctement.

## <a name="effect-on-the-runtime"></a>Effet sur le runtime
 Cet Assistant Débogage managé n'a aucun effet sur le CLR. Il signale uniquement des données sur les abandons de threads asynchrones.

## <a name="output"></a>Output
 L’Assistant Débogage managé signale l’ID du thread qui exécute l’abandon et l’ID du thread qui est la cible de l’abandon. Ces ID ne sont jamais les mêmes, car ce scénario se limite aux abandons asynchrones.

## <a name="configuration"></a>Configuration

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Exemple
 L’activation de l’Assistant Débogage managé `asynchronousThreadAbort` nécessite uniquement un appel à <xref:System.Threading.Thread.Abort%2A> sur un thread en cours d’exécution distinct. Tenez compte des conséquences si le contenu de la fonction de démarrage du thread était un ensemble d’opérations plus complexes susceptibles d’être interrompues à un point arbitraire par l’abandon.

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
