---
title: réentrance (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
ms.openlocfilehash: 5cbe8e843ad72785010240f3db30b1d344c80650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181762"
---
# <a name="reentrancy-mda"></a>réentrance (MDA)
L’Assistant Débogage managé (MDA) `reentrancy` est activé en cas de tentative de transition du code natif au code managé dans les cas où un basculement antérieur du code managé au mode natif n’a pas été effectué par le biais d’une transition ordonnée.  
  
## <a name="symptoms"></a>Symptômes  
 Le tas d’objets est endommagé ou d’autres erreurs graves se produisent lors de la transition du code natif au code managé.  
  
 Les threads qui basculent entre le code managé et le code natif dans les deux sens doivent effectuer une transition de façon ordonnée. Toutefois, certains points d’extensibilité de bas niveau dans le système d’exploitation, tels que le gestionnaire d’exceptions vectorisées, permettent de basculer entre le code managé et le code natif sans exécuter de transition ordonnée.  Ces basculement sont sous le contrôle du système d’exploitation, et non sous le contrôle du Commun Language Runtime (CLR).  Tout code natif qui s’exécute à l’intérieur de ces points d’extensibilité doit éviter de rappeler le code managé.  
  
## <a name="cause"></a>Cause :  
 Un point d’extensibilité de bas niveau du système d’exploitation, tel que le gestionnaire d’exceptions vectorisées, a été activé pendant l’exécution du code managé.  Le code d’application appelé par le biais de ce point d’extensibilité tente d’effectuer un rappel dans le code managé.  
  
 Ce problème est toujours dû au code d’application.  
  
## <a name="resolution"></a>Résolution  
 Recherchez dans l’arborescence des appels de procédure le thread qui a activé cet Assistant Débogage managé.  Le thread tente d’appeler illégalement du code managé.  La trace de pile doit révéler le code d’application qui utilise ce point d’extensibilité, le code du système d’exploitation qui fournit ce point d’extensibilité et le code managé qui a été interrompu par le point d’extensibilité.  
  
 Vous constaterez par exemple que l’Assistant Débogage managé a été activé lors d’une tentative d’appel de code managé à l’intérieur d’un gestionnaire d’exceptions vectorisées.  Sur la pile, vous verrez le code de gestion des exceptions du système d’exploitation et le code managé qui déclenche une exception comme <xref:System.DivideByZeroException> ou <xref:System.AccessViolationException>.  
  
 Dans cet exemple, la solution consiste à implémenter le gestionnaire d’exceptions vectorisées entièrement dans le code non managé.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Output  
 L’Assistant Débogage managé signale les tentatives de réentrance non conformes.  Examinez la pile du thread pour déterminer pourquoi cela se produit et comment résoudre le problème. Voici un exemple de sortie.  
  
```output
Additional Information: Attempting to call into managed code without
transitioning out first.  Do not attempt to run managed code inside
low-level native extensibility points. Managed Debugging Assistant
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant provoque la levée de <xref:System.AccessViolationException>.  Dans les versions de Windows qui prennent en charge la gestion des exceptions vectorisées, cela entraîne l’appel du gestionnaire d’exceptions vectorisées managé.  Si l’Assistant Débogage managé `reentrancy` est activé, il sera déclenché pendant la tentative d’appel à `MyHandler` à partir du code de prise en charge de gestion des exceptions vectorisées du système d’exploitation.  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try
        {  
            // Dispatch on null should AV.  
            Reenter r = null;
            r.Run();  
        }
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
