---
title: Référence de F# Interactive (dotnet)
description: 'Découvrez comment F# Interactive (dotnet FSI) est utilisé pour exécuter le code F # de manière interactive sur la console ou pour exécuter des scripts F #.'
ms.date: 08/20/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: b1020d8ab8f2282c792fb5d00656b6d43c2c6610
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064117"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="57817-103">Programmation interactive avec F\#</span><span class="sxs-lookup"><span data-stu-id="57817-103">Interactive programming with F\#</span></span>

<span data-ttu-id="57817-104">F# Interactive (dotnet FSI) est utilisé pour exécuter le code F # de manière interactive sur la console ou pour exécuter des scripts F #.</span><span class="sxs-lookup"><span data-stu-id="57817-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="57817-105">En d'autres termes, F# interactive exécute un REPL (Read, Evaluate, Print Loop) pour le langage F#.</span><span class="sxs-lookup"><span data-stu-id="57817-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="57817-106">Pour exécuter F# Interactive à partir de la console, exécutez `dotnet fsi` .</span><span class="sxs-lookup"><span data-stu-id="57817-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="57817-107">Vous y trouverez `dotnet fsi` tous les kits de développement logiciel (SDK) .net.</span><span class="sxs-lookup"><span data-stu-id="57817-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="57817-108">Pour plus d’informations sur les options de ligne de commande disponibles, consultez [Options de F# Interactive](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="57817-108">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="57817-109">Pour exécuter F# Interactive par l’intermédiaire de Visual Studio, vous pouvez cliquer sur le bouton de barre d’outils approprié intitulé **F# Interactive** ou utiliser les touches **Ctrl+Alt+F** .</span><span class="sxs-lookup"><span data-stu-id="57817-109">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive** , or use the keys **Ctrl+Alt+F** .</span></span> <span data-ttu-id="57817-110">La fenêtre interactive, fenêtre Outil exécutant une session F# Interactive, s'affiche.</span><span class="sxs-lookup"><span data-stu-id="57817-110">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="57817-111">Vous pouvez également sélectionner du code que vous souhaitez exécuter dans la fenêtre interactive et appuyer sur la combinaison de touches **Alt + Entrée** .</span><span class="sxs-lookup"><span data-stu-id="57817-111">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter** .</span></span> <span data-ttu-id="57817-112">F# Interactive démarre dans une fenêtre Outil nommée **F# Interactive** .</span><span class="sxs-lookup"><span data-stu-id="57817-112">F# Interactive starts in a tool window labeled **F# Interactive** .</span></span> <span data-ttu-id="57817-113">Lorsque vous utilisez cette combinaison de touches, assurez-vous que la fenêtre de l'éditeur a le focus.</span><span class="sxs-lookup"><span data-stu-id="57817-113">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="57817-114">Que vous utilisiez la console ou Visual Studio, une invite de commandes apparaît et l'interpréteur attend votre entrée.</span><span class="sxs-lookup"><span data-stu-id="57817-114">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="57817-115">Vous pouvez saisir le code comme vous le feriez dans un fichier de code.</span><span class="sxs-lookup"><span data-stu-id="57817-115">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="57817-116">Pour compiler et exécuter le code, entrez deux points-virgules ( **;;** ) pour terminer une ligne ou plusieurs lignes d’entrée.</span><span class="sxs-lookup"><span data-stu-id="57817-116">To compile and execute the code, enter two semicolons ( **;;** ) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="57817-117">F# Interactive tente de compiler le code et, en cas de réussite, exécute le code et imprime la signature des types et des valeurs qu'il a compilés.</span><span class="sxs-lookup"><span data-stu-id="57817-117">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="57817-118">Si des erreurs se produisent, l'interpréteur imprime les messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="57817-118">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="57817-119">Le code entré dans la même session ayant accès à toutes les constructions entrées précédemment, vous pouvez développer des programmes.</span><span class="sxs-lookup"><span data-stu-id="57817-119">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="57817-120">Une mémoire tampon étendue de la fenêtre Outil vous permet de copier le code dans un fichier si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="57817-120">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="57817-121">Comme lors de l'exécution dans Visual Studio, F# Interactive s'exécute indépendamment de votre projet, vous ne pouvez pas, par exemple, utiliser les constructions définies dans votre projet F# Interactive, sauf si vous copiez le code de la fonction dans la fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="57817-121">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="57817-122">Si vous avez un projet ouvert qui fait référence à des bibliothèques, vous pouvez référencer celles-ci dans F# Interactive par l’intermédiaire de l’ **Explorateur de solutions** .</span><span class="sxs-lookup"><span data-stu-id="57817-122">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer** .</span></span> <span data-ttu-id="57817-123">Pour référencer une bibliothèque dans F# Interactive, développez le nœud **Références** , ouvrez le menu contextuel de la bibliothèque et choisissez **Envoyer à F# Interactive** .</span><span class="sxs-lookup"><span data-stu-id="57817-123">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive** .</span></span>

<span data-ttu-id="57817-124">Vous pouvez contrôler les arguments de ligne de commande F# Interactive (options) en réglant les paramètres.</span><span class="sxs-lookup"><span data-stu-id="57817-124">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="57817-125">Dans le menu **Outils** , sélectionnez **Options** , puis développez **Outils F#** .</span><span class="sxs-lookup"><span data-stu-id="57817-125">On the **Tools** menu, select **Options...** , and then expand **F# Tools** .</span></span> <span data-ttu-id="57817-126">Les deux paramètres que vous pouvez changer sont les options F# Interactive et le paramètre **F# Interactive 64 bits** , qui n’est pertinent que si vous exécutez F# Interactive sur un ordinateur 64 bits.</span><span class="sxs-lookup"><span data-stu-id="57817-126">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="57817-127">Ce paramètre détermine si vous souhaitez exécuter la version 64 bits dédiée de fsi.exe ou fsianycpu.exe, qui utilise l'architecture de l'ordinateur pour déterminer s'il doit s'exécuter comme processus 32 bits ou 64 bits.</span><span class="sxs-lookup"><span data-stu-id="57817-127">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="57817-128">Écriture de scripts avec F\#</span><span class="sxs-lookup"><span data-stu-id="57817-128">Scripting with F\#</span></span>

<span data-ttu-id="57817-129">Les scripts utilisent l’extension de fichier **.fsx** ou **.fsscript** .</span><span class="sxs-lookup"><span data-stu-id="57817-129">Scripts use the file extension **.fsx** or **.fsscript** .</span></span> <span data-ttu-id="57817-130">Au lieu de compiler le code source puis d’exécuter l’assembly compilé, vous pouvez simplement exécuter **dotnet FSI** et spécifier le nom de fichier du script du code source f #, et F # Interactive lit le code et l’exécute en temps réel.</span><span class="sxs-lookup"><span data-stu-id="57817-130">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="57817-131">Différences entre les environnements interactifs, de script et compilés</span><span class="sxs-lookup"><span data-stu-id="57817-131">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="57817-132">Quand vous compilez du code en F# Interactive, que vous l’exécutiez interactivement ou exécutiez un script, le symbole **INTERACTIVE** est défini.</span><span class="sxs-lookup"><span data-stu-id="57817-132">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="57817-133">Quand vous compilez le code dans le compilateur, le symbole **COMPILED** est défini.</span><span class="sxs-lookup"><span data-stu-id="57817-133">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="57817-134">Par conséquent, si le code doit être différent dans les modes compilé et interactif, vous pouvez utiliser les directives du préprocesseur pour qu'une compilation conditionnelle déterminer quel code utiliser.</span><span class="sxs-lookup"><span data-stu-id="57817-134">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="57817-135">Certaines directives sont disponibles lorsque vous exécutez des scripts en F# Interactive qui ne sont pas disponibles lorsque vous exécutez le compilateur.</span><span class="sxs-lookup"><span data-stu-id="57817-135">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="57817-136">Le tableau suivant résume les directives qui sont disponibles lorsque vous utilisez F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="57817-136">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="57817-137">Directive</span><span class="sxs-lookup"><span data-stu-id="57817-137">Directive</span></span>|<span data-ttu-id="57817-138">Description</span><span class="sxs-lookup"><span data-stu-id="57817-138">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="57817-139">**#help**</span><span class="sxs-lookup"><span data-stu-id="57817-139">**#help**</span></span>|<span data-ttu-id="57817-140">Affiche des informations sur les directives disponibles.</span><span class="sxs-lookup"><span data-stu-id="57817-140">Displays information about available directives.</span></span>|
|<span data-ttu-id="57817-141">**#I**</span><span class="sxs-lookup"><span data-stu-id="57817-141">**#I**</span></span>|<span data-ttu-id="57817-142">Spécifie un chemin de recherche des assemblys entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="57817-142">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="57817-143">**#load**</span><span class="sxs-lookup"><span data-stu-id="57817-143">**#load**</span></span>|<span data-ttu-id="57817-144">Lit un fichier source, le compile et l'exécute.</span><span class="sxs-lookup"><span data-stu-id="57817-144">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="57817-145">**#quit**</span><span class="sxs-lookup"><span data-stu-id="57817-145">**#quit**</span></span>|<span data-ttu-id="57817-146">Met fin à une session de F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="57817-146">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="57817-147">**#r**</span><span class="sxs-lookup"><span data-stu-id="57817-147">**#r**</span></span>|<span data-ttu-id="57817-148">Fait référence à un assembly.</span><span class="sxs-lookup"><span data-stu-id="57817-148">References an assembly.</span></span>|
|<span data-ttu-id="57817-149">**#time ["on"&#124;"off"]**</span><span class="sxs-lookup"><span data-stu-id="57817-149">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="57817-150">Seul, **#time** active ou désactive l’affichage des informations sur les performances.</span><span class="sxs-lookup"><span data-stu-id="57817-150">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="57817-151">Lorsque cette option est activée, F# Interactive mesure le temps réel, le temps processeur et les informations de garbage collection pour chaque section du code qui est interprétée et exécutée.</span><span class="sxs-lookup"><span data-stu-id="57817-151">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="57817-152">Lorsque vous spécifiez des fichiers ou des chemins d'accès dans F# Interactive, un littéral de chaîne est attendu.</span><span class="sxs-lookup"><span data-stu-id="57817-152">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="57817-153">Par conséquent, les fichiers et les chemins d'accès doivent être entre guillemets, et les caractères d'échappement habituels s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="57817-153">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="57817-154">En outre, vous pouvez utiliser le caractère @ pour que F# Interactive interprète une chaîne qui contient un chemin d'accès comme chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="57817-154">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="57817-155">Dans ce cas, F# Interactive ignore les caractères d'échappement.</span><span class="sxs-lookup"><span data-stu-id="57817-155">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="57817-156">L’une des différences entre le mode compilé et le mode interactif est la façon d’accéder aux arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="57817-156">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="57817-157">En mode compilé, utilisez **System.Environment.GetCommandLineArgs** .</span><span class="sxs-lookup"><span data-stu-id="57817-157">In compiled mode, use **System.Environment.GetCommandLineArgs** .</span></span> <span data-ttu-id="57817-158">Dans les scripts, utilisez **fsi.CommandLineArgs** .</span><span class="sxs-lookup"><span data-stu-id="57817-158">In scripts, use **fsi.CommandLineArgs** .</span></span>

<span data-ttu-id="57817-159">Le code suivant illustre comment créer une fonction qui lit les arguments de ligne de commande dans un script et montre également comment référencer un autre assembly à partir d’un script.</span><span class="sxs-lookup"><span data-stu-id="57817-159">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="57817-160">Le premier fichier de code, **MyAssembly.fs** , est le code de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="57817-160">The first code file, **MyAssembly.fs** , is the code for the assembly being referenced.</span></span> <span data-ttu-id="57817-161">Compilez ce fichier avec la ligne de commande **fsc -a MyAssembly.fs** , puis exécutez le second fichier comme script avec la ligne de commande **fsi --exec file1.fsx** test.</span><span class="sxs-lookup"><span data-stu-id="57817-161">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="57817-162">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="57817-162">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="package-management-in-f-interactive"></a><span data-ttu-id="57817-163">Package Management dans F# Interactive</span><span class="sxs-lookup"><span data-stu-id="57817-163">Package Management in F# Interactive</span></span>

[!NOTE] <span data-ttu-id="57817-164">La gestion des packages est disponible sous la forme d’une fonctionnalité en version préliminaire dans les versions de `dotnet fsi` livrées avec `3.1.300` et versions ultérieures du kit de développement logiciel (SDK) .net, ainsi que toutes les `5.*` versions du kit de développement logiciel (SDK) .net.</span><span class="sxs-lookup"><span data-stu-id="57817-164">Package management is available as a preview feature in versions of `dotnet fsi` shipped in the `3.1.300` and greater versions of the .NET SDK, as well as all `5.*` versions of the .NET SDK.</span></span> <span data-ttu-id="57817-165">Pour l’activer dans cette version préliminaire, exécutez `dotnet fsi` avec l' `--langversion:preview` argument.</span><span class="sxs-lookup"><span data-stu-id="57817-165">To enable it in this preview release, run `dotnet fsi` with the `--langversion:preview` argument.</span></span>

<span data-ttu-id="57817-166">La `#r` syntaxe permettant de référencer une dll dans F# Interactive peut également être utilisée pour référencer un package NuGet à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="57817-166">The `#r` syntax for referencing a DLL in F# Interactive can also be used to reference a nuget package via the following syntax:</span></span>

```fsharp
#r "nuget: <package name>"
```

<span data-ttu-id="57817-167">Par exemple, pour référencer le `FSharp.Data` package, utilisez la `#r` référence suivante :</span><span class="sxs-lookup"><span data-stu-id="57817-167">For example, to reference the `FSharp.Data` package, use the following `#r` reference:</span></span>

```fsharp
#r "nuget: FSharp.Data"
```

<span data-ttu-id="57817-168">Après l’exécution de cette ligne, la version la plus récente du `FSharp.Data` package est téléchargée dans votre cache NuGet et référencée dans la session de F# Interactive actuelle.</span><span class="sxs-lookup"><span data-stu-id="57817-168">After executing this line, the latest version of the `FSharp.Data` package will be downloaded to your nuget cache and referenced in the current F# Interactive session.</span></span>

<span data-ttu-id="57817-169">En plus du nom du package, les versions spécifiques d’un package peuvent être référencées à l’aide d’une syntaxe abrégée :</span><span class="sxs-lookup"><span data-stu-id="57817-169">In addition to the package name, specific versions of a package can be referenced via a short syntax:</span></span>

```fsharp
#r "nuget: FSharp.Data, 3.3.2"
```

<span data-ttu-id="57817-170">ou de manière plus explicite :</span><span class="sxs-lookup"><span data-stu-id="57817-170">or in a more explicit fashion:</span></span>

```fsharp
#r "nuget: FSharp.Data, Version=3.3.2"
```

## <a name="related-articles"></a><span data-ttu-id="57817-171">Articles connexes</span><span class="sxs-lookup"><span data-stu-id="57817-171">Related articles</span></span>

|<span data-ttu-id="57817-172">Titre</span><span class="sxs-lookup"><span data-stu-id="57817-172">Title</span></span>|<span data-ttu-id="57817-173">Description</span><span class="sxs-lookup"><span data-stu-id="57817-173">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="57817-174">Options F# Interactive</span><span class="sxs-lookup"><span data-stu-id="57817-174">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="57817-175">Décrit la syntaxe et les options de ligne de commande pour le F# Interactive, fsi.exe.</span><span class="sxs-lookup"><span data-stu-id="57817-175">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
