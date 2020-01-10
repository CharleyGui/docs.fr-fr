---
title: 'Comment : déterminer le type désigné par une variable objet'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: b3778a170759f685db78e7dcde219138196f9eca
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344197"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Comment : déterminer le type désigné par une variable objet (Visual Basic)

Une variable objet contient un pointeur vers des données stockées ailleurs. Le type de ces données peut changer au moment de l’exécution. À tout moment, vous pouvez utiliser la méthode <xref:System.Type.GetTypeCode%2A> pour déterminer le type au moment de l’exécution actuel ou l' [opérateur typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si le type d’exécution actuel est compatible avec un type spécifié.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Pour déterminer le type exact auquel une variable objet fait actuellement référence

1. Sur la variable objet, appelez la méthode <xref:System.Object.GetType%2A> pour récupérer un objet <xref:System.Type?displayProperty=nameWithType>.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. Sur la classe <xref:System.Type?displayProperty=nameWithType>, appelez la méthode partagée <xref:System.Type.GetTypeCode%2A> pour récupérer la valeur d’énumération <xref:System.TypeCode> pour le type de l’objet.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    Vous pouvez tester la valeur d’énumération <xref:System.TypeCode> sur les membres d’énumération intéressants, tels que `Double`.

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Pour déterminer si le type d’une variable objet est compatible avec un type spécifié

- Utilisez l’opérateur `TypeOf` en association avec l' [opérateur is](../../../../visual-basic/language-reference/operators/is-operator.md) pour tester l’objet avec une expression `TypeOf`...`Is`.

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    L’expression `TypeOf`...`Is` retourne `True` si le type au moment de l’exécution de l’objet est compatible avec le type spécifié.

    Le critère de compatibilité varie selon que le type spécifié est une classe, une structure ou une interface. En général, les types sont compatibles si l’objet est du même type que, hérite de ou implémente le type spécifié. Pour plus d’informations, consultez [opérateur typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).

## <a name="compile-the-code"></a>Compiler le code

Notez que le type spécifié ne peut pas être une variable ou une expression. Il doit s’agir du nom d’un type défini, tel qu’une classe, une structure ou une interface. Cela comprend des types intrinsèques tels que `Integer` et `String`.

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
