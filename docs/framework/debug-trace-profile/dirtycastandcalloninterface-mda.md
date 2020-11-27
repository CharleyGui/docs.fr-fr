---
title: Assistant Débogage managé dirtyCastAndCallOnInterface
description: Passez en revue l’Assistant Débogage managé dirtyCastAndCallOnInterface, qui est appelé lorsque des appels vtable à liaison anticipée sont effectués sur des interfaces de classe uniquement à liaison tardive.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
ms.openlocfilehash: 49a2930d91e76856436480512360e8b9f9fd3d7a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273579"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="b2432-103">Assistant Débogage managé dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="b2432-103">dirtyCastAndCallOnInterface MDA</span></span>

<span data-ttu-id="b2432-104">L'Assistant Débogage managé (MDA) `dirtyCastAndCallOnInterface` est activé quand une tentative d'appel à liaison anticipée par un vtable est effectuée sur une interface de classes qui a été marquée comme étant à liaison tardive uniquement.</span><span class="sxs-lookup"><span data-stu-id="b2432-104">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b2432-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="b2432-105">Symptoms</span></span>  

 <span data-ttu-id="b2432-106">Une application lève une violation d'accès ou a un comportement inattendu quand un appel à liaison anticipée est placé via COM dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="b2432-106">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b2432-107">Cause</span><span class="sxs-lookup"><span data-stu-id="b2432-107">Cause</span></span>  

 <span data-ttu-id="b2432-108">Le code tente un appel à liaison anticipée par un vtable via une interface de classes qui est à liaison tardive uniquement.</span><span class="sxs-lookup"><span data-stu-id="b2432-108">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="b2432-109">Notez que, par défaut, les interfaces de classes sont identifiées comme étant à liaison tardive uniquement.</span><span class="sxs-lookup"><span data-stu-id="b2432-109">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="b2432-110">Elles peuvent également être identifiées comme étant à liaison tardive à l'aide de l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> défini à la valeur <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="b2432-110">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b2432-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="b2432-111">Resolution</span></span>  

 <span data-ttu-id="b2432-112">La résolution recommandée consiste à définir une interface explicite destinée à être utilisée par COM et à faire appeler les clients COM via cette interface plutôt que via l’interface de classes générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b2432-112">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="b2432-113">L'appel de COM peut aussi être changé en appel à liaison tardive via `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="b2432-113">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="b2432-114">Enfin, il est possible d'identifier la classe comme <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) pour permettre aux appels à liaison anticipée d'être placés par COM. L'utilisation de <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> est toutefois fortement déconseillée en raison des limitations du contrôle de version décrites dans <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b2432-114">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b2432-115">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="b2432-115">Effect on the Runtime</span></span>  

 <span data-ttu-id="b2432-116">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="b2432-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="b2432-117">Il fournit uniquement des données relatives aux appels à liaison anticipée qui sont effectués sur les interfaces à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="b2432-117">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b2432-118">Output</span><span class="sxs-lookup"><span data-stu-id="b2432-118">Output</span></span>  

 <span data-ttu-id="b2432-119">Nom de la méthode ou nom du champ qui fait l'objet d'un accès à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="b2432-119">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b2432-120">Configuration</span><span class="sxs-lookup"><span data-stu-id="b2432-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2432-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2432-121">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="b2432-122">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="b2432-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
