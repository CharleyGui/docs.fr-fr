---
title: Constantes et types de données littérales
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: b94259326b42104db05d9fc5bb09f686075d0759
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414529"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Constantes et types de données littérales (Visual Basic)
Un littéral est une valeur qui est exprimée comme étant elle-même plutôt que comme une valeur de variable ou le résultat d’une expression, tel que le numéro 3 ou la chaîne « Hello ». Une constante est un nom explicite qui prend la place d’un littéral et conserve cette même valeur dans tout le programme, par opposition à une variable, dont la valeur peut changer.  
  
 Quand [Option Infer](../../../language-reference/statements/option-infer-statement.md) est `Off` et [option strict](../../../language-reference/statements/option-strict-statement.md) est `On` , vous devez déclarer toutes les constantes explicitement avec un type de données. Dans l’exemple suivant, le type de données de `MyByte` est déclaré explicitement comme type de données `Byte` :  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 Lorsque `Option Infer` est `On` ou `Option Strict` a `Off` la clause, vous pouvez déclarer une constante sans spécifier de type de données avec une `As` clause. Le compilateur détermine le type de la constante à partir du type de l’expression. Un littéral d’entier numérique est converti par défaut en `Integer` type de données. Le type de données par défaut pour les nombres à virgule flottante est `Double` , et les mots clés `True` et `False` spécifient une `Boolean` constante.  
  
## <a name="literals-and-type-coercion"></a>Littéraux et forçage de type  
 Dans certains cas, vous souhaiterez peut-être forcer un littéral à un type de données particulier ; par exemple, lors de l’assignation d’une valeur littérale intégrale particulièrement importante à une variable de type `Decimal` . L’exemple suivant génère une erreur :  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 L’erreur résulte de la représentation du littéral. Le `Decimal` type de données peut contenir une valeur de cette taille, mais le littéral est implicitement représenté sous la forme d’un `Long` , ce qui ne peut pas.  
  
 Vous pouvez forcer un littéral à un type de données particulier de deux manières : en y ajoutant un caractère de type ou en le plaçant dans des caractères englobants. Un caractère de type ou des caractères englobants doit immédiatement précéder et/ou suivre le littéral, sans aucun espace ou caractère intermédiaire.  
  
 Pour que l’exemple précédent fonctionne, vous pouvez ajouter le `D` caractère de type au littéral, ce qui a pour effet de le représenter en tant que `Decimal` :  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 L’exemple suivant illustre l’utilisation correcte des caractères de type et des caractères englobants :  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 Le tableau suivant présente les caractères englobants et les caractères de type disponibles dans Visual Basic.  
  
|Type de données|Caractère englobant|Caractère de type ajouté|  
|---|---|---|  
|`Boolean`|(aucun)|(aucun)|  
|`Byte`|(aucun)|(aucun)|  
|`Char`|"|C|  
|`Date`|#|(aucun)|  
|`Decimal`|(aucun)|D ou @|  
|`Double`|(aucun)|R ou #|  
|`Integer`|(aucun)|I ou%|  
|`Long`|(aucun)|L ou &|  
|`Short`|(aucun)|S|  
|`Single`|(aucun)|F ou !|  
|`String`|"|(aucun)|  
  
## <a name="see-also"></a>Voir aussi

- [Constantes définies par l'utilisateur](user-defined-constants.md)
- [Comment : déclarer une constante](how-to-declare-a-constant.md)
- [Vue d'ensemble des constantes](constants-overview.md)
- [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)
- [Option Explicit (instruction)](../../../language-reference/statements/option-explicit-statement.md)
- [Vue d'ensemble des énumérations](enumerations-overview.md)
- [How to: Declare an, énumération](how-to-declare-enumerations.md)
- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Types de données](../../../language-reference/data-types/index.md)
- [Constantes et énumérations](../../../language-reference/constants-and-enumerations.md)
