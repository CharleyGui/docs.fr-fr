---
title: nameof - Référence C#
ms.custom: seodec18
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 349cbf4e918d97a5a2a5c1e873d7fa114be8e2db
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306631"
---
# <a name="nameof-c-reference"></a>nameof (informations de référence sur C#)

Permet d'obtenir le nom de chaîne simple (non qualifié) d'une variable, d'un type ou d'un membre.

Pour le signalement des erreurs dans le code, le raccordement aux liens MVC (model-view-controller) et le déclenchement des événements de modification de propriété, entre autres, il est souvent utile de capturer le nom de chaîne d'une méthode.  L'utilisation de `nameof` vous aide à garantir la validité de votre code quand vous renommez des définitions.  Auparavant, vous deviez utiliser des littéraux de chaîne pour faire référence aux définitions, ce qui présentait un risque quand vous renommiez des éléments de code, car les outils ne vérifiaient pas ces littéraux de chaîne.

Une expression `nameof` se présente comme suit :

```csharp
if (x == null) throw new ArgumentNullException(nameof(x));
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"
```

## <a name="key-use-cases"></a>Principaux cas d'usage

Ces exemples montrent les principaux cas d'usage de `nameof`.

Validation des paramètres :

 ```csharp
void f(string s) {
    if (s == null) throw new ArgumentNullException(nameof(s));
}
```

Liens d'action MVC :

```html
<%= Html.ActionLink("Sign up",
             @typeof(UserController),
             @nameof(UserController.SignUp))
%>
```

INotifyPropertyChanged :

```csharp
int p {
    get { return this.p; }
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too
}
```

Propriété de dépendance XAML :

```csharp
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));
```

Journalisation :

```csharp
void f(int i) {
    Log(nameof(f), "method entry");
}
```

Attributs :

```csharp
[DebuggerDisplay("={" + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

## <a name="examples"></a>Exemples

Exemples C# :

```csharp
using Stuff = Some.Cool.Functionality
class C {
    static int Method1 (string x, int y) {}
    static int Method1 (string x, string y) {}
    int Method2 (int z) {}
    string f<T>() => nameof(T);
}

var c = new C()

class Test {
    static void Main (string[] args) {
        Console.WriteLine(nameof(C)); // -> "C"
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]
        Console.WriteLine(nameof(f)); // -> "f"
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]
        // Console.WriteLine(nameof(f<>)); -> [syntax error]
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]
    }
}
```

## <a name="remarks"></a>Remarques

L'argument de `nameof` doit être un nom simple, un nom qualifié, un accès au membre, un accès de base avec un membre spécifié ou cet accès avec un membre spécifié.  L'expression d'argument identifie une définition de code, mais n'est jamais évaluée.

L'argument doit être une expression d'un point de vue syntaxique. Il existe donc beaucoup d'éléments non autorisés qu'il n'est pas utile de répertorier ici.  En revanche, nous mentionnerons les éléments suivants qui génèrent des erreurs : les types prédéfinis (par exemple, `int` ou `void`), les types Nullable (`Point?`), les types tableau (`Customer[,]`), les types pointeur (`Buffer*`), les alias qualifiés (`A::B`), les types génériques indépendants (`Dictionary<,>`), les symboles de prétraitement (`DEBUG`) et les étiquettes (`loop:`).

Si vous avez besoin d'obtenir le nom qualifié complet, vous pouvez utiliser l'expression `typeof` avec `nameof`.  Par exemple :

```csharp
class C {
    void f(int i) {
        Log($"{typeof(C)}.{nameof(f)}", "method entry");
    }
}
```

Malheureusement, `typeof` n’est pas une expression constante comme `nameof`, `typeof` ne peut donc pas être utilisé en conjonction avec `nameof` dans les mêmes emplacements que `nameof`.  Par exemple, le code suivant entraîne une erreur de compilation CS0182 :

```csharp
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

Les exemples montrent que vous pouvez utiliser un nom de type et accéder à un nom de méthode d'instance.  Il n'est pas nécessaire d'avoir une instance du type, comme c'est le cas dans les expressions évaluées.  Utiliser le nom de type peut être très pratique dans certains cas et, comme vous référencez seulement le nom et que vous n'utilisez pas de données d'instance, vous n'avez pas besoin de combiner une variable d'instance ou une expression.

Vous pouvez référencer les membres d'une classe dans les expressions d'attribut sur la classe.

Il n'existe aucun moyen pour obtenir des informations de signature comme « `Method1 (str, str)` ».  Pour cela, vous pouvez utiliser une expression, `Expression e = () => A.B.Method1("s1", "s2")`, puis extraire MemberInfo de l'arborescence de l'expression qui en résulte.

## <a name="language-specifications"></a>Spécifications du langage

Pour plus d’informations, consultez [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) dans la [spécification du langage C#](../language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../../../csharp/language-reference/index.md)
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator)
