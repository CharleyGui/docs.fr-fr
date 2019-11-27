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
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351477"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Indique qu’un opérateur de conversion (`CType`) convertit une classe ou une structure en un type qui peut ne pas pouvoir contenir certaines des valeurs possibles de la classe ou de la structure d’origine.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Conversion avec le mot clé restrictive  
 La procédure de conversion doit spécifier `Public Shared` en plus de `Narrowing`.  
  
 Les conversions restrictives ne réussissent pas toujours au moment de l’exécution et peuvent échouer ou entraîner une perte de données. Les exemples sont `Long` pour `Integer`, `String` pour `Date`et un type de base vers un type dérivé. Cette dernière conversion est restrictive, car le type de base ne peut pas contenir tous les membres du type dérivé et, par conséquent, n’est pas une instance du type dérivé.  
  
 Si `Option Strict` est `On`, le code de consommation doit utiliser `CType` pour toutes les conversions restrictives.  
  
 Le mot clé `Narrowing` peut être utilisé dans ce contexte :  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Guide pratique : définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
