---
title: Un caractère '.' ou '!' de début ne peut apparaître que dans une instruction 'With'
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 4ff273d5930fe58a5bccf0f4f4c10e971d777d01
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162503"
---
# <a name="bc30157-leading--or--can-only-appear-inside-a-with-statement"></a>BC30157 : '. 'ou' ! 'de début ne peut apparaître qu’à l’intérieur d’une instruction’with'

Un point (.) ou un point d’exclamation ( !) qui ne se trouve pas à l’intérieur d’un `With` bloc se produit sans une expression à gauche. L’accès au membre ( `.` ) et l’accès au membre de dictionnaire ( `!` ) requièrent une expression spécifiant l’élément qui contient le membre. Il doit apparaître immédiatement à gauche de l’accesseur ou en tant que cible d’un `With` bloc contenant l’accès au membre.

 **ID d’erreur :** BC30157

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Assurez-vous que le `With` bloc est correctement mis en forme.

2. S’il n’y a aucun `With` bloc, ajoutez une expression à gauche de l’accesseur qui prend la valeur d’un élément défini contenant le membre.

## <a name="see-also"></a>Voir aussi

- [Caractères spéciaux dans le code](../../programming-guide/program-structure/special-characters-in-code.md)
- [With...End With (instruction)](../statements/with-end-with-statement.md)
