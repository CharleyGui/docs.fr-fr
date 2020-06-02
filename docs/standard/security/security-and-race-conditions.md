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
ms.openlocfilehash: 715bf240a5f7f44ba3f914ad6788631074aa41b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291017"
---
# <a name="security-and-race-conditions"></a>Sécurité et conditions de concurrence
Une autre zone de préoccupation est le potentiel pour les brèches de sécurité exploitées par des conditions de concurrence. Cela peut se produire de plusieurs façons. Les sous-rubriques qui suivent décrivent certains des pièges majeurs que le développeur doit éviter.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Conditions de concurrence dans la méthode dispose  
 Si la méthode **dispose** d’une classe (pour plus d’informations, consultez [garbage collection](../garbage-collection/index.md)) n’est pas synchronisée, il est possible que le code de nettoyage à l’intérieur de **dispose** puisse être exécuté plusieurs fois, comme indiqué dans l’exemple suivant.  
  
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
  
 Comme cette implémentation de **dispose** n’est pas synchronisée, il est possible que soit `Cleanup` appelé par un premier thread, puis qu’un deuxième thread avant `_myObj` ait la valeur **null**. Le fait qu’il s’agisse d’un problème de sécurité dépend de ce qui se passe lorsque le `Cleanup` code s’exécute. Un problème majeur avec les implémentations de **suppression** non synchronisées implique l’utilisation de handles de ressources tels que des fichiers. Une suppression incorrecte peut entraîner l’utilisation d’un mauvais descripteur, ce qui entraîne souvent des failles de sécurité.  
  
## <a name="race-conditions-in-constructors"></a>Conditions de concurrence dans les constructeurs  
 Dans certaines applications, il est possible que d’autres threads accèdent à des membres de classe avant l’exécution complète de leurs constructeurs de classe. Vous devez examiner tous les constructeurs de classe pour vous assurer qu’il n’existe aucun problème de sécurité si cela se produit, ou synchroniser les threads si nécessaire.  
  
## <a name="race-conditions-with-cached-objects"></a>Conditions de concurrence critique avec des objets mis en cache  
 Le code qui met en cache des informations de sécurité ou utilise l’opération d' [assertion](../../framework/misc/using-the-assert-method.md) de sécurité d’accès du code peut également être vulnérable aux conditions de concurrence critique si d’autres parties de la classe ne sont pas correctement synchronisées, comme illustré dans l’exemple suivant.  
  
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
  
 S’il existe d’autres chemins vers `DoOtherWork` qui peuvent être appelés à partir d’un autre thread avec le même objet, un appelant non fiable peut ignorer une demande.  
  
 Si votre code met en cache les informations de sécurité, assurez-vous que vous l’avez révisée pour cette vulnérabilité.  
  
## <a name="race-conditions-in-finalizers"></a>Conditions de concurrence dans les finaliseurs  
 Des conditions de concurrence critique peuvent également se produire dans un objet qui fait référence à une ressource statique ou non managée qu’il libère ensuite dans son finaliseur. Si plusieurs objets partagent une ressource qui est manipulée dans le finaliseur d’une classe, les objets doivent synchroniser tous les accès à cette ressource.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](secure-coding-guidelines.md)
