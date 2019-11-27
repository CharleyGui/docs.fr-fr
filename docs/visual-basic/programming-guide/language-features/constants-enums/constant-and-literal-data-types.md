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
ms.openlocfilehash: 8ebecddfab0724023c269e92c1fc5534f096bf1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333732"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Constantes et types de données littérales (Visual Basic)
Un littéral est une valeur qui est exprimée comme étant elle-même plutôt que comme une valeur de variable ou le résultat d’une expression, tel que le numéro 3 ou la chaîne « Hello ». Une constante est un nom explicite qui prend la place d’un littéral et conserve cette même valeur dans tout le programme, par opposition à une variable, dont la valeur peut changer.  
  
 Quand [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) est `Off` et [option strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) est `On`, vous devez déclarer explicitement toutes les constantes avec un type de données. Dans l’exemple suivant, le type de données de `MyByte` est déclaré explicitement comme type de données `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 Lorsque `Option Infer` est `On` ou `Option Strict` est `Off`, vous pouvez déclarer une constante sans spécifier de type de données avec une clause `As`. Le compilateur détermine le type de la constante à partir du type de l’expression. Un littéral d’entier numérique est casté par défaut en type de données `Integer`. Le type de données par défaut pour les nombres à virgule flottante est `Double`, et les mots clés `True` et `False` spécifier une constante `Boolean`.  
  
## <a name="literals-and-type-coercion"></a>Littéraux et forçage de type  
 Dans certains cas, vous souhaiterez peut-être forcer un littéral à un type de données particulier ; par exemple, lors de l’assignation d’une valeur littérale intégrale particulièrement importante à une variable de type `Decimal`. L’exemple suivant génère une erreur :  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 L’erreur résulte de la représentation du littéral. Le type de données `Decimal` peut contenir une valeur de cette taille, mais le littéral est implicitement représenté sous la forme d’un `Long`, ce qui ne peut pas.  
  
 Vous pouvez forcer un littéral à un type de données particulier de deux manières : en y ajoutant un caractère de type ou en le plaçant dans des caractères englobants. Un caractère de type ou des caractères englobants doit immédiatement précéder et/ou suivre le littéral, sans aucun espace ou caractère intermédiaire.  
  
 Pour que l’exemple précédent fonctionne, vous pouvez ajouter le caractère de type `D` au littéral, ce qui a pour effet de le représenter comme `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 L’exemple suivant illustre l’utilisation correcte des caractères de type et des caractères englobants :  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 Le tableau suivant présente les caractères englobants et les caractères de type disponibles dans Visual Basic.  
  
|Type de données|Caractère englobant|Caractère de type ajouté|  
|---|---|---|  
|`Boolean`|(aucun)|(aucun)|  
|`Byte`|(aucun)|(aucun)|  
|`Char`|«|C|  
|`Date`|#|(aucun)|  
|`Decimal`|(aucun)|D ou @|  
|`Double`|(aucun)|R ou #|  
|`Integer`|(aucun)|I ou%|  
|`Long`|(aucun)|L ou &|  
|`Short`|(aucun)|T|  
|`Single`|(aucun)|F ou !|  
|`String`|«|(aucun)|  
  
## <a name="see-also"></a>Voir aussi

- [Constantes définies par l’utilisateur](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [Guide pratique : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Option Explicit (instruction)](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Types de données](../../../../visual-basic/language-reference/data-types/index.md)
- [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
