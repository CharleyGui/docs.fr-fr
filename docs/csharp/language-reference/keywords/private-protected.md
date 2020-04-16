---
title: private protected - Référence C#
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 03fa90582d096919f2e6546fae2fde28e486fe41
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463056"
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

Si `Assembly1.cs` contient <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> un `Assembly2`nom que `DerivedClass1` , la `private protected` classe `BaseClass`dérivée aura accès aux membres déclarés en . `InternalsVisibleTo`rend `private protected` les membres visibles aux classes dérivées dans d’autres assemblées.

Les membres de struct ne peuvent pas être `private protected`, car le struct ne peut pas être hérité.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation CMD](../../programming-guide/index.md)
- [Mots-clés C](index.md)
- [Modificateurs d’accès](access-modifiers.md)
- [Niveaux d'accessibilité](accessibility-levels.md)
- [Modificateurs](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Problèmes de sécurité pour les mots clés virtuels internes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
