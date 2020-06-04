---
title: Les expressions lambda ne sont pas valides dans la première expression d’une instruction ’Select Case’
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 08f7cd9dd95a10cad0df6539ba43122495347bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397361"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>Les expressions lambda ne sont pas valides dans la première expression d’une instruction ’Select Case’
Vous ne pouvez pas utiliser une expression lambda pour l’expression de test dans une `Select Case` instruction. Les définitions d’expression lambda retournent des fonctions, et l’expression de test d’une `Select Case` instruction doit être un type de données élémentaire.  
  
 Le code suivant génère cette erreur :  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **ID d’erreur :** BC36635  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Examinez votre code pour déterminer si une construction conditionnelle différente, comme une instruction `If...Then...Else` , répond à vos besoins.  
  
- Vous avez peut-être prévu d’appeler la fonction, comme illustré dans le code suivant :  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Voir aussi

- [Expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [If...Then...Else (instruction)](../statements/if-then-else-statement.md)
- [Select...Case (instruction)](../statements/select-case-statement.md)
