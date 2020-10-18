---
title: "'Is' requiert des opérandes ayant des types référence, mais cet opérande a le type valeur '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 5c9f156272cd0c3cbaeadbc0e162129f41619cc6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163348"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a>BC30020 : 'is’requiert des opérandes qui ont des types référence, mais cet opérande a le type valeur' \<typename> '

L' `Is` opérateur de comparaison détermine si deux variables objets font référence à la même instance. Cette comparaison n’est pas définie pour les types valeur.

 **ID d’erreur :** BC30020

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Utilisez l’opérateur de comparaison arithmétique approprié ou l' `Like` opérateur pour comparer deux types valeur.

## <a name="see-also"></a>Voir aussi

- [Is, opérateur](../operators/is-operator.md)
- [Like, opérateur](../operators/like-operator.md)
- [Opérateurs de comparaison](../operators/comparison-operators.md)
