---
title: Valeurs de retour de Main() - Guide de programmation C#
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: a3e29903448c3eb5e0b7dda027677d1785a445e7
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416291"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="fbf9c-102">Valeurs de retour de Main() (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fbf9c-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="fbf9c-103">La méthode `Main` peut retourner `void` :</span><span class="sxs-lookup"><span data-stu-id="fbf9c-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="fbf9c-104">Elle peut également retourner un `int` :</span><span class="sxs-lookup"><span data-stu-id="fbf9c-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="fbf9c-105">Si la valeur de retour de `Main` n’est pas utilisée, retourner `void` permet d’avoir un code un peu plus simple.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="fbf9c-106">Cependant, retourner un entier permet au programme de communiquer des informations d’état à d’autres programmes ou scripts qui appellent le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="fbf9c-107">La valeur de retour de `Main` est traitée comme le code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="fbf9c-108">Si `void` est retourné à partir de `Main` , le code de sortie est implicitement `0` .</span><span class="sxs-lookup"><span data-stu-id="fbf9c-108">If `void` is returned from `Main`, the exit code will be implicitly `0`.</span></span> <span data-ttu-id="fbf9c-109">L’exemple suivant montre comment accéder à la valeur de retour de `Main`.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="fbf9c-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbf9c-110">Example</span></span>

<span data-ttu-id="fbf9c-111">Cet exemple utilise les outils en ligne de commande [.net Core](../../../core/index.yml) .</span><span class="sxs-lookup"><span data-stu-id="fbf9c-111">This example uses [.NET Core](../../../core/index.yml) command-line tools.</span></span> <span data-ttu-id="fbf9c-112">Si vous n’êtes pas familiarisé avec les outils en ligne de commande .NET Core, vous pouvez en savoir plus à ce sujet dans cet [article de prise en main](../../../core/tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="fbf9c-112">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="fbf9c-113">Modifiez la méthode `Main` dans *program.cs* comme suit :</span><span class="sxs-lookup"><span data-stu-id="fbf9c-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="fbf9c-114">Quand un programme est exécuté dans Windows, toute valeur retournée par la fonction `Main` est stockée dans une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="fbf9c-115">Cette variable d’environnement peut être récupérée à l’aide de `ERRORLEVEL` dans un fichier de commandes ou de `$LastExitCode` dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="fbf9c-116">Vous pouvez générer l’application à l’aide de la commande [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="fbf9c-117">Ensuite, créez un script PowerShell pour exécuter l’application et afficher le résultat.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="fbf9c-118">Collez le code suivant dans un fichier texte et enregistrez-le sous `test.ps1` dans le dossier qui contient le projet.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="fbf9c-119">Exécutez le script PowerShell en tapant `test.ps1` à l’invite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="fbf9c-120">Comme le code retourne zéro, le fichier de commandes indique la réussite.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="fbf9c-121">Toutefois, si vous modifiez MainReturnValTest.cs pour retourner une valeur différente de zéro, puis recompilez le programme, l’exécution suivante du script PowerShell signalera un échec.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-121">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="fbf9c-122">Exemple de sortie</span><span class="sxs-lookup"><span data-stu-id="fbf9c-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="fbf9c-123">Valeurs de retour d’Async Main</span><span class="sxs-lookup"><span data-stu-id="fbf9c-123">Async Main return values</span></span>

<span data-ttu-id="fbf9c-124">Les valeurs de retour d’Async Main déplacent le code réutilisable nécessaire pour appeler les méthodes asynchrones dans `Main` vers le code généré par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="fbf9c-125">Avant, vous auriez dû écrire cette construction pour appeler du code asynchrone et vérifier que votre programme s’est exécuté jusqu’à la fin de l’opération asynchrone :</span><span class="sxs-lookup"><span data-stu-id="fbf9c-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="fbf9c-126">Maintenant, vous pouvez la remplacer par :</span><span class="sxs-lookup"><span data-stu-id="fbf9c-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="fbf9c-127">L’avantage de la nouvelle syntaxe est que le compilateur génère toujours un code correct.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="fbf9c-128">Code généré par le compilateur</span><span class="sxs-lookup"><span data-stu-id="fbf9c-128">Compiler-generated code</span></span>

<span data-ttu-id="fbf9c-129">Quand le point d’entrée de l’application retourne `Task` ou `Task<int>`, le compilateur génère un nouveau point d’entrée qui appelle la méthode de point d’entrée déclarée dans le code d’application.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="fbf9c-130">En supposant que ce point d’entrée est appelé `$GeneratedMain`, le compilateur génère le code suivant pour ces points d’entrée :</span><span class="sxs-lookup"><span data-stu-id="fbf9c-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="fbf9c-131">`static Task Main()` permet au compilateur d’émettre l’équivalent de `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="fbf9c-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="fbf9c-132">`static Task Main(string[])` permet au compilateur d’émettre l’équivalent de `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="fbf9c-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="fbf9c-133">`static Task<int> Main()` permet au compilateur d’émettre l’équivalent de `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="fbf9c-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="fbf9c-134">`static Task<int> Main(string[])` permet au compilateur d’émettre l’équivalent de `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="fbf9c-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="fbf9c-135">Si les exemples ont utilisé le modificateur `async` sur la méthode `Main`, le compilateur génère le même code.</span><span class="sxs-lookup"><span data-stu-id="fbf9c-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbf9c-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbf9c-136">See also</span></span>

- [<span data-ttu-id="fbf9c-137">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fbf9c-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fbf9c-138">Référence C#</span><span class="sxs-lookup"><span data-stu-id="fbf9c-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fbf9c-139">Main () et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="fbf9c-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="fbf9c-140">Comment afficher les arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="fbf9c-140">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
