---
title: Instruction non valide dans une méthode ou une expression lambda multiligne
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: cef992c3eaa2b82bbf5e8993f9fccd64ae388c95
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159675"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a>BC30024 : l’instruction n’est pas valide dans une méthode ou une expression lambda multiligne

L’instruction n’est pas valide dans `Sub` une `Function` procédure de propriété,, `Get` ou `Set` . Certaines instructions peuvent être placées au niveau du module ou de la classe. D’autres, telles que `Option Strict` , doivent se trouver au niveau de l’espace de noms et précéder toutes les autres déclarations.

 **ID d’erreur :** BC30024

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez l’instruction de la procédure.

## <a name="see-also"></a>Voir aussi

- [Sub (instruction)](../statements/sub-statement.md)
- [Function (instruction)](../statements/function-statement.md)
- [Get, instruction](../statements/get-statement.md)
- [Instruction Set](../statements/set-statement.md)
