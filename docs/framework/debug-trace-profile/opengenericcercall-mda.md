---
title: openGenericCERCall (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa6ad656a5f762bf86d277d986bb087c97d7a78f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052416"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall (MDA)
L’Assistant Débogage managé `openGenericCERCall` est activé pour signaler qu’un graphe de région d’exécution limitée avec des variables de type générique au niveau de la méthode racine est en cours de traitement au moment de la compilation JIT ou de la génération d’images natives, et qu’au moins une des variables de type générique est un type de référence d’objet.  
  
## <a name="symptoms"></a>Symptômes  
 Le code de la région d’exécution limitée ne s’exécute pas quand un thread est abandonné ou quand un domaine d’application est déchargé.  
  
## <a name="cause"></a>Cause  
 Au moment de la compilation JIT, une instanciation contenant un type de référence d’objet est seulement représentative, car le code obtenu est partagé et chacune des variables de type de référence d’objet peut être n’importe quel type de référence d’objet. Ceci peut empêcher la préparation de certaines ressources préalablement à l’exécution.  
  
 En particulier, les méthodes avec des variables de type générique peuvent allouer tardivement des ressources en arrière-plan. Celles-ci sont appelées des entrées de dictionnaire génériques. Par exemple, pour l’instruction `List<T> list = new List<T>();`, où `T` est une variable de type générique, le runtime doit rechercher et éventuellement créer l’instanciation exacte au moment de l’exécution, par exemple `List<Object>, List<String>`, et ainsi de suite. Cette opération peut échouer pour différentes raisons qui échappent au contrôle du développeur, comme l’insuffisance de mémoire.  
  
 Cet Assistant Débogage managé doit être activé seulement au moment de la compilation JIT, et non pas quand il existe une instanciation exacte.  
  
 Quand cet Assistant Débogage managé est activé, les symptômes probables sont que les régions d’exécution limitée ne sont pas fonctionnelles pour les instanciations incorrectes. En fait, le runtime n’a pas tenté implémenter une région d’exécution limitée dans les circonstances qui ont provoqué l’activation de l’Assistant Débogage managé. Par conséquent, si le développeur utilise une instanciation partagée de la région d’exécution limitée, les erreurs de compilation JIT, les erreurs de chargement de types génériques ou les abandons de threads dans la région d’exécution limitée prévue ne sont pas interceptées.  
  
## <a name="resolution"></a>Résolution :  
 N’utilisez pas de variables de type générique qui sont du type de référence d’objet pour les méthodes qui peuvent contenir une région d’exécution limitée.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Sortie  
 Voici un exemple de sortie de cet Assistant Débogage managé.  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Exemple  
 Le code de la région d’exécution limitée n’est pas exécuté.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
