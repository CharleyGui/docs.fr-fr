---
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 1c9aa78549ca6e41c9fe54c12e0aaec8e7cc30cb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347830"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
Indique qu’un opérateur de conversion (`CType`) convertit une classe ou une structure en un type qui peut contenir toutes les valeurs possibles de la classe ou de la structure d’origine.  
  
## <a name="converting-with-the-widening-keyword"></a>Conversion avec le mot clé Widening  
 La procédure de conversion doit spécifier `Public Shared` en plus de `Widening`.  
  
 Les conversions étendues fonctionnent toujours au moment de l’exécution et n’entraînent jamais de perte de données. Les exemples sont `Single` pour `Double`, `Char` pour `String`et un type dérivé dans son type de base. Cette dernière conversion est étendue car le type dérivé contient tous les membres du type de base et est donc une instance du type de base.  
  
 Le code de consommation n’a pas besoin d’utiliser `CType` pour les conversions étendues, même si `Option Strict` est `On`.  
  
 Le mot clé `Widening` peut être utilisé dans ce contexte :  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Pour obtenir des exemples de définitions d’opérateurs de conversion étendues et restrictives, consultez [Comment : définir un opérateur de conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Voir aussi

- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Guide pratique : définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Guide pratique : définir un opérateur de conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
