---
description: private protected - Référence C#
title: private protected - Référence C#
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: d83fd2a570b735a029bd2a79ad24e30d235dc5fb
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117959"
---
# <a name="private-protected-c-reference"></a>private protected (Référence C#)

La combinaison de mots clés `private protected` est un modificateur d’accès de membre. Un membre protégé privé est accessible par les types dérivés de la classe conteneur, mais seulement au sein de son assembly conteneur. Pour obtenir une comparaison de `private protected` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md).

> [!NOTE]
> Le modificateur d’accès `private protected` est valide dans C# 7.2 et ultérieur.

## <a name="example"></a>Exemple

Un membre protégé privé d’une classe de base est accessible à partir des types dérivés de son assembly conteneur seulement si le type statique de la variable est le type de la classe dérivée. Prenons l’exemple de l’extrait de code suivant :

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly2.cs`.
Le premier fichier contient une classe de base publique, `BaseClass`, et un type qui en est dérivé, `DerivedClass1`. `BaseClass` possède un membre protégé privé, `myValue`, auquel `DerivedClass1` tente d’accéder de deux manières. La première tentative d’accès à `myValue` via une instance de `BaseClass` génère une erreur. Cependant, la tentative de l’utiliser comme un membre hérité dans `DerivedClass1` réussit.

Dans le deuxième fichier, une tentative d’accès à `myValue` en tant que membre hérité de `DerivedClass2` génère une erreur, car il est accessible seulement par des types dérivés dans Assembly1.

Si `Assembly1.cs` contient un <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> nom `Assembly2` , la classe dérivée aura `DerivedClass1` accès aux `private protected` membres déclarés dans `BaseClass` . `InternalsVisibleTo` rend `private protected` les membres visibles aux classes dérivées dans d’autres assemblys.

Les membres de struct ne peuvent pas être `private protected`, car le struct ne peut pas être hérité.

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
