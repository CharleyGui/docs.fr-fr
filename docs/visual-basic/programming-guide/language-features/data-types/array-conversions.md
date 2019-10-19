---
title: Conversion des tableaux (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 475f3f5357f7c989a30ca9e6c5d32b8cc989436f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581862"
---
# <a name="array-conversions-visual-basic"></a>Conversion des tableaux (Visual Basic)
Vous pouvez convertir un type tableau en un type de tableau différent, à condition que vous respectiez les conditions suivantes :  
  
- **Même rang.** Les rangs des deux tableaux doivent être identiques, autrement dit, ils doivent avoir le même nombre de dimensions. Toutefois, les longueurs des dimensions respectives ne doivent pas nécessairement être identiques.  
  
- **Type de données de l’élément.** Les types de données des éléments des deux tableaux doivent être des types référence. Vous ne pouvez pas convertir un tableau `Integer` en tableau `Long`, ni même en tableau `Object`, car au moins un type valeur est impliqué. Pour plus d'informations, consultez [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
- **Convertibilité.** Une conversion, étendue ou restrictive, doit être possible entre les types d’éléments des deux tableaux. Un exemple qui ne respecte pas cette exigence est une tentative de conversion entre un tableau `String` et un tableau d’une classe dérivée de <xref:System.Attribute?displayProperty=nameWithType>. Ces deux types n’ont rien en commun et aucune conversion n’existe entre eux.  
  
 La conversion d’un type tableau en un autre est étendue ou restrictive, selon que la conversion des éléments respectifs est étendue ou restrictive. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Conversion en tableau d’objets  
 Lorsque vous déclarez un tableau de `Object` sans l’initialiser, son type d’élément est `Object` tant qu’il n’est pas initialisé. Quand vous le définissez sur un tableau d’une classe spécifique, il prend le type de cette classe. Toutefois, son type sous-jacent est toujours `Object`, et vous pouvez le définir par la suite sur un autre tableau d’une classe non liée. Étant donné que toutes les classes dérivent de `Object`, vous pouvez remplacer le type d’élément du tableau de toute classe par une autre classe.  
  
 Dans l’exemple suivant, aucune conversion n’existe entre les types `student` et `String`, mais les deux dérivent de `Object`, donc toutes les affectations sont valides.  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>Type sous-jacent d’un tableau  
 Si vous déclarez à l’origine un tableau avec une classe spécifique, son type d’élément sous-jacent est cette classe. Si vous la définissez par la suite sur un tableau d’une autre classe, il doit y avoir une conversion entre les deux classes.  
  
 Dans l’exemple suivant, `students` est un tableau de `student`. Étant donné qu’il n’existe aucune conversion entre `String` et `student`, la dernière instruction échoue.  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversion entre des chaînes et d’autres types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Comment : convertir un objet en un autre type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Types de données](../../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
