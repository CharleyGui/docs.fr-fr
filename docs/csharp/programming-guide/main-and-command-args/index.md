---
title: Main() et arguments de ligne de commande - Guide de programmation C#
description: En savoir plus sur les arguments main () et de ligne de commande. La méthode main est le point d’entrée d’un programme exécutable.
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 95ec9d3dfebe4721d4b1822939f925aa37b9e9c4
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382072"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() et arguments de ligne de commande (Guide de programmation C#)

La méthode `Main` est le point d’entrée d’une application C#. (Les bibliothèques et les services ne requièrent pas de `Main` méthode comme point d’entrée.) Lorsque l’application est démarrée, la `Main` méthode est la première méthode appelée.

Il ne peut y avoir qu’un seul point d’entrée dans un programme C#. Si vous avez plusieurs classes qui ont une `Main` méthode, vous devez compiler votre programme avec l' `-main` option de compilateur pour spécifier la `Main` méthode à utiliser comme point d’entrée. Pour plus d’informations, consultez [-main (options du compilateur C#)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Vue d’ensemble

- La méthode `Main` est le point d’entrée d’un programme exécutable ; c’est l’endroit où le contrôle du programme commence et se termine.
- `Main` est déclaré à l’intérieur d’une classe ou d’un struct. `Main` doit être [statique](../../language-reference/keywords/static.md) et ne doit pas être [public](../../language-reference/keywords/public.md). (Dans l’exemple précédent, il reçoit l’accès par défaut de [Private](../../language-reference/keywords/private.md).) La classe ou le struct englobant ne doit pas obligatoirement être statique.
- `Main` peut avoir un type de retour `void`, `int` ou, à partir de C# 7.1, `Task` ou `Task<int>`.
- Si et seulement si `Main` retourne `Task` ou `Task<int>` , la déclaration de `Main` peut inclure le [`async`](../../language-reference/keywords/async.md) modificateur. Notez que cela exclut spécifiquement une méthode `async void Main`.
- La méthode `Main` peut être déclarée avec ou sans paramètre `string[]`, qui contient des arguments de ligne de commande. Lorsque vous utilisez Visual Studio pour créer des applications Windows, vous pouvez ajouter le paramètre manuellement ou utiliser la <xref:System.Environment.GetCommandLineArgs> méthode pour obtenir les [arguments de ligne de commande](command-line-arguments.md). Les paramètres sont lus comme des arguments de ligne de commande avec index de base zéro. Contrairement à C et C++, le nom du programme n’est pas traité comme le premier argument de ligne de commande dans le `args` tableau, mais il s’agit du premier élément de la <xref:System.Environment.GetCommandLineArgs> méthode.

La liste suivante répertorie les signatures valides `Main` :

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

Les exemples précédents utilisent tous le modificateur d’accesseur public. Cela est courant, mais pas obligatoire.

L’ajout des types de retour `async` et `Task`, `Task<int>` simplifie le code de programme lorsque les applications de console doivent démarrer et `await` des opérations asynchrones dans `Main`.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Génération à partir de la ligne de commande avec csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Guide de programmation C#](../index.md)
- [Méthodes](../classes-and-structs/methods.md)
- [À l’intérieur d’un programme C#](../inside-a-program/index.md)
