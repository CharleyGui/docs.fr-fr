---
title: Assistant Débogage managé jitCompilationStart (MDA)
description: L’Assistant Débogage managé jitCompilationStart (MDA) signale que le compilateur juste-à-temps (JIT) commence la compilation d’une fonction .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 13e20c1a940b7bfa777245ba35f3cc1b003d15b2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325536"
---
# <a name="jitcompilationstart-mda"></a>Assistant Débogage managé jitCompilationStart

L’Assistant Débogage managé `jitCompilationStart` est activé pour signaler le moment où le compilateur juste-à-temps (JIT, Just-In-Time) commence à compiler une fonction.  
  
## <a name="symptoms"></a>Symptômes  
 La taille de la plage de travail augmente pour un programme qui est déjà au format d’image native, car mscorjit.dll est chargé dans le processus.  
  
## <a name="cause"></a>Cause  
Tous les assemblys dont dépend le programme n’ont pas été générés au format natif ou un assembly n’est pas inscrit correctement.  

## <a name="resolution"></a>Résolution  
 L’activation de cet Assistant Débogage managé vous permet d’identifier la fonction qui est compilée juste-à-temps. Assurez-vous que l’assembly qui contient la fonction est généré au format natif et correctement inscrit.
  
## <a name="effect-on-the-runtime"></a>Effet sur le Runtime  
 Cet Assistant Débogage managé enregistre un message juste avant qu’une méthode ne soit compilée juste-à-temps, de sorte que son activation a un impact significatif sur les performances. Si une méthode est Inline, cet Assistant Débogage managé ne génère pas de message distinct.  
  
## <a name="output"></a>Sortie  
 L’exemple de code suivant illustre une sortie. Dans ce cas, la sortie indique que, dans le test de l’assembly, la méthode « m » de la classe « ns2.CO » a été compilée juste-à-temps.  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Configuration  
 Le fichier de configuration suivant présente divers filtres qui peuvent être utilisés pour filtrer les méthodes signalées quand elles sont d’abord compilées juste-à-temps. Vous pouvez spécifier que toutes les méthodes soient signalées en définissant la valeur de l’attribut Name sur \* .  
  
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
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant doit normalement être utilisé avec le fichier de configuration précédent.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
