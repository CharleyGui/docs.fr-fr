---
title: 'La déclaration d’opérateur doit être l’une des suivantes : +,-, *,-,-, ^, &amp; , like, mod, and, or, Xor, not,  <<,  >>, =,  <>, <, <=, >, >=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 3fb2cf392611e5ca83818e3bf173513be031085d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409332"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>La déclaration d’opérateur doit être l’une des suivantes : +,-, *, \, /, ^, &amp; , like, mod, and, or, Xor, not, \<\<, >>...
Vous pouvez déclarer uniquement un opérateur éligible pour la surcharge. Le tableau suivant répertorie les opérateurs que vous pouvez déclarer.  
  
|Type|Opérateurs|  
|----------|---------------|  
|Unaire|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binaire|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversion (unaire)|`CType`|  
  
 Notez que l’opérateur `=` dans la liste binaire est l’opérateur de comparaison, et non l’opérateur d’assignation.  
  
 **ID d’erreur :** BC33000  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Sélectionnez un opérateur dans le jeu d’opérateurs surchargeables.  
  
2. Si vous avez besoin des fonctionnalités de surcharge d’un opérateur que vous ne pouvez pas surcharger directement, créez une procédure `Function` qui accepte les paramètres appropriés et retourne la valeur adéquate.  
  
## <a name="see-also"></a>Voir aussi

- [Operator Statement](../statements/operator-statement.md)
- [Procédures d'opérateur](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Comment : définir un opérateur](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function (instruction)](../statements/function-statement.md)
