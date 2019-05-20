---
title: Valeurs de retour de Main() - Guide de programmation C#
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 1e4c03985908f6e49d5ce001cdc9c1472f5a6d44
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595598"
---
# <a name="main-return-values-c-programming-guide"></a>Valeurs de retour de Main() (Guide de programmation C#)

La méthode `Main` peut retourner `void` :

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Elle peut également retourner un `int` :

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Si la valeur de retour de `Main` n’est pas utilisée, retourner `void` permet d’avoir un code un peu plus simple. Cependant, retourner un entier permet au programme de communiquer des informations d’état à d’autres programmes ou scripts qui appellent le fichier exécutable. La valeur de retour de `Main` est traitée comme le code de sortie du processus. Si `void` est retourné à partir de `Main`, le code de sortie est implicitement `0`. L’exemple suivant montre comment accéder à la valeur de retour de `Main`.

## <a name="example"></a>Exemple

Cet exemple utilise les outils de ligne de commande [.NET Core](../../../core/index.md). Si vous ne connaissez pas les outils de ligne de commande .NET Core, vous pouvez les découvrir dans cette [rubrique Bien démarrer](../../../core/tutorials/using-with-xplat-cli.md).

Modifiez la méthode `Main` dans *program.cs* comme suit :

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Quand un programme est exécuté dans Windows, toute valeur retournée par la fonction `Main` est stockée dans une variable d’environnement. Cette variable d’environnement peut être récupérée à l’aide de `ERRORLEVEL` dans un fichier de commandes ou de `$LastExitCode` dans PowerShell.

Vous pouvez générer l’application à l’aide de la commande [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build`.

Ensuite, créez un script PowerShell pour exécuter l’application et afficher le résultat. Collez le code suivant dans un fichier texte et enregistrez-le sous `test.ps1` dans le dossier qui contient le projet. Exécutez le script PowerShell en tapant `test.ps1` à l’invite de PowerShell.

Comme le code retourne zéro, le fichier de commandes indique la réussite. Toutefois, si vous modifiez MainReturnValTest.cs pour qu’il retourne une valeur différente de zéro, puis que vous recompilez le programme, l’exécution suivante du script PowerShell indique un échec.

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Résultat de l'exemple

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Valeurs de retour d’Async Main

Les valeurs de retour d’Async Main déplacent le code réutilisable nécessaire pour appeler les méthodes asynchrones dans `Main` vers le code généré par le compilateur. Avant, vous auriez dû écrire cette construction pour appeler du code asynchrone et vérifier que votre programme s’est exécuté jusqu’à la fin de l’opération asynchrone :

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

Maintenant, vous pouvez la remplacer par :

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

L’avantage de la nouvelle syntaxe est que le compilateur génère toujours un code correct.

## <a name="compiler-generated-code"></a>Code généré par le compilateur

Quand le point d’entrée de l’application retourne `Task` ou `Task<int>`, le compilateur génère un nouveau point d’entrée qui appelle la méthode de point d’entrée déclarée dans le code d’application. En supposant que ce point d’entrée est appelé `$GeneratedMain`, le compilateur génère le code suivant pour ces points d’entrée :

- `static Task Main()` permet au compilateur d’émettre l’équivalent de `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` permet au compilateur d’émettre l’équivalent de `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` permet au compilateur d’émettre l’équivalent de `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` permet au compilateur d’émettre l’équivalent de `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Si les exemples ont utilisé le modificateur `async` sur la méthode `Main`, le compilateur génère le même code.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../programming-guide/index.md)
- [Référence C#](../index.md)
- [Main() et arguments de ligne de commande](index.md)
- [Guide pratique pour afficher les arguments de ligne de commande](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
