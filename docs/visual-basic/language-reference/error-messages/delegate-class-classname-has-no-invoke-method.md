---
title: La classe déléguée '<classname>' n'a pas de méthode Invoke, c'est pourquoi une expression de ce type ne peut pas être la cible d'un appel de méthode
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: e6ad06262806088347c94b3040b743618a3b3695
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874495"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>La classe déléguée '\<classname>' n'a pas de méthode Invoke, c'est pourquoi une expression de ce type ne peut pas être la cible d'un appel de méthode

Un appel à `Invoke` via un délégué a échoué, car `Invoke` n’est pas implémenté sur la classe déléguée.  
  
 **ID d’erreur :** BC30220  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous qu’une instance de la classe déléguée a été créée avec une `Dim` instruction et qu’une procédure a été assignée à l’instance de délégué avec l' `AddressOf` opérateur.  
  
2. Recherchez le code qui implémente la classe déléguée et assurez-vous qu’il implémente la `Invoke` procédure.  
  
## <a name="see-also"></a>Voir aussi

- [Délégués](../../programming-guide/language-features/delegates/index.md)
- [Delegate, instruction](../statements/delegate-statement.md)
- [AddressOf, opérateur](../operators/addressof-operator.md)
- [Dim (instruction)](../statements/dim-statement.md)
