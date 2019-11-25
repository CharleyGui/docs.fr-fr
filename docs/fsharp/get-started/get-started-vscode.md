---
title: Get Started with F# in Visual Studio Code
description: Learn how to use F# with Visual Studio Code and the Ionide plugin suite.
ms.date: 12/23/2018
ms.openlocfilehash: 2802438144eb2352c3abeeccfc126b16c6a87d8f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204911"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="265eb-103">Get Started with F# in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="265eb-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="265eb-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span><span class="sxs-lookup"><span data-stu-id="265eb-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="265eb-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span><span class="sxs-lookup"><span data-stu-id="265eb-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="265eb-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="265eb-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="265eb-107">Create your first project with Ionide</span><span class="sxs-lookup"><span data-stu-id="265eb-107">Create your first project with Ionide</span></span>

<span data-ttu-id="265eb-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span><span class="sxs-lookup"><span data-stu-id="265eb-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang F# -o FirstIonideProject
```

<span data-ttu-id="265eb-109">Once it completes, change directory to the project and open Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="265eb-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="265eb-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span><span class="sxs-lookup"><span data-stu-id="265eb-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="265eb-111">This means Ionide has successfully loaded the project you just created.</span><span class="sxs-lookup"><span data-stu-id="265eb-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="265eb-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span><span class="sxs-lookup"><span data-stu-id="265eb-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="265eb-113">Configure F# interactive</span><span class="sxs-lookup"><span data-stu-id="265eb-113">Configure F# interactive</span></span>

<span data-ttu-id="265eb-114">First, ensure that .NET Core scripting is your default scripting environment:</span><span class="sxs-lookup"><span data-stu-id="265eb-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="265eb-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span><span class="sxs-lookup"><span data-stu-id="265eb-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="265eb-116">Search for the term **F# Script**.</span><span class="sxs-lookup"><span data-stu-id="265eb-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="265eb-117">Click the checkbox that says **FSharp: use SDK scripts**.</span><span class="sxs-lookup"><span data-stu-id="265eb-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="265eb-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span><span class="sxs-lookup"><span data-stu-id="265eb-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="265eb-119">In the future, .NET Core scripting will become the default.</span><span class="sxs-lookup"><span data-stu-id="265eb-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="265eb-120">Write your first script</span><span class="sxs-lookup"><span data-stu-id="265eb-120">Write your first script</span></span>

<span data-ttu-id="265eb-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span><span class="sxs-lookup"><span data-stu-id="265eb-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="265eb-122">Name it *MyFirstScript.fsx*.</span><span class="sxs-lookup"><span data-stu-id="265eb-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="265eb-123">Now add the following code to it:</span><span class="sxs-lookup"><span data-stu-id="265eb-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="265eb-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="265eb-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="265eb-125">The next step is to evaluate it using F# Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="265eb-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="265eb-126">Highlight the entire function (it should be 11 lines long).</span><span class="sxs-lookup"><span data-stu-id="265eb-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="265eb-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span><span class="sxs-lookup"><span data-stu-id="265eb-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="265eb-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span><span class="sxs-lookup"><span data-stu-id="265eb-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![Example of F# Interactive output with Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="265eb-130">This did three things:</span><span class="sxs-lookup"><span data-stu-id="265eb-130">This did three things:</span></span>

1. <span data-ttu-id="265eb-131">It started the FSI process.</span><span class="sxs-lookup"><span data-stu-id="265eb-131">It started the FSI process.</span></span>
2. <span data-ttu-id="265eb-132">It sent the code you highlighted over the FSI process.</span><span class="sxs-lookup"><span data-stu-id="265eb-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="265eb-133">The FSI process evaluated the code you sent over.</span><span class="sxs-lookup"><span data-stu-id="265eb-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="265eb-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span><span class="sxs-lookup"><span data-stu-id="265eb-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="265eb-135">In the interactive window, type the following:</span><span class="sxs-lookup"><span data-stu-id="265eb-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="265eb-136">You should see the following result:</span><span class="sxs-lookup"><span data-stu-id="265eb-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="265eb-137">Now, let's try with a vowel as the first letter.</span><span class="sxs-lookup"><span data-stu-id="265eb-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="265eb-138">Entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="265eb-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="265eb-139">You should see the following result:</span><span class="sxs-lookup"><span data-stu-id="265eb-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="265eb-140">The function appears to be working as expected.</span><span class="sxs-lookup"><span data-stu-id="265eb-140">The function appears to be working as expected.</span></span> <span data-ttu-id="265eb-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span><span class="sxs-lookup"><span data-stu-id="265eb-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="265eb-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span><span class="sxs-lookup"><span data-stu-id="265eb-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="265eb-143">This is because FSI allows you to enter multiple lines.</span><span class="sxs-lookup"><span data-stu-id="265eb-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="265eb-144">The `;;` at the end lets FSI know when the code is finished.</span><span class="sxs-lookup"><span data-stu-id="265eb-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="265eb-145">Explaining the code</span><span class="sxs-lookup"><span data-stu-id="265eb-145">Explaining the code</span></span>

<span data-ttu-id="265eb-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span><span class="sxs-lookup"><span data-stu-id="265eb-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="265eb-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span><span class="sxs-lookup"><span data-stu-id="265eb-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="265eb-148">The rules for this are as follows:</span><span class="sxs-lookup"><span data-stu-id="265eb-148">The rules for this are as follows:</span></span>

<span data-ttu-id="265eb-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span><span class="sxs-lookup"><span data-stu-id="265eb-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="265eb-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span><span class="sxs-lookup"><span data-stu-id="265eb-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="265eb-151">You may have noticed the following in FSI:</span><span class="sxs-lookup"><span data-stu-id="265eb-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="265eb-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span><span class="sxs-lookup"><span data-stu-id="265eb-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="265eb-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span><span class="sxs-lookup"><span data-stu-id="265eb-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="265eb-154">You'll also notice this if you hover over the function in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="265eb-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="265eb-155">In the body of the function, you'll notice two distinct parts:</span><span class="sxs-lookup"><span data-stu-id="265eb-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="265eb-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="265eb-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="265eb-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span><span class="sxs-lookup"><span data-stu-id="265eb-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="265eb-158">The flow of `toPigLatin` is thus:</span><span class="sxs-lookup"><span data-stu-id="265eb-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="265eb-159">Check if the first character of the input word is a vowel.</span><span class="sxs-lookup"><span data-stu-id="265eb-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="265eb-160">If it is, attach "yay" to the end of the word.</span><span class="sxs-lookup"><span data-stu-id="265eb-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="265eb-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span><span class="sxs-lookup"><span data-stu-id="265eb-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="265eb-162">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span><span class="sxs-lookup"><span data-stu-id="265eb-162">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="265eb-163">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span><span class="sxs-lookup"><span data-stu-id="265eb-163">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="265eb-164">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span><span class="sxs-lookup"><span data-stu-id="265eb-164">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="265eb-165">Turn the console app into a Pig Latin generator</span><span class="sxs-lookup"><span data-stu-id="265eb-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="265eb-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span><span class="sxs-lookup"><span data-stu-id="265eb-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="265eb-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span><span class="sxs-lookup"><span data-stu-id="265eb-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="265eb-168">It's a great way to experiment with functionality until you have something working.</span><span class="sxs-lookup"><span data-stu-id="265eb-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="265eb-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span><span class="sxs-lookup"><span data-stu-id="265eb-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="265eb-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span><span class="sxs-lookup"><span data-stu-id="265eb-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="265eb-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="265eb-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="265eb-172">You'll notice that some code is already in there.</span><span class="sxs-lookup"><span data-stu-id="265eb-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="265eb-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span><span class="sxs-lookup"><span data-stu-id="265eb-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="265eb-174">This module should be above the `main` function and below the `open System` declaration.</span><span class="sxs-lookup"><span data-stu-id="265eb-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="265eb-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span><span class="sxs-lookup"><span data-stu-id="265eb-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="265eb-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span><span class="sxs-lookup"><span data-stu-id="265eb-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

<span data-ttu-id="265eb-177">Now you can run your console app from the command line:</span><span class="sxs-lookup"><span data-stu-id="265eb-177">Now you can run your console app from the command line:</span></span>

```console
dotnet run apple banana
```

<span data-ttu-id="265eb-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span><span class="sxs-lookup"><span data-stu-id="265eb-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="265eb-179">Troubleshooting Ionide</span><span class="sxs-lookup"><span data-stu-id="265eb-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="265eb-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span><span class="sxs-lookup"><span data-stu-id="265eb-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="265eb-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span><span class="sxs-lookup"><span data-stu-id="265eb-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="265eb-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="265eb-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="265eb-183">If you have invalid characters in your project directories, Ionide might not work.</span><span class="sxs-lookup"><span data-stu-id="265eb-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="265eb-184">Rename your project directories if this is the case.</span><span class="sxs-lookup"><span data-stu-id="265eb-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="265eb-185">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span><span class="sxs-lookup"><span data-stu-id="265eb-185">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="265eb-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span><span class="sxs-lookup"><span data-stu-id="265eb-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="265eb-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span><span class="sxs-lookup"><span data-stu-id="265eb-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="265eb-188">Ionide is an open source project built and maintained by members of the F# community.</span><span class="sxs-lookup"><span data-stu-id="265eb-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="265eb-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="265eb-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="265eb-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="265eb-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="265eb-191">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="265eb-191">Next steps</span></span>

<span data-ttu-id="265eb-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="265eb-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
