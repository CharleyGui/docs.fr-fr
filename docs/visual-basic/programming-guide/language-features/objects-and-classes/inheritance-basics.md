---
title: Éléments fondamentaux de l’héritage
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
ms.openlocfilehash: 89fcf2a14d8938d536aa72628218242811baa1a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400882"
---
# <a name="inheritance-basics-visual-basic"></a>Éléments fondamentaux de l'héritage (Visual Basic)

La `Inherits` déclaration est utilisée pour déclarer une nouvelle classe, appelée *classe dérivée,* basée sur une classe existante, connue sous le nom de *classe de base*. Les classes dérivées héritent et peuvent s’étendre, les propriétés, les méthodes, les événements, les champs et les constantes définis dans la classe de base. La section suivante décrit certaines des règles d’héritage, et les modificateurs que vous pouvez utiliser pour changer la façon dont les classes héritent ou sont héritées :

- Par défaut, toutes les classes sont `NotInheritable` héréditaires à moins d’être marquées par le mot clé. Les classes peuvent hériter d’autres classes de votre projet ou de cours dans d’autres assemblées que votre projet fait référence.

- Contrairement aux langues qui permettent un héritage multiple, Visual Basic n’autorise qu’un seul héritage dans les classes; c’est-à-dire que les classes dérivées ne peuvent avoir qu’une seule classe de base. Bien que l’héritage multiple ne soit pas autorisé dans les classes, les classes peuvent implémenter plusieurs interfaces, qui peuvent accomplir efficacement les mêmes extrémités.

- Pour éviter d’exposer des articles restreints dans une classe de base, le type d’accès d’une classe dérivée doit être égal ou plus restrictif que sa classe de base. Par exemple, `Public` une classe `Friend` ne `Private` peut pas `Friend` hériter `Private` d’une classe ou d’une classe, et une classe ne peut pas hériter d’une classe.

## <a name="inheritance-modifiers"></a>Modifications d’héritage

Visual Basic présente les énoncés et les modificateurs de niveau de classe suivants pour soutenir l’héritage :

- `Inherits`déclaration — Précise la classe de base.

- `NotInheritable`modificateur — Empêche les programmeurs d’utiliser la classe comme classe de base.

- `MustInherit`modificateur — Précise que la classe est destinée à être utilisée comme classe de base seulement. Les `MustInherit` instances des classes ne peuvent pas être créées directement; ils ne peuvent être créés que comme instances de classe de base d’une classe dérivée. (D’autres langages de programmation, tels que le C et le CMD, utilisent le terme *classe abstraite* pour décrire une telle classe.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Propriétés et méthodes prépondérer dans les classes dérivées

Par défaut, une classe dérivée des propriétés et des méthodes de sa classe de base. Si une propriété ou une méthode héritée doit se comporter différemment dans la classe dérivée, elle peut être *remplacée.* Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode dans la classe dérivée. Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :

- `Overridable`— Permet de répartir une propriété ou une méthode dans une classe dans une classe dérivée.

- `Overrides`— Remplace une `Overridable` propriété ou une méthode définie dans la classe de base.

- `NotOverridable`— Empêche qu’une propriété ou une méthode ne soit remplacée dans une classe d’héritage. Par défaut, `Public` `NotOverridable`les méthodes sont .

- `MustOverride`— Exige qu’une classe dérivée l’emporte sur la propriété ou la méthode. Lorsque `MustOverride` le mot clé est utilisé, `Sub`la `Function`définition `Property` de la méthode se compose de seulement le , , ou la déclaration. Aucune autre déclaration n’est autorisée, et en particulier il n’y a pas `End Sub` ou `End Function` déclaration. `MustOverride`méthodes doivent être `MustInherit` déclarées en classe.

Supposons que vous voulez définir les classes pour gérer la paie. Vous pouvez définir `Payroll` une classe `RunPayroll` générique qui contient une méthode qui calcule la paie pour une semaine typique. Vous pouvez `Payroll` alors utiliser comme classe `BonusPayroll` de base pour une classe plus spécialisée, qui pourrait être utilisée lors de la distribution des primes des employés.

La `BonusPayroll` classe peut hériter `PayEmployee` et remplacer la `Payroll` méthode définie dans la classe de base.

L’exemple suivant définit une `Payroll,` classe de `BonusPayroll`base, et une classe `PayEmployee`dérivée, qui l’emporte sur une méthode héritée, . Une `RunPayroll`procédure, , crée `Payroll` puis passe `BonusPayroll` un objet `Pay`et un objet `PayEmployee` à une fonction, , qui exécute la méthode des deux objets.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>Le mot-clé MyBase

Le `MyBase` mot clé se comporte comme une variable d’objet qui se réfère à la classe de base de l’instance actuelle d’une classe. `MyBase`est fréquemment utilisé pour accéder aux membres de la classe de base qui sont remplacés ou ombragés dans une classe dérivée. En particulier, `MyBase.New` est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.

Supposons, par exemple, que vous concevez une classe dérivée qui remplace une méthode héritée de la classe de base. La méthode précédée peut appeler la méthode dans la classe de base et modifier la valeur de retour comme indiqué dans le fragment de code suivant :

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

La liste suivante décrit `MyBase`les restrictions à l’utilisation :

- `MyBase`se réfère à la classe de base immédiate et à ses membres hérités. Il ne peut `Private` pas être utilisé pour accéder aux membres de la classe.

- `MyBase`est un mot clé, pas un objet réel. `MyBase`ne peuvent pas être affectés à une variable, `Is` transmis aux procédures ou utilisés en comparaison.

- La méthode `MyBase` qui est admissible n’a pas à être définie dans la classe de base immédiate; il peut plutôt être défini dans une classe de base indirectement héritée. Afin qu’une référence `MyBase` qualifiée pour compiler correctement, une classe de base doit contenir une méthode correspondant au nom et aux types de paramètres qui apparaissent dans l’appel.

- Vous ne `MyBase` pouvez `MustOverride` pas utiliser pour appeler les méthodes de classe de base.

- `MyBase`ne peut pas être utilisé pour se qualifier lui-même. Par conséquent, le code suivant n’est pas valide :

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`ne peut pas être utilisé dans les modules.

- `MyBase`ne peut pas être utilisé pour `Friend` accéder aux membres de la classe de base qui sont marqués comme si la classe de base est dans une assemblée différente.

Pour plus d’informations et un autre exemple, voir [Comment : Accéder à une variable cachée par une classe dérivée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>Le mot-clé MyClass

Le `MyClass` mot clé se comporte comme une variable d’objet qui se réfère à l’instance actuelle d’une classe telle qu’elle a été mise en œuvre à l’origine. `MyClass`ressemble `Me`, mais chaque méthode `MyClass` et appel de propriété sur est traitée comme si la méthode ou la propriété [n’étaient pasOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Par conséquent, la méthode ou la propriété n’est pas affectée par le dépassement dans une classe dérivée.

- `MyClass`est un mot clé, pas un objet réel. `MyClass`ne peuvent pas être affectés à une variable, `Is` transmis aux procédures ou utilisés en comparaison.

- `MyClass`se réfère à la classe de confinement et à ses membres hérités.

- `MyClass`peut être utilisé comme `Shared` un qualificatif pour les membres.

- `MyClass`ne peut pas `Shared` être utilisé à l’intérieur d’une méthode, mais peut être utilisé à l’intérieur d’une méthode d’instance pour accéder à un membre partagé d’une classe.

- `MyClass`ne peut pas être utilisé dans des modules standard.

- `MyClass`peut être utilisé pour qualifier une méthode qui est définie dans une classe de base et qui n’a pas de mise en œuvre de la méthode fournie dans cette classe. Une telle référence a `MyBase.`le même sens que *la méthode*.

L’exemple suivant `Me` `MyClass`se compare et .

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

Même `derivedClass` si les `testMethod`remplacements, le `MyClass` mot clé dans `useMyClass` annule les effets de la prépondération, `testMethod`et le compilateur résout l’appel à la version de la classe de base de .

## <a name="see-also"></a>Voir aussi

- [Inherits (instruction)](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
