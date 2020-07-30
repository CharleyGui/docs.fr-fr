---
title: Valeurs de retour de Main() - Guide de programmation C#
description: En savoir plus sur les valeurs de retour main (). Consultez les exemples de code, le code généré par le compilateur et l’affichage des ressources supplémentaires disponibles.
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 4458f3cd7c8259c5725cfe5e853f826fe2ef61cc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382059"
---
# <a name="main-return-values-c-programming-guide"></a>Valeurs de retour de Main() (Guide de programmation C#)

La méthode `Main` peut retourner `void` :

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Elle peut également retourner un `int` :

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Si la valeur de retour de `Main` n’est pas utilisée, retourner `void` permet d’avoir un code un peu plus simple. Cependant, retourner un entier permet au programme de communiquer des informations d’état à d’autres programmes ou scripts qui appellent le fichier exécutable. La valeur de retour de `Main` est traitée comme le code de sortie du processus. Si `void` est retourné à partir de `Main` , le code de sortie est implicitement `0` . L’exemple suivant montre comment accéder à la valeur de retour de `Main`.

## <a name="example"></a>Exemple

Cet exemple utilise les outils en ligne de commande [.net Core](../../../core/index.yml) . Si vous n’êtes pas familiarisé avec les outils en ligne de commande .NET Core, vous pouvez en savoir plus à ce sujet dans cet [article de prise en main](../../../core/tutorials/with-visual-studio-code.md).

Modifiez la méthode `Main` dans *program.cs* comme suit :

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Quand un programme est exécuté dans Windows, toute valeur retournée par la fonction `Main` est stockée dans une variable d’environnement. Cette variable d’environnement peut être récupérée à l’aide de `ERRORLEVEL` dans un fichier de commandes ou de `$LastExitCode` dans PowerShell.

Vous pouvez générer l’application à l’aide de la commande [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build`.

Ensuite, créez un script PowerShell pour exécuter l’application et afficher le résultat. Collez le code suivant dans un fichier texte et enregistrez-le sous `test.ps1` dans le dossier qui contient le projet. Exécutez le script PowerShell en tapant `test.ps1` à l’invite de PowerShell.

Comme le code retourne zéro, le fichier de commandes indique la réussite. Toutefois, si vous modifiez MainReturnValTest.cs pour retourner une valeur différente de zéro, puis recompilez le programme, l’exécution suivante du script PowerShell signalera un échec.

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Exemple de sortie

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

- [Guide de programmation C#](../index.md)
- [Référence C#](../index.md)
- [Main () et arguments de ligne de commande](index.md)
- [Comment afficher les arguments de ligne de commande](./how-to-display-command-line-arguments.md)
