---
title: 'Comment : créer une Union C-C++ à l’aide d’attributs'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: ebab0ad947f776932f9379af3969e369eeec1941
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400679"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Guide pratique : créer une union C/C++ à l’aide d’attributs (Visual Basic)

Vous pouvez personnaliser la disposition des structs en mémoire à l’aide d’attributs. Par exemple, vous pouvez créer ce qu’on appelle une union en C/C++ à l’aide des attributs `StructLayout(LayoutKind.Explicit)` et `FieldOffset`.

## <a name="example"></a>Exemple

Dans ce segment de code, tous les champs de `TestUnion` débutent au même emplacement en mémoire.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a>Exemple

Voici un autre exemple où les champs débutent à différents emplacements définis explicitement.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

Les deux champs entiers, `i1` et `i2`, partagent leurs emplacements de mémoire avec `lg`. Ce type de contrôle sur la disposition des structs est utile quand vous utilisez des appels de code non managé.

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Guide de programmation Visual Basic](../../index.md)
- [Attributs](../../../../standard/attributes/index.md)
- [Réflexion (Visual Basic)](../reflection.md)
- [Attributs (Visual Basic)](../../../language-reference/attributes.md)
- [Créer des attributs personnalisés (Visual Basic)](creating-custom-attributes.md)
- [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](accessing-attributes-by-using-reflection.md)
