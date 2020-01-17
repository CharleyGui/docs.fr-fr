---
title: Types référence intégrés - Référence C#
description: Découvrez les types référence qui ont des mots clés C# que vous pouvez utiliser pour les déclarer.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: d5ca0593d802d331d980cf35c701e0a79d54abee
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163096"
---
# <a name="built-in-reference-types-c-reference"></a>Types référence intégrés (Référence C#)

C# a un nombre de types référence intégrés. Ils ont des mots clés ou des opérateurs qui sont synonymes pour un type dans la bibliothèque .NET. 

## <a name="the-object-type"></a>Type d’objet

Le type `object` est un alias de <xref:System.Object?displayProperty=nameWithType> dans .NET. Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object?displayProperty=nameWithType>. Vous pouvez assigner des valeurs de tout type aux variables de type `object`. Toute variable `object` peut être attribuée à sa valeur par défaut à l’aide du littéral `null`. Quand une variable d’un type valeur est convertie en type objet, elle est dite *boxed*. Quand une variable de type `object` est convertie en un type valeur, elle est dite *unboxed*. Pour plus d’informations, consultez [Conversion boxing et unboxing](../../programming-guide/types/boxing-and-unboxing.md). 

## <a name="the-string-type"></a>Type de chaîne

Le type `string` représente une séquence de zéro, un ou plusieurs caractères Unicode. `string` est un alias de <xref:System.String?displayProperty=nameWithType> dans .NET.

Bien que `string` soit un type référence, les [opérateurs d’égalité`==` (`!=` et ](../operators/equality-operators.md#string-equality)) sont définis pour comparer les valeurs des objets `string`, pas les références. Cela permet de tester l’égalité de chaînes de façon plus intuitive. Par exemple :

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Cette opération affiche « True », puis « False », car le contenu des chaînes est équivalent, mais `a` et `b` ne font pas référence à la même instance de chaîne.

L’[opérateur +](../operators/addition-operator.md#string-concatenation) concatène les chaînes :

```csharp
string a = "good " + "morning";
```

Cela crée un objet String qui contient « good morning ».

Les chaînes sont *immuables* : il est impossible de changer le contenu d’un objet String après avoir créé l’objet, bien que la syntaxe semble indiquer le contraire. Par exemple, lorsque vous écrivez ce code, le compilateur crée en fait un nouvel objet String pour stocker la nouvelle séquence de caractères, et ce nouvel objet est attribué à `b`. La mémoire allouée pour `b` (quand elle contenait la chaîne « h ») est alors éligible pour le garbage collection.

```csharp
string b = "h";
b += "ello";
```

L' [opérateur](../operators/member-access-operators.md#indexer-operator-) `[]` peut être utilisé pour l’accès en lecture seule aux caractères individuels d’une chaîne. Les valeurs d’index valides commencent à `0` et doivent être inférieures à la longueur de la chaîne :

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

De la même façon, l’opérateur `[]` peut également être utilisé pour itérer au sein de chaque caractère dans une chaîne :

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Les littéraux de chaîne sont de type `string` et peuvent être écrits sous deux formes, entre guillemets et entre `@`. Les littéraux de chaîne entre guillemets sont placés entre guillemets doubles (") :

```csharp
"good morning"  // a string literal
```

Les littéraux de chaîne peuvent contenir tout littéral de caractère. Les séquences d’échappement sont incluses. L’exemple suivant utilise la séquence d’échappement `\\` pour la barre oblique inverse, `\u0066` pour la lettre f et `\n` pour un saut de ligne.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Le code d’échappement `\udddd` (où `dddd` est un nombre à quatre chiffres) représente le caractère Unicode U+`dddd`. Les codes d’échappement Unicode à huit chiffres sont également reconnus : `\Udddddddd`.

Les [littéraux de chaîne textuelle](../tokens/verbatim.md) commencent par `@` et sont placés entre guillemets doubles. Par exemple :

```csharp
@"good morning"  // a string literal
```

L’avantage des chaînes textuelles est que les séquences d’échappement *ne sont pas* traitées, ce qui facilite l’écriture, par exemple, d’un nom de fichier complet Windows :

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Pour inclure un guillemet double dans une chaîne @-quoted, doublez-le :

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Type de délégué

La déclaration d’un type délégué est semblable à une signature de méthode. Elle a une valeur de retour et un nombre quelconque de paramètres de type quelconque :

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

Dans .NET, les types `System.Action` et `System.Func` fournissent des définitions génériques pour de nombreux délégués courants. Vous n’avez probablement pas besoin de définir de nouveaux types de délégué personnalisés. À la place, vous pouvez créer des instanciations des types génériques fournis.

Un `delegate` est un type référence qui peut être utilisé pour encapsuler une méthode anonyme ou nommée. Les délégués sont comparables aux pointeurs fonction en C++, mais ils offrent l’avantage d’être sûrs et de type sécurisé. Pour les applications de délégués, consultez [Délégués](../../programming-guide/delegates/index.md) et [Délégués génériques](../../programming-guide/generics/generic-delegates.md). Les délégués sont la base des [événements](../../programming-guide/events/index.md). Un délégué peut être instancié en l’associant à une méthode nommée ou anonyme.

Le délégué doit être instancié avec une méthode ou une expression lambda qui a un type de retour compatible et des paramètres d’entrée. Pour plus d’informations sur le degré de variance autorisé dans la signature de méthode, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Pour une utilisation avec des méthodes anonymes, le délégué et le code à lui associer sont déclarés ensemble. 

## <a name="the-dynamic-type"></a>Type dynamique

Le type `dynamic` indique que l’utilisation de la variable et des références à ses membres contourne la vérification du type au moment de la compilation. Au lieu de cela, ces opérations sont résolues au moment de l’exécution. Le type `dynamic` simplifie l’accès aux API COM telles que les API Office Automation, aux API dynamiques telles que les bibliothèques IronPython et au modèle DOM (Document Object Model) HTML.

Le type `dynamic` se comporte comme le type `object` dans la plupart des cas. En particulier, toute expression non null peut être convertie en type `dynamic`. Le type `dynamic` diffère de `object` en cela que les opérations qui contiennent des expressions de type `dynamic` ne sont pas résolues et leur type n’est pas vérifié par le compilateur. Le compilateur empaquète des informations sur l’opération, qui sont ensuite utilisées pour évaluer l’opération au moment de l’exécution. Dans le cadre du processus, les variables de type `dynamic` sont compilées dans des variables de type `object`. Ainsi, le type `dynamic` existe seulement au moment de la compilation, et non au moment de l’exécution.

L’exemple suivant compare une variable de type `dynamic` à une variable de type `object`. Pour vérifier le type de chaque variable au moment de la compilation, placez le pointeur de la souris sur `dyn` ou `obj` dans les instructions `WriteLine`. Copiez le code suivant dans un éditeur où IntelliSense est disponible. IntelliSense affiche **dynamic** pour `dyn` et **object** pour `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

Les instructions <xref:System.Console.WriteLine%2A> affichent les types d’exécution de `dyn` et `obj`. À ce stade, tous deux ont le même type, entier. La sortie suivante est produite :

```console
System.Int32
System.Int32
```

Pour voir la différence entre `dyn` et `obj` au moment de la compilation, ajoutez les deux lignes suivantes entre les déclarations et les instructions `WriteLine` de l’exemple précédent.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Une erreur du compilateur est signalée pour la tentative d’ajout d’un entier et un d’objet dans l’expression `obj + 3`. Toutefois, aucune erreur n’est signalée pour `dyn + 3`. L’expression qui contient `dyn` n’est pas vérifié au moment de la compilation, car le type de `dyn` est `dynamic`.

L’exemple suivant utilise `dynamic` dans plusieurs déclarations. La méthode `Main` compare également la vérification de type au moment de la compilation avec la vérification de type au moment de l’exécution.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Mots clés C#](../keywords/index.md)
- [Événements](../../programming-guide/events/index.md)
- [Utilisation du type dynamic](../../programming-guide/types/using-type-dynamic.md)
- [Bonnes pratiques pour l’utilisation de chaînes](../../../standard/base-types/best-practices-strings.md)
- [Opérations de chaînes de base](../../../standard/base-types/basic-string-operations.md)
- [Création de chaînes](../../../standard/base-types/creating-new.md)
- [Opérateurs de test et de cast de type](../operators/type-testing-and-cast.md)
- [Comment effectuer un cast en toute sécurité à l’aide de critères spéciaux et des opérateurs As et is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Procédure pas à pas : création et utilisation d’objets dynamiques](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
