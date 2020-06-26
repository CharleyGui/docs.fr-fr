---
title: Assistant Débogage managé asynchronousThreadAbort
description: Examinez comment l’Assistant Débogage managé (MDA) MDA AsynchronousThreadAbort est activé lorsqu’un thread tente de placer un abandon asynchrone dans un autre thread.
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
ms.openlocfilehash: 469372d57d9c21198353d171fec16458691eb25d
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415665"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="373c0-103">Assistant Débogage managé asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="373c0-103">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="373c0-104">L’Assistant Débogage managé (MDA) `asynchronousThreadAbort` est activé quand un thread tente d’introduire un abandon asynchrone dans un autre thread.</span><span class="sxs-lookup"><span data-stu-id="373c0-104">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="373c0-105">Les abandons de threads synchrones n’activent pas l’Assistant Débogage managé `asynchronousThreadAbort`.</span><span class="sxs-lookup"><span data-stu-id="373c0-105">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="373c0-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="373c0-106">Symptoms</span></span>
 <span data-ttu-id="373c0-107">Une application se bloque avec une exception <xref:System.Threading.ThreadAbortException> non gérée quand le thread d’application principal est abandonné.</span><span class="sxs-lookup"><span data-stu-id="373c0-107">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="373c0-108">Si l’application continuait à s’exécuter, les conséquences pourraient être pires qu’un blocage, entraînant éventuellement un endommagement supplémentaire des données.</span><span class="sxs-lookup"><span data-stu-id="373c0-108">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="373c0-109">Des opérations censées être atomiques ont probablement été interrompues après l’achèvement partiel, laissant les données d’application dans un état imprévisible.</span><span class="sxs-lookup"><span data-stu-id="373c0-109">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="373c0-110">Une exception <xref:System.Threading.ThreadAbortException> peut être générée à partir de points apparemment aléatoires dans l’exécution du code, souvent à des endroits à partir desquels une exception n’est pas censée se produire.</span><span class="sxs-lookup"><span data-stu-id="373c0-110">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="373c0-111">Le code n’est peut-être pas capable de gérer cette exception, entraînant un état endommagé.</span><span class="sxs-lookup"><span data-stu-id="373c0-111">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="373c0-112">Les symptômes peuvent varier considérablement en raison du caractère aléatoire du problème.</span><span class="sxs-lookup"><span data-stu-id="373c0-112">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="373c0-113">Cause</span><span class="sxs-lookup"><span data-stu-id="373c0-113">Cause</span></span>
 <span data-ttu-id="373c0-114">Le code dans un thread a appelé la méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> sur un thread cible pour introduire un abandon de thread asynchrone.</span><span class="sxs-lookup"><span data-stu-id="373c0-114">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="373c0-115">L’abandon de thread est asynchrone, car le code qui effectue l’appel à <xref:System.Threading.Thread.Abort%2A> s’exécute sur un thread différent de la cible de l’opération d’abandon.</span><span class="sxs-lookup"><span data-stu-id="373c0-115">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="373c0-116">Les abandons de threads synchrones ne doivent pas provoquer de problème, car le thread exécutant <xref:System.Threading.Thread.Abort%2A> doit l’avoir fait uniquement à un point de contrôle sécurisé où l’état de l’application est cohérent.</span><span class="sxs-lookup"><span data-stu-id="373c0-116">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="373c0-117">Les abandons de threads asynchrones présentent un problème, car ils sont traités à des points inattendus dans l’exécution du thread cible.</span><span class="sxs-lookup"><span data-stu-id="373c0-117">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="373c0-118">Pour éviter cela, le code écrit pour s’exécuter sur un thread susceptible d’être abandonné de cette manière aurait besoin de gérer une exception <xref:System.Threading.ThreadAbortException> presque à chaque ligne de code, en prenant soin de remettre les données d’application dans un état cohérent.</span><span class="sxs-lookup"><span data-stu-id="373c0-118">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="373c0-119">Il n’est pas réaliste de s’attendre à ce que le code soit écrit avec ce problème à l’esprit, ni d’écrire du code qui protège contre tous les cas possibles.</span><span class="sxs-lookup"><span data-stu-id="373c0-119">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="373c0-120">Les appels dans le code non managé et les blocs `finally` ne seront pas abandonnés de façon asynchrone, mais dès la sortie de l’une de ces catégories.</span><span class="sxs-lookup"><span data-stu-id="373c0-120">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="373c0-121">La cause peut être difficile à déterminer en raison du caractère aléatoire du problème.</span><span class="sxs-lookup"><span data-stu-id="373c0-121">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="373c0-122">Résolution</span><span class="sxs-lookup"><span data-stu-id="373c0-122">Resolution</span></span>
 <span data-ttu-id="373c0-123">Évitez les conceptions du code qui exigent l’utilisation d’abandons de threads asynchrones.</span><span class="sxs-lookup"><span data-stu-id="373c0-123">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="373c0-124">Il existe plusieurs approches plus appropriées pour l’interruption d’un thread cible qui ne nécessitent pas d’appel à <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="373c0-124">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="373c0-125">La plus sûre consiste à introduire un mécanisme, par exemple une propriété commune, qui envoie un signal au thread cible pour demander une interruption.</span><span class="sxs-lookup"><span data-stu-id="373c0-125">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="373c0-126">Le thread cible vérifie ce signal à certains points de contrôle sécurisés.</span><span class="sxs-lookup"><span data-stu-id="373c0-126">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="373c0-127">S’il remarque qu’une interruption a été demandée, il peut s’arrêter correctement.</span><span class="sxs-lookup"><span data-stu-id="373c0-127">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="373c0-128">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="373c0-128">Effect on the Runtime</span></span>
 <span data-ttu-id="373c0-129">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="373c0-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="373c0-130">Il signale uniquement des données sur les abandons de threads asynchrones.</span><span class="sxs-lookup"><span data-stu-id="373c0-130">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="373c0-131">Output</span><span class="sxs-lookup"><span data-stu-id="373c0-131">Output</span></span>
 <span data-ttu-id="373c0-132">L’Assistant Débogage managé signale l’ID du thread qui exécute l’abandon et l’ID du thread qui est la cible de l’abandon.</span><span class="sxs-lookup"><span data-stu-id="373c0-132">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="373c0-133">Ces ID ne sont jamais les mêmes, car ce scénario se limite aux abandons asynchrones.</span><span class="sxs-lookup"><span data-stu-id="373c0-133">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="373c0-134">Configuration</span><span class="sxs-lookup"><span data-stu-id="373c0-134">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="373c0-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="373c0-135">Example</span></span>
 <span data-ttu-id="373c0-136">L’activation de l’Assistant Débogage managé `asynchronousThreadAbort` nécessite uniquement un appel à <xref:System.Threading.Thread.Abort%2A> sur un thread en cours d’exécution distinct.</span><span class="sxs-lookup"><span data-stu-id="373c0-136">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="373c0-137">Tenez compte des conséquences si le contenu de la fonction de démarrage du thread était un ensemble d’opérations plus complexes susceptibles d’être interrompues à un point arbitraire par l’abandon.</span><span class="sxs-lookup"><span data-stu-id="373c0-137">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="373c0-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="373c0-138">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="373c0-139">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="373c0-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
