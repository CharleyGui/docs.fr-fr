---
description: '#Directive de préprocesseur if - Référence C#'
title: '#Directive de préprocesseur if - Référence C#'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: f01db9d7801d4b6f4c273a9cf82806acbb4828bb
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138135"
---
# <a name="if-c-reference"></a>#if (référence C#)

Quand le compilateur C# rencontre une directive `#if`, suivie éventuellement d’une directive [#endif](preprocessor-endif.md), il compile le code entre les directives uniquement si le symbole spécifié est défini. Contrairement à C et C++, vous ne pouvez pas attribuer de valeur numérique à un symbole. L' `#if` instruction en C# est booléenne et teste uniquement si le symbole a été défini ou non. Par exemple :

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Vous pouvez utiliser les opérateurs [==](../operators/equality-operators.md#equality-operator-) (égalité) et [! =](../operators/equality-operators.md#inequality-operator-) (inégalité) uniquement pour tester les valeurs [bool](../builtin-types/bool.md) `true` ou `false` . `true` signifie que le symbole est défini. L’instruction `#if DEBUG` a la même signification que `#if (DEBUG == true)`. Vous pouvez utiliser les [&&  (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;  (ou)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)et [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) opérateurs permettant d’évaluer si plusieurs symboles ont été définis. Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.

## <a name="remarks"></a>Remarques

`#if`, ainsi que les directives [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)et [#undef](preprocessor-undef.md) , vous permettent d’inclure ou d’exclure du code en fonction de l’existence d’un ou plusieurs symboles. Cela peut être utile lors de la compilation du code pour une version Debug ou lors de la compilation d’une configuration spécifique.

Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.

`#define` vous permet de définir un symbole. En utilisant ensuite ce dernier comme expression passée à la directive `#if`, l’expression correspond à `true`.

Vous pouvez également définir un symbole avec l’option [de compilateur-define](../compiler-options/define-compiler-option.md) . Vous pouvez annuler la définition d’un symbole avec [#undef](preprocessor-undef.md).

Un symbole que vous définissez avec `-define` ou `#define` n’est pas en conflit avec une variable du même nom. Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur, et un symbole ne peut être évalué que par une directive de préprocesseur.

La portée d’un symbole créé avec `#define` est le fichier dans lequel il a été défini.

Le système de génération est également conscient des symboles de préprocesseur prédéfinis qui représentent différents [frameworks cibles](../../../standard/frameworks.md) dans les projets de type SDK. Ils sont utiles durant la création d’applications pouvant cibler plusieurs versions ou implémentations de .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> Pour les projets de .NET Framework traditionnels, vous devez configurer manuellement les symboles de compilation conditionnelle pour les différents frameworks cibles dans Visual Studio via les pages de propriétés du projet.

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

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](index.md)
- [Procédure : Effectuer une compilation conditionnelle avec Trace et Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
