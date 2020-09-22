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
ms.openlocfilehash: 14e0b026f4fc3b0bf202ea643a28d6f1a7df2b7c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867646"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)

Indique qu’un opérateur de conversion ( `CType` ) convertit une classe ou une structure en un type qui peut contenir toutes les valeurs possibles de la classe ou de la structure d’origine.  
  
## <a name="converting-with-the-widening-keyword"></a>Conversion avec le mot clé Widening  

 La procédure de conversion doit spécifier `Public Shared` en plus de `Widening` .  
  
 Les conversions étendues fonctionnent toujours au moment de l’exécution et n’entraînent jamais de perte de données. Les exemples sont `Single` pour `Double` , `Char` à `String` et un type dérivé dans son type de base. Cette dernière conversion est étendue car le type dérivé contient tous les membres du type de base et est donc une instance du type de base.  
  
 Le code de consommation n’a pas besoin d’utiliser `CType` pour les conversions étendues, même si `Option Strict` est `On` .  
  
 Le `Widening` mot clé peut être utilisé dans ce contexte :  
  
 [Operator Statement](../statements/operator-statement.md)  
  
 Pour obtenir des exemples de définitions d’opérateurs de conversion étendues et restrictives, consultez [Comment : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Voir aussi

- [Operator Statement](../statements/operator-statement.md)
- [Narrowing](narrowing.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Comment : définir un opérateur](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType Function](../functions/ctype-function.md)
- [Option Strict Statement](../statements/option-strict-statement.md)
- [Guide pratique : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
