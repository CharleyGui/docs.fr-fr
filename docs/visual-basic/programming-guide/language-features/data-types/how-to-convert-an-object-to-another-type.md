---
title: 'Comment : convertir un objet en un autre type'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 19708d03b0514f4572c2baa53e05781e5949766b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350071"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Comment : convertir un objet en un autre type dans Visual Basic
Vous convertissez une variable `Object` en un autre type de données à l’aide d’un mot clé de conversion tel que [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant convertit une variable `Object` en `Integer` et un `String`.  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Si vous savez que le contenu d’une variable de `Object` est d’un type de données particulier, il est préférable de convertir la variable en ce type de données. Si vous continuez à utiliser la variable `Object`, vous devez effectuer une *conversion boxing* et *unboxing* (pour un type valeur) ou une *liaison tardive* (pour un type référence). Ces opérations prennent toutes une durée d’exécution supplémentaire et ralentissent vos performances.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- une référence à l'espace de noms <xref:System?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Object>
- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversion entre des chaînes et d’autres types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Conversions de tableau](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Types de données](../../../../visual-basic/language-reference/data-types/index.md)
- [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
