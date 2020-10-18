---
title: La classe déléguée '<classname>' n'a pas de méthode Invoke, c'est pourquoi une expression de ce type ne peut pas être la cible d'un appel de méthode
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 4e0fc61c7356008755134f670fa1fab0165cfd48
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162789"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>BC30220 : la classe déléguée' \<classname> 'n’a pas de méthode Invoke. par conséquent, une expression de ce type ne peut pas être la cible d’un appel de méthode

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
