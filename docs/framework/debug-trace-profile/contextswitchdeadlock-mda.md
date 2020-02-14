---
title: Assistant Débogage managé contextSwitchDeadlock
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
ms.openlocfilehash: e3fc4a2cb35cdcc713ba0ef362071083af08a27b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217559"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="e548f-102">Assistant Débogage managé contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="e548f-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="e548f-103">L'Assistant Débogage managé `contextSwitchDeadlock` est activé quand un interblocage est détecté pendant une tentative de transition de contexte COM.</span><span class="sxs-lookup"><span data-stu-id="e548f-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="e548f-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="e548f-104">Symptoms</span></span>

<span data-ttu-id="e548f-105">Le symptôme le plus courant est l'absence de retour suite à un appel sur un composant COM non managé à partir d'un code managé.</span><span class="sxs-lookup"><span data-stu-id="e548f-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="e548f-106">Un autre symptôme est l'augmentation de l'utilisation de la mémoire dans le temps.</span><span class="sxs-lookup"><span data-stu-id="e548f-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="e548f-107">Cause :</span><span class="sxs-lookup"><span data-stu-id="e548f-107">Cause</span></span>

<span data-ttu-id="e548f-108">La cause la plus probable est qu'un thread cloisonné ne pompe pas les messages.</span><span class="sxs-lookup"><span data-stu-id="e548f-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="e548f-109">Soit le thread cloisonné attend sans pomper les messages, soit il effectue des opérations de longue durée qui empêchent le pompage de la file d'attente des messages.</span><span class="sxs-lookup"><span data-stu-id="e548f-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="e548f-110">L'augmentation de l'utilisation de la mémoire dans le temps est due au fait que le thread du finaliseur appelle `Release` sur un composant COM non managé qui ne répond pas à cet appel.</span><span class="sxs-lookup"><span data-stu-id="e548f-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="e548f-111">Dans cette situation, le finaliseur ne peut pas récupérer d'autres objets.</span><span class="sxs-lookup"><span data-stu-id="e548f-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="e548f-112">Par défaut, le modèle de thread du thread principal des applications console Visual Basic est le modèle cloisonné.</span><span class="sxs-lookup"><span data-stu-id="e548f-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="e548f-113">Cet Assistant Débogage managé est activé si un thread cloisonné utilise l'interopérabilité COM soit directement, soit indirectement par le biais du Common Language Runtime ou d'un contrôle tiers.</span><span class="sxs-lookup"><span data-stu-id="e548f-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="e548f-114">Pour éviter d'activer cet Assistant Débogage managé dans une application console Visual Basic, appliquez l'attribut <xref:System.MTAThreadAttribute> à la méthode principale ou modifiez l'application pour qu'elle pompe les messages.</span><span class="sxs-lookup"><span data-stu-id="e548f-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="e548f-115">Il est possible que cet Assistant Débogage managé soit faussement activé quand toutes les conditions suivantes sont réunies :</span><span class="sxs-lookup"><span data-stu-id="e548f-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="e548f-116">Une application crée des composants COM à partir de threads cloisonnés soit directement, soit indirectement par le biais de bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="e548f-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="e548f-117">L'application a été arrêtée dans le débogueur et l'utilisateur a continué d'exécuter l'application ou a effectué une opération pas à pas.</span><span class="sxs-lookup"><span data-stu-id="e548f-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="e548f-118">Le débogage non managé n'est pas activé.</span><span class="sxs-lookup"><span data-stu-id="e548f-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="e548f-119">Pour déterminer si l'Assistant Débogage managé est faussement activé, désactivez tous les points d'arrêt, redémarrez l'application et laissez-la s'exécuter sans l'interrompre.</span><span class="sxs-lookup"><span data-stu-id="e548f-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="e548f-120">Si l'Assistant Débogage managé n'est pas activé, l'activation initiale était probablement fausse.</span><span class="sxs-lookup"><span data-stu-id="e548f-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="e548f-121">Dans ce cas, désactivez l'Assistant Débogage managé pour éviter des interférences avec la session de débogage.</span><span class="sxs-lookup"><span data-stu-id="e548f-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="e548f-122">Cet Assistant Débogage managé est défini par défaut pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e548f-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="e548f-123">Pour plus d’informations sur la désactivation des MDA, consultez [diagnostic des erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="e548f-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="e548f-124">Résolution</span><span class="sxs-lookup"><span data-stu-id="e548f-124">Resolution</span></span>

<span data-ttu-id="e548f-125">Appliquez les règles COM relatives au pompage des messages de thread cloisonné.</span><span class="sxs-lookup"><span data-stu-id="e548f-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="e548f-126">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="e548f-126">Effect on the Runtime</span></span>

<span data-ttu-id="e548f-127">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="e548f-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="e548f-128">Il fournit uniquement des informations sur les contextes COM.</span><span class="sxs-lookup"><span data-stu-id="e548f-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="e548f-129">Output</span><span class="sxs-lookup"><span data-stu-id="e548f-129">Output</span></span>

<span data-ttu-id="e548f-130">Message décrivant le contexte actuel et le contexte cible.</span><span class="sxs-lookup"><span data-stu-id="e548f-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="e548f-131">Configuration</span><span class="sxs-lookup"><span data-stu-id="e548f-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="e548f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e548f-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e548f-133">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="e548f-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e548f-134">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="e548f-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
