---
title: "'<typename>' est un type délégué"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: dcb52188c53b38ac14de0002b5212bb33c9f7203
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161775"
---
# <a name="bc32008-typename-is-a-delegate-type"></a>BC32008 : ' \<typename> 'est un type délégué

' \<typename> 'est un type délégué. La construction de délégué autorise uniquement une seule expression AddressOf comme liste d’arguments. Souvent, une expression AddressOf peut être utilisée à la place d’une construction de délégué.

 Une `New` clause qui crée une instance d’une classe déléguée fournit une liste d’arguments non valide au constructeur délégué.

 Vous ne pouvez fournir qu’une seule `AddressOf` expression lors de la création d’une instance de délégué.

 Cette erreur peut se produire si vous ne transmettez pas d’arguments au constructeur délégué, si vous transmettez plusieurs arguments ou si vous transmettez un argument unique qui n’est pas une `AddressOf` expression valide.

 **ID d’erreur :** BC32008

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Utilisez une `AddressOf` expression unique dans la liste d’arguments pour la classe déléguée dans la `New` clause.

## <a name="see-also"></a>Voir aussi

- [Nouvel opérateur](../operators/new-operator.md)
- [AddressOf, opérateur](../operators/addressof-operator.md)
- [Délégués](../../programming-guide/language-features/delegates/index.md)
- [Comment : appeler une méthode déléguée](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
