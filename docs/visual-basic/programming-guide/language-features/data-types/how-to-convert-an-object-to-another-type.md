---
title: 'Procédure : Convertir un objet en un autre type'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: cdb78bc66867ce27076d7b7e42de6a2880cb3a8c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393959"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Comment : convertir un objet en un autre type dans Visual Basic
Vous convertissez une `Object` variable en un autre type de données à l’aide d’un mot clé de conversion tel que [CType Function](../../../language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant convertit une `Object` variable en `Integer` et `String` .  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Si vous savez que le contenu d’une `Object` variable est d’un type de données particulier, il est préférable de convertir la variable en ce type de données. Si vous continuez à utiliser la `Object` variable, vous devez effectuer une *conversion boxing* et *unboxing* (pour un type valeur) ou une *liaison tardive* (pour un type référence). Ces opérations prennent toutes une durée d’exécution supplémentaire et ralentissent vos performances.  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite :  
  
- une référence à l'espace de noms <xref:System?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Object>
- [Conversions de type en Visual Basic](type-conversions.md)
- [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](implicit-and-explicit-conversions.md)
- [Conversions entre des chaînes et d’autres types](conversions-between-strings-and-other-types.md)
- [Conversions de tableau](array-conversions.md)
- [Structures](structures.md)
- [Types de données](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
