---
title: virtualCERCall (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: 49ba4e7ca0b8ed2e433053130bc9ca2742c72ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217196"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="9eebc-102">virtualCERCall (MDA)</span><span class="sxs-lookup"><span data-stu-id="9eebc-102">virtualCERCall MDA</span></span>
<span data-ttu-id="9eebc-103">L’Assistant Débogage managé `virtualCERCall` est activé comme un avertissement indiquant qu’un site d’appel dans un graphique des appels d’une région d’exécution limitée fait référence à une cible virtuelle, c’est-à-dire un appel virtuel à une méthode virtuelle non finale ou un appel à l’aide d’une interface.</span><span class="sxs-lookup"><span data-stu-id="9eebc-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="9eebc-104">Le CLR (Common Language Runtime) ne peut pas prédire la méthode de destination de ces appels uniquement à partir du langage intermédiaire et de l’analyse des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9eebc-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="9eebc-105">En conséquence, l’arborescence des appels ne peut pas être préparée dans le cadre du graphique d’une région d’exécution limitée et les interruptions de threads dans cette sous-arborescence ne peuvent pas être automatiquement bloquées.</span><span class="sxs-lookup"><span data-stu-id="9eebc-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="9eebc-106">Cet Assistant Débogage managé vous avertit des cas où il peut s’avérer nécessaire d’étendre une région d’exécution limitée en utilisant des appels explicites à la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> dès que les informations supplémentaires requises pour calculer la cible de l’appel sont connues au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9eebc-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9eebc-107">Symptômes</span><span class="sxs-lookup"><span data-stu-id="9eebc-107">Symptoms</span></span>  
 <span data-ttu-id="9eebc-108">Des régions d’exécution limitée ne s’exécutent pas lors de l’interruption d’un thread ou du déchargement d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="9eebc-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9eebc-109">Cause :</span><span class="sxs-lookup"><span data-stu-id="9eebc-109">Cause</span></span>  
 <span data-ttu-id="9eebc-110">Une région d’exécution limitée contient un appel à une méthode virtuelle qui ne peut pas être préparée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="9eebc-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9eebc-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="9eebc-111">Resolution</span></span>  
 <span data-ttu-id="9eebc-112">Appelez <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> pour la méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9eebc-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9eebc-113">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="9eebc-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="9eebc-114">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="9eebc-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9eebc-115">Output</span><span class="sxs-lookup"><span data-stu-id="9eebc-115">Output</span></span>  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="9eebc-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="9eebc-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9eebc-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="9eebc-117">Example</span></span>  
  
```csharp
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eebc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eebc-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="9eebc-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="9eebc-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9eebc-120">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="9eebc-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
