---
title: Sécurité et conditions de concurrence
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186779"
---
# <a name="security-and-race-conditions"></a>Sécurité et conditions de concurrence
Un autre sujet de préoccupation est le potentiel de failles de sécurité exploitées par les conditions de course. Il y a plusieurs façons de cela. Les sous-produits qui suivent décrivent quelques-uns des principaux pièges que le développeur doit éviter.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Conditions de course dans la méthode disposer  
 Si la méthode **dispose d’une** classe (pour plus d’informations, voir [Collection d’ordures](../../../docs/standard/garbage-collection/index.md)) n’est pas synchronisée, il est possible que le code de nettoyage à l’intérieur **de Dispose** puisse être exécuté plus d’une fois, comme le montre l’exemple suivant.  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()
{  
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 Parce que cette implémentation **Dispose** n’est pas synchronisée, il est possible `Cleanup` pour être appelé par un premier thread, puis un deuxième thread avant `_myObj` est configuré à **null.** La question de savoir s’il `Cleanup` s’agit d’une préoccupation de sécurité dépend de ce qui se passe lorsque le code s’exécute. Un problème majeur avec les implémentations **de disposition** non synchronisées concerne l’utilisation de poignées de ressources telles que les fichiers. Une mauvaise élimination peut entraîner l’utilisation d’une mauvaise poignée, ce qui entraîne souvent des failles de sécurité.  
  
## <a name="race-conditions-in-constructors"></a>Conditions de course dans les constructeurs  
 Dans certaines applications, il pourrait être possible pour d’autres threads d’accéder aux membres de la classe avant que leurs constructeurs de classe ont complètement exécuté. Vous devez passer en revue tous les constructeurs de classe pour vous assurer qu’il n’y a pas de problèmes de sécurité si cela devait se produire, ou synchroniser les threads si nécessaire.  
  
## <a name="race-conditions-with-cached-objects"></a>Conditions de course avec objets caches  
 Le code qui cache les informations de sécurité ou utilise l’opération de sécurité [d’accès](../../../docs/framework/misc/using-the-assert-method.md) au code Assert peut également être vulnérable aux conditions de course si d’autres parties de la classe ne sont pas synchronisées de manière appropriée, comme le montre l’exemple suivant.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()
{  
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
    {  
        DoSomethingTrusted();  
    }  
    else
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 S’il y `DoOtherWork` a d’autres chemins à qui peut être appelé à partir d’un autre thread avec le même objet, un appelant non fiable peut glisser au-delà d’une demande.  
  
 Si votre code cache des informations de sécurité, assurez-vous de les examiner pour cette vulnérabilité.  
  
## <a name="race-conditions-in-finalizers"></a>Conditions de course dans finalizers  
 Les conditions de course peuvent également se produire dans un objet qui fait référence à une ressource statique ou non mentée qu’il libère ensuite dans son finalisateur. Si plusieurs objets partagent une ressource qui est manipulée dans le finalisateur d’une classe, les objets doivent synchroniser tout accès à cette ressource.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)
