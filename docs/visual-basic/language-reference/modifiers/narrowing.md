---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: f7724053e3732c909523e4e2d3b65bb1918c29d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362357"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Indique qu’un opérateur de conversion ( `CType` ) convertit une classe ou une structure en un type qui peut ne pas pouvoir contenir certaines des valeurs possibles de la classe ou de la structure d’origine.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Conversion avec le mot clé restrictive  
 La procédure de conversion doit spécifier `Public Shared` en plus de `Narrowing` .  
  
 Les conversions restrictives ne réussissent pas toujours au moment de l’exécution et peuvent échouer ou entraîner une perte de données. Exemples : `Long` à `Integer` , `String` à `Date` et un type de base à un type dérivé. Cette dernière conversion est restrictive, car le type de base ne peut pas contenir tous les membres du type dérivé et, par conséquent, n’est pas une instance du type dérivé.  
  
 Si `Option Strict` est `On` , le code de consommation doit utiliser `CType` pour toutes les conversions restrictives.  
  
 Le `Narrowing` mot clé peut être utilisé dans ce contexte :  
  
 [Operator Statement](../statements/operator-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Operator Statement](../statements/operator-statement.md)
- [Widening](widening.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Comment : définir un opérateur](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType Function](../functions/ctype-function.md)
- [Option Strict Statement](../statements/option-strict-statement.md)
