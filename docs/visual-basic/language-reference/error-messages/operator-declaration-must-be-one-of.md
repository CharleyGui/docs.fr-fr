---
title: 'La déclaration d’opérateur doit être l’une des suivantes : +,-, *,-,-, ^, &amp; , like, mod, and, or, Xor, not,  <<,  >>, =,  <>, <, <=, >, >=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: a94e62e33427987a302a6244b2b8ce8d295e4f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159896"
---
# <a name="bc33000-operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>BC33000 : la déclaration d’opérateur doit être l’une des suivantes : +,-, *, \, /, ^, &amp; , like, mod, and, or, Xor, not, \<\<, >>...

Vous pouvez déclarer uniquement un opérateur éligible pour la surcharge. Le tableau suivant répertorie les opérateurs que vous pouvez déclarer.

|Type|Opérateurs|
|----------|---------------|
|Unaire|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|
|Conversion (unaire)|`CType`|

 Notez que l’opérateur `=` dans la liste binaire est l’opérateur de comparaison, et non l’opérateur d’assignation.

 **ID d’erreur :** BC33000

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Sélectionnez un opérateur dans le jeu d’opérateurs surchargeables.

- Si vous avez besoin des fonctionnalités de surcharge d’un opérateur que vous ne pouvez pas surcharger directement, créez une procédure `Function` qui accepte les paramètres appropriés et retourne la valeur adéquate.

## <a name="see-also"></a>Voir aussi

- [Operator Statement](../statements/operator-statement.md)
- [Procédures d'opérateur](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Comment : définir un opérateur](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function (instruction)](../statements/function-statement.md)
