---
title: 'Procédure : Déterminer le type auquel une variable objet fait référence (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626567"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Procédure : Déterminer le type auquel une variable objet fait référence (Visual Basic)

Une variable objet contient un pointeur vers des données stockées ailleurs. Le type de ces données peut changer au moment de l’exécution. À tout moment, vous pouvez utiliser la <xref:System.Type.GetTypeCode%2A> méthode pour déterminer le type au moment de l’exécution actuel ou l' [opérateur typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si le type d’exécution actuel est compatible avec un type spécifié.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Pour déterminer le type exact auquel une variable objet fait actuellement référence

1. Sur la variable objet, appelez la <xref:System.Object.GetType%2A> méthode pour récupérer un <xref:System.Type?displayProperty=nameWithType> objet.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. Sur la <xref:System.Type?displayProperty=nameWithType> classe, appelez la méthode <xref:System.Type.GetTypeCode%2A> partagée pour récupérer la <xref:System.TypeCode> valeur d’énumération du type de l’objet.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    Vous pouvez tester la <xref:System.TypeCode> valeur d’énumération en fonction des membres d’énumération intéressants `Double`, tels que.

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Pour déterminer si le type d’une variable objet est compatible avec un type spécifié

- Utilisez l' `TypeOf` opérateur en association avec l' [opérateur is](../../../../visual-basic/language-reference/operators/is-operator.md) pour tester l’objet avec un `TypeOf`... `Is` expression.

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`... l’expression `True` retourne si le type au moment de l’exécution de l’objet est compatible avec le type spécifié. `Is`

    Le critère de compatibilité varie selon que le type spécifié est une classe, une structure ou une interface. En général, les types sont compatibles si l’objet est du même type que, hérite de ou implémente le type spécifié. Pour plus d’informations, consultez [opérateur typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).

## <a name="compiling-the-code"></a>Compilation du code

Notez que le type spécifié ne peut pas être une variable ou une expression. Il doit s’agir du nom d’un type défini, tel qu’une classe, une structure ou une interface. Cela comprend les types intrinsèques `Integer` tels `String`que et.

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)
