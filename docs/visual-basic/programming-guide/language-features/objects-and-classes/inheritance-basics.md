---
title: Éléments fondamentaux de l'héritage (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 8a75b75ef9acb4c89f4c7d05f1410d4ca70e680b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582748"
---
# <a name="inheritance-basics-visual-basic"></a>Éléments fondamentaux de l'héritage (Visual Basic)

L’instruction `Inherits` est utilisée pour déclarer une nouvelle classe, appelée *classe dérivée*, basée sur une classe existante, appelée classe de *base*. Les classes dérivées héritent des propriétés, des méthodes, des événements, des champs et des constantes définies dans la classe de base, et peuvent étendre celles-ci. La section suivante décrit certaines des règles d’héritage et les modificateurs que vous pouvez utiliser pour modifier la façon dont les classes héritent ou sont héritées :

- Par défaut, toutes les classes peuvent être héritées, sauf si elles sont marquées avec le mot clé `NotInheritable`. Les classes peuvent hériter d’autres classes de votre projet ou de classes dans d’autres assemblys référencés par votre projet.

- Contrairement aux langages qui autorisent l’héritage multiple, Visual Basic n’autorise que l’héritage unique dans les classes ; autrement dit, les classes dérivées ne peuvent avoir qu’une seule classe de base. Même si l’héritage multiple n’est pas autorisé dans les classes, les classes peuvent implémenter plusieurs interfaces, ce qui peut effectivement atteindre les mêmes terminaisons.

- Pour empêcher l’exposition d’éléments restreints dans une classe de base, le type d’accès d’une classe dérivée doit être égal ou plus restrictif que sa classe de base. Par exemple, une classe `Public` ne peut pas hériter d’une classe `Friend` ou `Private`, et une classe `Friend` ne peut pas hériter d’une classe `Private`.

## <a name="inheritance-modifiers"></a>Modificateurs d’héritage

Visual Basic introduit les instructions et les modificateurs de niveau classe suivants pour prendre en charge l’héritage :

- instruction `Inherits` : spécifie la classe de base.

- modificateur de `NotInheritable` : empêche les programmeurs d’utiliser la classe comme classe de base.

- `MustInherit` modifier : spécifie que la classe est destinée à être utilisée comme classe de base uniquement. Les instances de `MustInherit` classes ne peuvent pas être créées directement ; ils peuvent uniquement être créés en tant qu’instances de classe de base d’une classe dérivée. (D’autres langages de programmation C++ , C#tels que et, utilisent le terme *classe abstraite* pour décrire une telle classe.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Substitution de propriétés et de méthodes dans les classes dérivées

Par défaut, une classe dérivée hérite des propriétés et des méthodes de sa classe de base. Si une propriété ou une méthode héritée doit se comporter différemment dans la classe dérivée, elle peut être *substituée*. Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode dans la classe dérivée. Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :

- `Overridable` : permet à une propriété ou à une méthode d’une classe d’être substituée dans une classe dérivée.

- `Overrides` : substitue une propriété ou une méthode `Overridable` définie dans la classe de base.

- `NotOverridable` : empêche une propriété ou une méthode d’être substituée dans une classe qui hérite. Par défaut, les méthodes de `Public` sont `NotOverridable`.

- `MustOverride` : exige qu’une classe dérivée substitue la propriété ou la méthode. Lorsque le mot clé `MustOverride` est utilisé, la définition de la méthode se compose uniquement de l’instruction `Sub`, `Function` ou `Property`. Aucune autre instruction n’est autorisée et, en particulier, il n’y a pas d’instruction `End Sub` ou `End Function`. `MustOverride` méthodes doivent être déclarées dans des classes `MustInherit`.

Supposons que vous souhaitiez définir des classes pour gérer les salaires. Vous pouvez définir une classe de `Payroll` générique qui contient une méthode `RunPayroll` qui calcule la paie d’une semaine classique. Vous pouvez ensuite utiliser `Payroll` comme classe de base pour une classe `BonusPayroll` plus spécialisée, qui pourrait être utilisée lors de la distribution des bonus des employés.

La classe `BonusPayroll` peut hériter de la méthode `PayEmployee` définie dans la classe de base `Payroll` et la substituer.

L’exemple suivant définit une classe de base, `Payroll,` et une classe dérivée, `BonusPayroll`, qui substitue une méthode héritée, `PayEmployee`. Une procédure, `RunPayroll`, crée, puis passe un objet `Payroll` et un objet `BonusPayroll` à une fonction, `Pay`, qui exécute la méthode `PayEmployee` des deux objets.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>Le mot clé MyBase

Le mot clé `MyBase` se comporte comme une variable objet qui fait référence à la classe de base de l’instance actuelle d’une classe. `MyBase` est fréquemment utilisé pour accéder aux membres de la classe de base qui sont substitués ou occultés dans une classe dérivée. En particulier, `MyBase.New` est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.

Par exemple, supposons que vous conceviez une classe dérivée qui substitue une méthode héritée de la classe de base. La méthode substituée peut appeler la méthode dans la classe de base et modifier la valeur de retour comme indiqué dans le fragment de code suivant :

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

La liste suivante décrit les restrictions relatives à l’utilisation de `MyBase` :

- `MyBase` fait référence à la classe de base immédiate et à ses membres hérités. Elle ne peut pas être utilisée pour accéder à `Private` membres de la classe.

- `MyBase` est un mot clé, et non un objet réel. `MyBase` ne peut pas être assigné à une variable, passé à des procédures ou utilisé dans une comparaison `Is`.

- La méthode qui `MyBase` qualifie n’a pas besoin d’être définie dans la classe de base immédiate ; elle peut être définie à la place dans une classe de base indirectement héritée. Pour qu’une référence qualifiée par `MyBase` soit compilée correctement, une classe de base doit contenir une méthode qui correspond au nom et aux types des paramètres qui s’affichent dans l’appel.

- Vous ne pouvez pas utiliser `MyBase` pour appeler des méthodes de classe de base `MustOverride`.

- `MyBase` ne peut pas être utilisé pour se qualifier lui-même. Par conséquent, le code suivant n’est pas valide :

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase` ne peut pas être utilisé dans les modules.

- `MyBase` ne peut pas être utilisé pour accéder aux membres de la classe de base marqués comme `Friend` si la classe de base se trouve dans un assembly différent.

Pour plus d’informations et pour obtenir un autre exemple, consultez [Comment : accéder à une variable masquée par une classe dérivée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>Mot clé MyClass

Le mot clé `MyClass` se comporte comme une variable objet qui fait référence à l’instance actuelle d’une classe telle qu’elle a été implémentée à l’origine. `MyClass` ressemble à `Me`, mais chaque méthode et appel de propriété sur `MyClass` est traité comme si la méthode ou la propriété était [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Par conséquent, la méthode ou la propriété n’est pas affectée par la substitution dans une classe dérivée.

- `MyClass` est un mot clé, et non un objet réel. `MyClass` ne peut pas être assigné à une variable, passé à des procédures ou utilisé dans une comparaison `Is`.

- `MyClass` fait référence à la classe conteneur et à ses membres hérités.

- `MyClass` peut être utilisé en tant que qualificateur pour les membres `Shared`.

- `MyClass` ne peut pas être utilisé à l’intérieur d’une méthode `Shared`, mais peut être utilisé dans une méthode d’instance pour accéder à un membre partagé d’une classe.

- `MyClass` ne peut pas être utilisé dans les modules standard.

- `MyClass` peut être utilisé pour qualifier une méthode définie dans une classe de base et qui n’a aucune implémentation de la méthode fournie dans cette classe. Une telle référence a la même signification que `MyBase.`*méthode*.

L’exemple suivant compare `Me` et `MyClass`.

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

Même si `derivedClass` remplace `testMethod`, le mot clé `MyClass` dans `useMyClass` annule les effets de la substitution, et le compilateur résout l’appel à la version de la classe de base de `testMethod`.

## <a name="see-also"></a>Voir aussi

- [Inherits (instruction)](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
