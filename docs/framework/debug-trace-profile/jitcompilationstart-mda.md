---
title: Assistant Débogage managé jitCompilationStart
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 9cae942bc01e9263720dbfe9acfb21bbb70bc548
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216258"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="f9a5a-102">Assistant Débogage managé jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="f9a5a-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="f9a5a-103">L’Assistant Débogage managé `jitCompilationStart` est activé pour signaler le moment où le compilateur juste-à-temps (JIT, Just-In-Time) commence à compiler une fonction.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f9a5a-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="f9a5a-104">Symptoms</span></span>  
 <span data-ttu-id="f9a5a-105">La taille du jeu de travail augmente pour un programme qui est déjà au format d’image natif, car mscorjit.dll est chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f9a5a-106">Cause :</span><span class="sxs-lookup"><span data-stu-id="f9a5a-106">Cause</span></span>  
 <span data-ttu-id="f9a5a-107">Les assemblys dont dépend le programme n’ont pas tous été générés au format natif, ou ceux qui l’ont été ne sont pas correctement inscrits.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f9a5a-108">Résolution</span><span class="sxs-lookup"><span data-stu-id="f9a5a-108">Resolution</span></span>  
 <span data-ttu-id="f9a5a-109">L’activation de cet Assistant Débogage managé vous permet de déterminer la fonction qui est compilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="f9a5a-110">Déterminez si l’assembly qui contient la fonction est généré au format natif et s’il est correctement inscrit.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f9a5a-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="f9a5a-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="f9a5a-112">Cet Assistant Débogage managé enregistre un message juste avant qu’une méthode ne soit compilée juste-à-temps, de sorte que son activation a un impact significatif sur les performances.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="f9a5a-113">Notez que, si une méthode est inline, cet Assistant Débogage managé ne générera pas de message séparé.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f9a5a-114">Output</span><span class="sxs-lookup"><span data-stu-id="f9a5a-114">Output</span></span>  
 <span data-ttu-id="f9a5a-115">L’exemple de code suivant illustre une sortie.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-115">The following code sample shows sample output.</span></span> <span data-ttu-id="f9a5a-116">Dans ce cas, la sortie montre que, dans l’assembly Test, la méthode m sur la classe ns2.CO a été compilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="f9a5a-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="f9a5a-117">Configuration</span></span>  
 <span data-ttu-id="f9a5a-118">Le fichier de configuration suivant présente divers filtres qui peuvent être utilisés pour filtrer les méthodes signalées quand elles sont d’abord compilées juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="f9a5a-119">Vous pouvez spécifier que toutes les méthodes soient signalées en définissant la valeur de l’attribut Name sur \*.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f9a5a-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9a5a-120">Example</span></span>  
 <span data-ttu-id="f9a5a-121">L’exemple de code suivant doit normalement être utilisé avec le fichier de configuration précédent.</span><span class="sxs-lookup"><span data-stu-id="f9a5a-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```csharp
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9a5a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9a5a-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f9a5a-123">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="f9a5a-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f9a5a-124">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f9a5a-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
