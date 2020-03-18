---
title: Limitations sur l’utilisation des niveaux d’accessibilité - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 48ab765db7c839ed0dd14df5e6b30f5bd6c0d29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173534"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Limitations sur l’utilisation des niveaux d’accessibilité (informations de référence sur C#)

Lorsque vous spécifiez un type dans une déclaration, vérifiez si le niveau d’accessibilité du type dépend du niveau d’accessibilité d’un membre ou d’un autre type. Par exemple, la classe de base directe doit être au moins aussi accessible que la classe dérivée. Les déclarations suivantes entraînent une erreur du compilateur, car la classe de base `BaseClass` est moins accessible que `MyClass` :

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

Le tableau suivant résume les limitations sur les niveaux d’accessibilité déclarés.

|Context|Notes |
|-------------|-------------|
|[Classes](../../programming-guide/classes-and-structs/classes.md)|La classe de base directe d’un type de classe doit être au moins aussi accessible que le type de classe lui-même.|
|[Interfaces](../../programming-guide/interfaces/index.md)|Les interfaces de base explicites d’un type d’interface doivent être au moins aussi accessibles que le type d’interface lui-même.|
|[Délégués](../../programming-guide/delegates/index.md)|Le type de retour et les types de paramètres d’un type délégué doivent être au moins aussi accessibles que le type délégué lui-même.|
|[Constantes](../../programming-guide/classes-and-structs/constants.md)|Le type d’une constante doit être au moins aussi accessible que la constante elle-même.|
|[Champs](../../programming-guide/classes-and-structs/fields.md)|Le type d’un champ doit être au moins aussi accessible que le champ lui-même.|
|[Méthodes](../../programming-guide/classes-and-structs/methods.md)|Le type de retour et les types de paramètres d’une méthode doivent être au moins aussi accessibles que la méthode elle-même.|
|[Propriétés](../../programming-guide/classes-and-structs/properties.md)|Le type d’une propriété doit être au moins aussi accessible que la propriété elle-même.|
|[Événements](../../programming-guide/events/index.md)|Le type d’un événement doit être au moins aussi accessible que l’événement lui-même.|
|[Indexeurs](../../programming-guide/indexers/index.md)|Le type et les types de paramètres d’un indexeur doivent être au moins aussi accessibles que l’indexeur lui-même.|
|[Opérateurs](../operators/index.md)|Le type de retour et les types de paramètres d’un opérateur doivent être au moins aussi accessibles que l’opérateur lui-même.|
|[Constructeurs](../../programming-guide/classes-and-structs/constructors.md)|Les types de paramètres d’un constructeur doivent être au moins aussi accessibles que le constructeur lui-même.|

## <a name="example"></a> Exemple

L’exemple suivant contient des déclarations erronées de différents types. Le commentaire qui suit chaque déclaration indique l’erreur du compilateur à attendre.

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error:
    // "The parameter B.MyPrivateMethod is not accessible due to
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../../language-reference/index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](../../language-reference/keywords/index.md)
- [Modificateurs d’accès](../../language-reference/keywords/access-modifiers.md)
- [Domaine d’accessibilité](../../language-reference/keywords/accessibility-domain.md)
- [Niveaux d’accessibilité](../../language-reference/keywords/accessibility-levels.md)
- [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](../../language-reference/keywords/public.md)
- [Privé](../../language-reference/keywords/private.md)
- [Protégé](../../language-reference/keywords/protected.md)
- [Interne](../../language-reference/keywords/internal.md)
