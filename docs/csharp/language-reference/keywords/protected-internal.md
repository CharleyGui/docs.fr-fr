---
title: protected internal - Référence C#
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: 4067da93bcceba0fa3e4a14aa58b4cde812412f3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301786"
---
# <a name="protected-internal-c-reference"></a>protected internal (Référence C#)

La combinaison de mots clés `protected internal` est un modificateur d’accès de membre. Un membre interne protégé est accessible depuis l’assembly actif ou depuis des types dérivés de la classe conteneur. Pour obtenir une comparaison de `protected internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md).

## <a name="example"></a>Exemple

Un membre interne protégé d’une classe de base est accessible depuis n’importe quel type au sein de son assembly conteneur. Il est également accessible dans une classe dérivée qui se trouve dans un autre assembly seulement si l’accès s’effectue via une variable du type de la classe dérivée. Prenons l’exemple de l’extrait de code suivant :

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly2.cs`.
Le premier fichier contient une classe de base publique, `BaseClass`, et une autre classe, `TestAccess`. `BaseClass` possède un membre interne protégé, `myValue`, à laquelle le type `TestAccess` accède.
Dans le deuxième fichier, une tentative d’accès à `myValue` via une instance de `BaseClass` génère une erreur, tandis qu’un accès à ce membre via une instance d’une classe dérivée, `DerivedClass`, réussit.

Les membres de struct ne peuvent pas être `protected internal`, car le struct ne peut pas être hérité.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs d’accès](access-modifiers.md)
- [Niveaux d'accessibilité](accessibility-levels.md)
- [Modificateurs](index.md)
- [public](public.md)
- [priv](private.md)
- [intérieurs](internal.md)
- [Problèmes de sécurité pour les mots clés virtuels internes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
