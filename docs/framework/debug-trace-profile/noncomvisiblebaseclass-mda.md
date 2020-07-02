---
title: nonComVisibleBaseClass (MDA)
description: Consultez l’Assistant Débogage managé nonComVisibleBaseClass (MDA) qui est appelé sur les appels QueryInterface à partir du code natif qui échoue avec COR_E_INVALIDOPERATION.
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
ms.openlocfilehash: 9f32b2c57f50fcd900b1fd78f4f8df1ec656a6db
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803916"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="1d782-103">nonComVisibleBaseClass (MDA)</span><span class="sxs-lookup"><span data-stu-id="1d782-103">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="1d782-104">L'Assistant Débogage managé (MDA) `nonComVisibleBaseClass` est activé quand un appel `QueryInterface` est effectué par du code natif ou non managé sur le wrapper CCW (COM Callable Wrapper) d'une classe managée visible par COM qui dérive d'une classe de base qui ne l'est pas.</span><span class="sxs-lookup"><span data-stu-id="1d782-104">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="1d782-105">L'appel `QueryInterface` provoque l'activation de l'Assistant Débogage managé uniquement dans les cas où l'appel demande l'interface de classe ou l'interface `IDispatch` par défaut de la classe managée visible par COM.</span><span class="sxs-lookup"><span data-stu-id="1d782-105">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="1d782-106">L'Assistant Débogage managé n'est pas activé si `QueryInterface` concerne une interface explicite à laquelle est appliqué l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> et qui est implémentée explicitement par la classe visible par COM.</span><span class="sxs-lookup"><span data-stu-id="1d782-106">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1d782-107">Symptômes</span><span class="sxs-lookup"><span data-stu-id="1d782-107">Symptoms</span></span>  
 <span data-ttu-id="1d782-108">Un appel `QueryInterface` effectué à partir du code natif échoue (erreur COR_E_INVALIDOPERATION HRESULT).</span><span class="sxs-lookup"><span data-stu-id="1d782-108">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="1d782-109">L'erreur HRESULT peut être due au refus des appels `QueryInterface` par le runtime, provoquant ainsi l'activation de cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="1d782-109">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1d782-110">Cause</span><span class="sxs-lookup"><span data-stu-id="1d782-110">Cause</span></span>  
 <span data-ttu-id="1d782-111">Pour éviter des problèmes de version potentiels, le runtime n'autorise pas les appels `QueryInterface` pour l'interface de classe ou l'interface `IDispatch` par défaut d'une classe visible par COM dérivant d'une classe qui n'est pas visible par COM.</span><span class="sxs-lookup"><span data-stu-id="1d782-111">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="1d782-112">Si, par exemple, des membres publics étaient ajoutés à la classe de base non visible par COM, les clients COM existants utilisant la classe dérivée pourraient être interrompus, car la table vtable de la classe dérivée qui contient les membres de la classe de base serait modifiée.</span><span class="sxs-lookup"><span data-stu-id="1d782-112">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="1d782-113">Les interfaces explicites exposées à COM ne rencontrent pas ce problème dans la mesure où elles n'incluent pas les membres de base des interfaces de vtable.</span><span class="sxs-lookup"><span data-stu-id="1d782-113">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1d782-114">Résolution</span><span class="sxs-lookup"><span data-stu-id="1d782-114">Resolution</span></span>  
 <span data-ttu-id="1d782-115">N'exposez pas l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="1d782-115">Do not expose the class interface.</span></span> <span data-ttu-id="1d782-116">Définissez une interface explicite et appliquez-lui l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1d782-116">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1d782-117">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="1d782-117">Effect on the Runtime</span></span>  
 <span data-ttu-id="1d782-118">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="1d782-118">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1d782-119">Output</span><span class="sxs-lookup"><span data-stu-id="1d782-119">Output</span></span>  
 <span data-ttu-id="1d782-120">La sortie ci-dessous est un exemple de message qui est retourné après un appel `QueryInterface` effectué sur une classe `Derived` visible par COM dérivant d'une classe `Base` non visible par COM.</span><span class="sxs-lookup"><span data-stu-id="1d782-120">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM
visible managed class 'Derived'. However since this class derives from
non COM visible class 'Base', the QueryInterface call will fail. This
is done to prevent the non COM visible base class from being
constrained by the COM versioning rules.
```  
  
## <a name="configuration"></a><span data-ttu-id="1d782-121">Configuration</span><span class="sxs-lookup"><span data-stu-id="1d782-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d782-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d782-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1d782-123">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="1d782-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1d782-124">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1d782-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
