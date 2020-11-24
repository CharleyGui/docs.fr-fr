---
title: Référence de F# Interactive (dotnet)
description: 'Découvrez comment F# Interactive (dotnet FSI) est utilisé pour exécuter le code F # de manière interactive sur la console ou pour exécuter des scripts F #.'
ms.date: 10/31/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: b535cb03d76909043ca192ed5a9d2078f9343795
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099476"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="e88fb-103">Programmation interactive avec F\#</span><span class="sxs-lookup"><span data-stu-id="e88fb-103">Interactive programming with F\#</span></span>

<span data-ttu-id="e88fb-104">F# Interactive (dotnet FSI) est utilisé pour exécuter le code F # de manière interactive sur la console ou pour exécuter des scripts F #.</span><span class="sxs-lookup"><span data-stu-id="e88fb-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="e88fb-105">En d'autres termes, F# interactive exécute un REPL (Read, Evaluate, Print Loop) pour le langage F#.</span><span class="sxs-lookup"><span data-stu-id="e88fb-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="e88fb-106">Pour exécuter F# Interactive à partir de la console, exécutez `dotnet fsi` .</span><span class="sxs-lookup"><span data-stu-id="e88fb-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="e88fb-107">Vous y trouverez `dotnet fsi` tous les kits de développement logiciel (SDK) .net.</span><span class="sxs-lookup"><span data-stu-id="e88fb-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="e88fb-108">Pour plus d’informations sur les options de ligne de commande disponibles, consultez [options de F# Interactive](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="e88fb-108">For information about available command-line options, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

## <a name="executing-code-directly-in-f-interactive"></a><span data-ttu-id="e88fb-109">Exécution de code directement dans F# Interactive</span><span class="sxs-lookup"><span data-stu-id="e88fb-109">Executing code directly in F# Interactive</span></span>

<span data-ttu-id="e88fb-110">Étant donné que F# Interactive est une boucle REPL (lecture-eval-Print), vous pouvez exécuter le code de manière interactive dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="e88fb-110">Because F# Interactive is a REPL (read-eval-print loop), you can execute code interactively in it.</span></span> <span data-ttu-id="e88fb-111">Voici un exemple de session interactive après `dotnet fsi` l’exécution à partir de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="e88fb-111">Here is an example of an interactive session after executing `dotnet fsi` from the command line:</span></span>

```console
Microsoft (R) F# Interactive version 11.0.0.0 for F# 5.0
Copyright (c) Microsoft Corporation. All Rights Reserved.

For help type #help;;

> let square x = x *  x;;
val square : x:int -> int

> square 12;;
val it : int = 144

> printfn "Hello, FSI!"
- ;;
Hello, FSI!
val it : unit = ()
```

<span data-ttu-id="e88fb-112">Vous remarquerez deux choses principales :</span><span class="sxs-lookup"><span data-stu-id="e88fb-112">You'll notice two main things:</span></span>

1. <span data-ttu-id="e88fb-113">Tout le code doit se terminer par un double point-virgule ( `;;` ) à évaluer</span><span class="sxs-lookup"><span data-stu-id="e88fb-113">All code must be terminated with a double semicolon (`;;`) to be evaluated</span></span>
2. <span data-ttu-id="e88fb-114">Le code est évalué et stocké dans une `it` valeur.</span><span class="sxs-lookup"><span data-stu-id="e88fb-114">Code is evaluated and stored in an `it` value.</span></span> <span data-ttu-id="e88fb-115">Vous pouvez référencer de `it` manière interactive.</span><span class="sxs-lookup"><span data-stu-id="e88fb-115">You can reference `it` interactively.</span></span>

<span data-ttu-id="e88fb-116">F# Interactive prend également en charge l’entrée multiligne.</span><span class="sxs-lookup"><span data-stu-id="e88fb-116">F# Interactive also supports multi-line input.</span></span> <span data-ttu-id="e88fb-117">Vous devez simplement mettre fin à la soumission avec un double point-virgule ( `;;` ).</span><span class="sxs-lookup"><span data-stu-id="e88fb-117">You just need to terminate your submission with a double semicolon (`;;`).</span></span> <span data-ttu-id="e88fb-118">Examinez l’extrait de code suivant qui a été collé dans et évalué par F# Interactive :</span><span class="sxs-lookup"><span data-stu-id="e88fb-118">Consider the following snippet that has been pasted into and evaluated by F# Interactive:</span></span>

```console
> let getOddSquares xs =
-     xs
-     |> List.filter (fun x -> x % 2 <> 0)
-     |> List.map (fun x -> x * x)
-
- printfn "%A" (getOddSquares [1..10]);;
[1; 9; 25; 49; 81]
val getOddSquares : xs:int list -> int list
val it : unit = ()

>
```

<span data-ttu-id="e88fb-119">La mise en forme du code est préservée et un double point-virgule ( `;;` ) termine l’entrée.</span><span class="sxs-lookup"><span data-stu-id="e88fb-119">The code's formatting is preserved, and there is a double semicolon (`;;`) terminating the input.</span></span> <span data-ttu-id="e88fb-120">F# Interactive ensuite évalué le code et imprimé les résultats !</span><span class="sxs-lookup"><span data-stu-id="e88fb-120">F# Interactive then evaluated the code and printed the results!</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="e88fb-121">Écriture de scripts avec F\#</span><span class="sxs-lookup"><span data-stu-id="e88fb-121">Scripting with F\#</span></span>

<span data-ttu-id="e88fb-122">L’évaluation interactive du code dans F# Interactive peut être un excellent outil d’apprentissage, mais vous découvrirez rapidement qu’il n’est pas aussi productif que d’écrire du code dans un éditeur normal.</span><span class="sxs-lookup"><span data-stu-id="e88fb-122">Evaluating code interactively in F# Interactive can be a great learning tool, but you'll quickly find that it's not as productive as writing code in a normal editor.</span></span> <span data-ttu-id="e88fb-123">Pour prendre en charge la modification de code normale, vous pouvez écrire des scripts F #.</span><span class="sxs-lookup"><span data-stu-id="e88fb-123">To support normal code editing, you can write F# scripts.</span></span>

<span data-ttu-id="e88fb-124">Les scripts utilisent l’extension de fichier **. FSX**.</span><span class="sxs-lookup"><span data-stu-id="e88fb-124">Scripts use the file extension **.fsx**.</span></span> <span data-ttu-id="e88fb-125">Au lieu de compiler le code source puis d’exécuter l’assembly compilé, vous pouvez simplement exécuter **dotnet FSI** et spécifier le nom de fichier du script du code source f #, et F # Interactive lit le code et l’exécute en temps réel.</span><span class="sxs-lookup"><span data-stu-id="e88fb-125">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span> <span data-ttu-id="e88fb-126">Par exemple, considérez le script suivant appelé `Script.fsx` :</span><span class="sxs-lookup"><span data-stu-id="e88fb-126">For example, consider the following script called `Script.fsx`:</span></span>

```fsharp
let getOddSquares xs =
    xs
    |> List.filter (fun x -> x % 2 <> 0)
    |> List.map (fun x -> x * x)

printfn "%A" (getOddSquares [1..10])
```

<span data-ttu-id="e88fb-127">Lorsque ce fichier est créé sur votre ordinateur, vous pouvez l’exécuter avec `dotnet fsi` et voir la sortie directement dans la fenêtre de votre terminal :</span><span class="sxs-lookup"><span data-stu-id="e88fb-127">When this file is created in your machine, you can run it with `dotnet fsi` and see the output directly in your terminal window:</span></span>

```console
dotnet fsi Script.fsx
[1; 9; 25; 49; 81]
```

<span data-ttu-id="e88fb-128">Les scripts F # sont pris en charge en mode natif dans [Visual Studio](../../get-started/get-started-visual-studio.md), [Visual Studio code](../../get-started/get-started-vscode.md)et [Visual Studio pour Mac](../../get-started/get-started-with-visual-studio-for-mac.md).</span><span class="sxs-lookup"><span data-stu-id="e88fb-128">F# scripting is natively supported in [Visual Studio](../../get-started/get-started-visual-studio.md), [Visual Studio Code](../../get-started/get-started-vscode.md), and [Visual Studio for Mac](../../get-started/get-started-with-visual-studio-for-mac.md).</span></span>

## <a name="referencing-packages-in-f-interactive"></a><span data-ttu-id="e88fb-129">Référencement de packages dans F# Interactive</span><span class="sxs-lookup"><span data-stu-id="e88fb-129">Referencing packages in F# Interactive</span></span>

<span data-ttu-id="e88fb-130">F# Interactive prend en charge le référencement de packages NuGet avec la `#r "nuget:"` syntaxe et une version facultative :</span><span class="sxs-lookup"><span data-stu-id="e88fb-130">F# Interactive supports referencing NuGet packages with the `#r "nuget:"` syntax and an optional version:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"
open Newtonsoft.Json

let data = {| Name = "Don Syme"; Occupation = "F# Creator" |}
JsonConvert.SerializeObject(data)
```

<span data-ttu-id="e88fb-131">Si aucune version n’est spécifiée, le package non préliminaire disponible le plus élevé est pris.</span><span class="sxs-lookup"><span data-stu-id="e88fb-131">If a version is not specified, the highest available non-preview package is taken.</span></span> <span data-ttu-id="e88fb-132">Pour référencer une version spécifique, introduisez la version à l’aide d’une virgule.</span><span class="sxs-lookup"><span data-stu-id="e88fb-132">To reference a specific version, introduce the version via a comma.</span></span> <span data-ttu-id="e88fb-133">Cela peut être pratique lorsque vous référencez une version préliminaire d’un package.</span><span class="sxs-lookup"><span data-stu-id="e88fb-133">This can be handy when referencing a preview version of a package.</span></span> <span data-ttu-id="e88fb-134">Par exemple, considérez ce script en utilisant une version préliminaire de [DiffSharp](https://diffsharp.github.io/):</span><span class="sxs-lookup"><span data-stu-id="e88fb-134">For example, consider this script using a preview version of [DiffSharp](https://diffsharp.github.io/):</span></span>

```fsharp
#r "nuget: DiffSharp-lite, 1.0.0-preview-328097867"
open DiffSharp

// A 1D tensor
let t1 = dsharp.tensor [ 0.0 .. 0.2 .. 1.0 ]

// A 2x2 tensor
let t2 = dsharp.tensor [ [ 0; 1 ]; [ 2; 2 ] ]

// Define a scalar-to-scalar function
let f (x: Tensor) = sin (sqrt x)

printfn "%A" (f (dsharp.tensor 1.2))
```

<span data-ttu-id="e88fb-135">Vous pouvez spécifier autant de références de package que vous le souhaitez dans un script.</span><span class="sxs-lookup"><span data-stu-id="e88fb-135">You can specify as many package references as you like in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="e88fb-136">Il existe actuellement une limitation pour les scripts qui utilisent des références d’infrastructure (par exemple `Microsoft.NET.Sdk.Web`  `Microsoft.NET.Sdk.WindowsDesktop` , ou).</span><span class="sxs-lookup"><span data-stu-id="e88fb-136">There's currently a limitation for scripts that use framework references (e.g.`Microsoft.NET.Sdk.Web` or  `Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="e88fb-137">Les packages comme Saturn, Giraffe, WinForms ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="e88fb-137">Packages like Saturn, Giraffe, WinForms are not available.</span></span> <span data-ttu-id="e88fb-138">Cela est suivi dans le [#9417](https://github.com/dotnet/fsharp/issues/9417)du problème.</span><span class="sxs-lookup"><span data-stu-id="e88fb-138">This is being tracked in issue [#9417](https://github.com/dotnet/fsharp/issues/9417).</span></span>

## <a name="referencing-assemblies-on-disk-with-f-interactive"></a><span data-ttu-id="e88fb-139">Référencement d’assemblys sur un disque avec F # Interactive</span><span class="sxs-lookup"><span data-stu-id="e88fb-139">Referencing assemblies on disk with F# interactive</span></span>

<span data-ttu-id="e88fb-140">Sinon, si vous disposez d’un assembly sur le disque et que vous souhaitez le référencer dans un script, vous pouvez utiliser la `#r` syntaxe pour spécifier un assembly.</span><span class="sxs-lookup"><span data-stu-id="e88fb-140">Alternatively, if you have an assembly on disk and wish to reference that in a script, you can use the `#r` syntax to specify an assembly.</span></span> <span data-ttu-id="e88fb-141">Examinez le code suivant dans un projet compilé dans `MyAssembly.dll` :</span><span class="sxs-lookup"><span data-stu-id="e88fb-141">Consider the following code in a project compiled into `MyAssembly.dll`:</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

<span data-ttu-id="e88fb-142">Une fois compilé, vous pouvez le référencer dans un fichier appelé, par `Script.fsx` exemple :</span><span class="sxs-lookup"><span data-stu-id="e88fb-142">One compiled, you can reference it in a file called `Script.fsx` like so:</span></span>

```fsharp
#r "path/to/MyAssembly.dll"

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="e88fb-143">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="e88fb-143">The output is as follows:</span></span>

```console
dotnet fsi Script.fsx
90
```

<span data-ttu-id="e88fb-144">Vous pouvez spécifier autant de références d’assembly que vous le souhaitez dans un script.</span><span class="sxs-lookup"><span data-stu-id="e88fb-144">You can specify as many assembly references as you like in a script.</span></span>

## <a name="loading-other-scripts"></a><span data-ttu-id="e88fb-145">Chargement d’autres scripts</span><span class="sxs-lookup"><span data-stu-id="e88fb-145">Loading other scripts</span></span>

<span data-ttu-id="e88fb-146">Lors de l’écriture de scripts, il peut souvent être utile d’utiliser différents scripts pour différentes tâches.</span><span class="sxs-lookup"><span data-stu-id="e88fb-146">When scripting, it can often be helpful to use different scripts for different tasks.</span></span> <span data-ttu-id="e88fb-147">Il peut arriver que vous souhaitiez réutiliser du code à partir d’un script dans un autre.</span><span class="sxs-lookup"><span data-stu-id="e88fb-147">Sometimes you may want to reuse code from on script in another.</span></span> <span data-ttu-id="e88fb-148">Au lieu de copier-coller son contenu dans votre fichier, vous pouvez le charger et l’évaluer facilement avec `#load` .</span><span class="sxs-lookup"><span data-stu-id="e88fb-148">Rather than copy-pasting its contents into your file, you can simple load and evaluate it with `#load`.</span></span>

<span data-ttu-id="e88fb-149">Tenez compte des points suivants `Script1.fsx` :</span><span class="sxs-lookup"><span data-stu-id="e88fb-149">Consider the following `Script1.fsx`:</span></span>

```fsharp
let square x = x * x
```

<span data-ttu-id="e88fb-150">Et le fichier de consommation `Script2.fsx` :</span><span class="sxs-lookup"><span data-stu-id="e88fb-150">And the consuming file, `Script2.fsx`:</span></span>

```fsharp
#load "Script1.fsx"
open Script1

printfn "%d" (square 12)
```

<span data-ttu-id="e88fb-151">Notez que la `open Script1` déclaration est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e88fb-151">Note that the `open Script1` declaration is required.</span></span> <span data-ttu-id="e88fb-152">Cela est dû au fait que les constructions dans un script F # sont compilées dans un module de niveau supérieur qui est le nom du fichier de script dans lequel elle se trouve.</span><span class="sxs-lookup"><span data-stu-id="e88fb-152">This is because constructs in an F# script are compiled into a top-level module that is the name of the script file it is in.</span></span>

<span data-ttu-id="e88fb-153">Vous pouvez évaluer `Script2.fsx` comme suit :</span><span class="sxs-lookup"><span data-stu-id="e88fb-153">You can evaluate `Script2.fsx` like so:</span></span>

```console
dotnet fsi Script2.fsx
144
```

<span data-ttu-id="e88fb-154">Vous pouvez spécifier autant `#load` de directives que vous le souhaitez dans un script.</span><span class="sxs-lookup"><span data-stu-id="e88fb-154">You can specify as many `#load` directives as you like in a script.</span></span>

## <a name="using-the-fsi-object-in-f-code"></a><span data-ttu-id="e88fb-155">Utilisation `fsi` de l’objet dans le code F #</span><span class="sxs-lookup"><span data-stu-id="e88fb-155">Using the `fsi` object in F# code</span></span>

<span data-ttu-id="e88fb-156">Les scripts F # ont accès à un `fsi` objet personnalisé qui représente la session F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="e88fb-156">F# scripts have access to a custom `fsi` object that represents the F# Interactive session.</span></span> <span data-ttu-id="e88fb-157">Elle vous permet de personnaliser des éléments tels que la mise en forme de la sortie.</span><span class="sxs-lookup"><span data-stu-id="e88fb-157">It allows you to customize things like output formatting.</span></span> <span data-ttu-id="e88fb-158">C’est également la manière dont vous pouvez accéder aux arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e88fb-158">It is also how you can access command-line arguments.</span></span>

<span data-ttu-id="e88fb-159">L’exemple suivant montre comment récupérer et utiliser des arguments de ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="e88fb-159">The following example shows how to get and use command-line arguments:</span></span>

```fsharp
let args = fsi.CommandLineArgs

for arg in args do
    printfn "%s" arg
```

<span data-ttu-id="e88fb-160">Lorsqu’elle est évaluée, elle imprime tous les arguments.</span><span class="sxs-lookup"><span data-stu-id="e88fb-160">When evaluated, it prints all arguments.</span></span> <span data-ttu-id="e88fb-161">Le premier argument est toujours le nom du script évalué :</span><span class="sxs-lookup"><span data-stu-id="e88fb-161">The first argument is always the name of the script that is evaluated:</span></span>

```dotnet
dotnet fsi Script1.fsx hello world from fsi
Script1.fsx
hello
world
from
fsi
```

<span data-ttu-id="e88fb-162">Vous pouvez également utiliser `System.Environment.GetCommandLineArgs()` pour accéder aux mêmes arguments.</span><span class="sxs-lookup"><span data-stu-id="e88fb-162">You can also use `System.Environment.GetCommandLineArgs()` to access the same arguments.</span></span>

## <a name="f-interactive-directive-reference"></a><span data-ttu-id="e88fb-163">Informations de référence sur la directive F# Interactive</span><span class="sxs-lookup"><span data-stu-id="e88fb-163">F# Interactive directive reference</span></span>

<span data-ttu-id="e88fb-164">Les `#r` `#load` directives et présentées précédemment sont uniquement disponibles dans F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="e88fb-164">The `#r` and `#load` directives seen previously are only available in F# Interactive.</span></span> <span data-ttu-id="e88fb-165">Plusieurs directives sont uniquement disponibles dans F# Interactive :</span><span class="sxs-lookup"><span data-stu-id="e88fb-165">There are several directives only available in F# Interactive:</span></span>

|<span data-ttu-id="e88fb-166">Directive</span><span class="sxs-lookup"><span data-stu-id="e88fb-166">Directive</span></span>|<span data-ttu-id="e88fb-167">Description</span><span class="sxs-lookup"><span data-stu-id="e88fb-167">Description</span></span>|
|---------|-----------|
|`#r "nuget:..."`|<span data-ttu-id="e88fb-168">Fait référence à un package à partir de NuGet</span><span class="sxs-lookup"><span data-stu-id="e88fb-168">References a package from NuGet</span></span>|
|`#r "assembly-name.dll"`|<span data-ttu-id="e88fb-169">Référence un assembly sur le disque</span><span class="sxs-lookup"><span data-stu-id="e88fb-169">References an assembly on disk</span></span>|
|`#load "file-name.fsx"`|<span data-ttu-id="e88fb-170">Lit un fichier source, le compile et l'exécute.</span><span class="sxs-lookup"><span data-stu-id="e88fb-170">Reads a source file, compiles it, and runs it.</span></span>|
|`#help`|<span data-ttu-id="e88fb-171">Affiche des informations sur les directives disponibles.</span><span class="sxs-lookup"><span data-stu-id="e88fb-171">Displays information about available directives.</span></span>|
|`#I`|<span data-ttu-id="e88fb-172">Spécifie un chemin de recherche des assemblys entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="e88fb-172">Specifies an assembly search path in quotation marks.</span></span>|
|`#quit`|<span data-ttu-id="e88fb-173">Met fin à une session de F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="e88fb-173">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="e88fb-174">`#time "on"` ou `#time "off"`</span><span class="sxs-lookup"><span data-stu-id="e88fb-174">`#time "on"` or `#time "off"`</span></span>|<span data-ttu-id="e88fb-175">Par lui-même, `#time` active ou désactive l’affichage des informations de performances.</span><span class="sxs-lookup"><span data-stu-id="e88fb-175">By itself, `#time` toggles whether to display performance information.</span></span> <span data-ttu-id="e88fb-176">Quand c’est le cas `"on"` , F# Interactive mesure le temps réel, le temps processeur et les informations garbage collection pour chaque section de code qui est interprétée et exécutée.</span><span class="sxs-lookup"><span data-stu-id="e88fb-176">When it is `"on"`, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="e88fb-177">Lorsque vous spécifiez des fichiers ou des chemins d'accès dans F# Interactive, un littéral de chaîne est attendu.</span><span class="sxs-lookup"><span data-stu-id="e88fb-177">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="e88fb-178">Par conséquent, les fichiers et les chemins d'accès doivent être entre guillemets, et les caractères d'échappement habituels s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="e88fb-178">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="e88fb-179">Vous pouvez utiliser le `@` caractère pour que F# Interactive interprète une chaîne qui contient un chemin d’accès comme chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="e88fb-179">You can use the `@` character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="e88fb-180">Dans ce cas, F# Interactive ignore les caractères d'échappement.</span><span class="sxs-lookup"><span data-stu-id="e88fb-180">This causes F# Interactive to ignore any escape characters.</span></span>

## <a name="interactive-and-compiled-preprocessor-directives"></a><span data-ttu-id="e88fb-181">Directives de préprocesseurs interactives et compilées</span><span class="sxs-lookup"><span data-stu-id="e88fb-181">Interactive and compiled preprocessor directives</span></span>

<span data-ttu-id="e88fb-182">Quand vous compilez du code dans F# Interactive, que vous exécutez de manière interactive ou que vous exécutiez un script, le symbole **interactif** est défini.</span><span class="sxs-lookup"><span data-stu-id="e88fb-182">When you compile code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="e88fb-183">Quand vous compilez du code dans le compilateur, le symbole **compilé** est défini.</span><span class="sxs-lookup"><span data-stu-id="e88fb-183">When you compile code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="e88fb-184">Par conséquent, si le code doit être différent dans les modes compilé et interactif, vous pouvez utiliser ces directives de préprocesseur pour la compilation conditionnelle afin de déterminer laquelle utiliser.</span><span class="sxs-lookup"><span data-stu-id="e88fb-184">Thus, if code needs to be different in compiled and interactive modes, you can use these preprocessor directives for conditional compilation to determine which to use.</span></span> <span data-ttu-id="e88fb-185">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e88fb-185">For example:</span></span>

```fsharp
#if INTERACTIVE
// Some code that executes only in FSI
// ...
#endif
```

## <a name="using-f-interactive-in-visual-studio"></a><span data-ttu-id="e88fb-186">Utilisation de F# Interactive dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e88fb-186">Using F# Interactive in Visual Studio</span></span>

<span data-ttu-id="e88fb-187">Pour exécuter F# Interactive par l’intermédiaire de Visual Studio, vous pouvez cliquer sur le bouton de barre d’outils approprié intitulé **F# Interactive** ou utiliser les touches **Ctrl+Alt+F**.</span><span class="sxs-lookup"><span data-stu-id="e88fb-187">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="e88fb-188">La fenêtre interactive, fenêtre Outil exécutant une session F# Interactive, s'affiche.</span><span class="sxs-lookup"><span data-stu-id="e88fb-188">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="e88fb-189">Vous pouvez également sélectionner du code que vous souhaitez exécuter dans la fenêtre interactive et appuyer sur la combinaison de touches **Alt + Entrée**.</span><span class="sxs-lookup"><span data-stu-id="e88fb-189">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="e88fb-190">F# Interactive démarre dans une fenêtre Outil nommée **F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="e88fb-190">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="e88fb-191">Lorsque vous utilisez cette combinaison de touches, assurez-vous que la fenêtre de l'éditeur a le focus.</span><span class="sxs-lookup"><span data-stu-id="e88fb-191">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="e88fb-192">Que vous utilisiez la console ou Visual Studio, une invite de commandes apparaît et l'interpréteur attend votre entrée.</span><span class="sxs-lookup"><span data-stu-id="e88fb-192">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="e88fb-193">Vous pouvez saisir le code comme vous le feriez dans un fichier de code.</span><span class="sxs-lookup"><span data-stu-id="e88fb-193">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="e88fb-194">Pour compiler et exécuter le code, entrez deux points-virgules (**;;**) pour terminer une ligne ou plusieurs lignes d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e88fb-194">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="e88fb-195">F# Interactive tente de compiler le code et, en cas de réussite, exécute le code et imprime la signature des types et des valeurs qu'il a compilés.</span><span class="sxs-lookup"><span data-stu-id="e88fb-195">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="e88fb-196">Si des erreurs se produisent, l'interpréteur imprime les messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e88fb-196">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="e88fb-197">Le code entré dans la même session ayant accès à toutes les constructions entrées précédemment, vous pouvez développer des programmes.</span><span class="sxs-lookup"><span data-stu-id="e88fb-197">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="e88fb-198">Une mémoire tampon étendue de la fenêtre Outil vous permet de copier le code dans un fichier si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e88fb-198">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="e88fb-199">Comme lors de l'exécution dans Visual Studio, F# Interactive s'exécute indépendamment de votre projet, vous ne pouvez pas, par exemple, utiliser les constructions définies dans votre projet F# Interactive, sauf si vous copiez le code de la fonction dans la fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="e88fb-199">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="e88fb-200">Vous pouvez contrôler les F# Interactive arguments de ligne de commande (options) en ajustant les paramètres.</span><span class="sxs-lookup"><span data-stu-id="e88fb-200">You can control the F# Interactive command-line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="e88fb-201">Dans le menu **Outils**, sélectionnez **Options**, puis développez **Outils F#**.</span><span class="sxs-lookup"><span data-stu-id="e88fb-201">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="e88fb-202">Les deux paramètres que vous pouvez changer sont les options F# Interactive et le paramètre **F# Interactive 64 bits**, qui n’est pertinent que si vous exécutez F# Interactive sur un ordinateur 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e88fb-202">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="e88fb-203">Ce paramètre détermine si vous souhaitez exécuter la version 64 bits dédiée de **fsi.exe** ou **fsianycpu.exe**, qui utilise l’architecture de l’ordinateur pour déterminer s’il doit s’exécuter en tant que processus 32 bits ou 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e88fb-203">This setting determines whether you want to run the dedicated 64-bit version of **fsi.exe** or **fsianycpu.exe**, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="related-articles"></a><span data-ttu-id="e88fb-204">Articles connexes</span><span class="sxs-lookup"><span data-stu-id="e88fb-204">Related articles</span></span>

|<span data-ttu-id="e88fb-205">Titre</span><span class="sxs-lookup"><span data-stu-id="e88fb-205">Title</span></span>|<span data-ttu-id="e88fb-206">Description</span><span class="sxs-lookup"><span data-stu-id="e88fb-206">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="e88fb-207">Options F# Interactive</span><span class="sxs-lookup"><span data-stu-id="e88fb-207">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="e88fb-208">Décrit la syntaxe et les options de ligne de commande pour le F# Interactive, fsi.exe.</span><span class="sxs-lookup"><span data-stu-id="e88fb-208">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|