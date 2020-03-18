---
title: '#Directive de préprocesseur if - Référence C#'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899852"
---
# <a name="if-c-reference"></a>#if (référence C)

Quand le compilateur C# rencontre une directive `#if`, suivie éventuellement d’une directive [#endif](preprocessor-endif.md), il compile le code entre les directives uniquement si le symbole spécifié est défini. Contrairement à C et C++, vous ne pouvez pas attribuer de valeur numérique à un symbole. L’énoncé `#if` dans C est Boolean et ne teste que si le symbole a été défini ou non. Par exemple :

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Vous pouvez utiliser [==](../operators/equality-operators.md#equality-operator-) les opérateurs (égalité) et [!'](../operators/equality-operators.md#inequality-operator-) (inégalité) `true` `false`seulement pour tester les valeurs [bool](../builtin-types/bool.md) ou . `true`signifie que le symbole est défini. L’instruction `#if DEBUG` a la même signification que `#if (DEBUG == true)`. Vous pouvez utiliser le [&&  (et)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;  (ou)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), et [! (non)](../operators/boolean-logical-operators.md#logical-negation-operator-) d’évaluer si plusieurs symboles ont été définis. Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.

## <a name="remarks"></a>Notes 

`#if`, avec le [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), et [#undef](preprocessor-undef.md) directives, vous permet d’inclure ou d’exclure le code en fonction de l’existence d’un ou plusieurs symboles. Cela peut être utile lors de la compilation du code pour une version Debug ou lors de la compilation d’une configuration spécifique.

Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.

`#define` vous permet de définir un symbole. En utilisant ensuite ce dernier comme expression passée à la directive `#if`, l’expression correspond à `true`.

Vous pouvez également définir un symbole avec l’option [compilateur-définir.](../compiler-options/define-compiler-option.md) Vous pouvez annuler la définition d’un symbole avec [#undef](preprocessor-undef.md).

Un symbole que vous définissez avec `-define` ou `#define` n’est pas en conflit avec une variable du même nom. Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur, et un symbole ne peut être évalué que par une directive de préprocesseur.

La portée d’un symbole créé avec `#define` est le fichier dans lequel il a été défini.

Le système de construction est également conscient des symboles préprocesseurs prédéfinis représentant différents cadres cibles dans [des projets](../../../standard/frameworks.md) de type SDK. Ils sont utiles durant la création d’applications pouvant cibler plusieurs versions ou implémentations de .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> Pour les projets cadres .NET traditionnels, vous devez configurer manuellement les symboles de compilation conditionnelles pour les différents cadres cibles de Visual Studio via les pages propriétés du projet.

Parmi les autres symboles prédéfinis se trouvent les constantes DEBUG et TRACE. Vous pouvez remplacer les valeurs définies pour le projet à l’aide de `#define`. Le symbole DEBUG, par exemple, est automatiquement défini en fonction de vos propriétés de configuration de build (mode « Debug » ou « Release »).

## <a name="examples"></a>Exemples

L’exemple suivant montre comment définir un symbole MYTEST sur un fichier, puis tester les valeurs des symboles MYTEST et DEBUG. La sortie de cet exemple dépend du mode de configuration que vous avez utilisé pour créer le projet (Debug ou Release).

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

L’exemple suivant montre comment tester différents frameworks cibles pour pouvoir utiliser les nouvelles API dans la mesure du possible :

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur de CMD](index.md)
- [Comment : effectuer une compilation conditionnelle avec Trace et Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
