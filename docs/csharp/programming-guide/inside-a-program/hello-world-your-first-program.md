---
title: Hello World--votre premier programme à l’aide de Visual Studio sur Windows ou Mac-Guide de programmation C#
description: Visual Studio est un environnement de développement professionnel avec de nombreuses fonctionnalités pour le développement .NET. Utilisez Visual Studio pour créer une version C# de Hello World !
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: b78937b8ba1c7d4718bfb6252dac705945336d2a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301825"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="538cf-104">Hello World--votre premier programme</span><span class="sxs-lookup"><span data-stu-id="538cf-104">Hello World -- Your first program</span></span>

<span data-ttu-id="538cf-105">Dans cet article, vous allez utiliser Visual Studio pour créer le « Hello World ! » traditionnel</span><span class="sxs-lookup"><span data-stu-id="538cf-105">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="538cf-106">.</span><span class="sxs-lookup"><span data-stu-id="538cf-106">program.</span></span> <span data-ttu-id="538cf-107">Visual Studio est un environnement de développement intégré (IDE) professionnel avec de nombreuses fonctionnalités conçues pour le développement .NET.</span><span class="sxs-lookup"><span data-stu-id="538cf-107">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="538cf-108">Vous n’utiliserez que quelques-unes des fonctionnalités de Visual Studio pour créer ce programme.</span><span class="sxs-lookup"><span data-stu-id="538cf-108">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="538cf-109">Pour en savoir plus sur Visual Studio, consultez [prise en main avec Visual C#](/visualstudio/ide/quickstart-csharp-console).</span><span class="sxs-lookup"><span data-stu-id="538cf-109">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="538cf-110">Créer une application</span><span class="sxs-lookup"><span data-stu-id="538cf-110">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="538cf-111">Windows</span><span class="sxs-lookup"><span data-stu-id="538cf-111">Windows</span></span>](#tab/windows)

<span data-ttu-id="538cf-112">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="538cf-112">Start Visual Studio.</span></span> <span data-ttu-id="538cf-113">L’image suivante s’affiche sur Windows :</span><span class="sxs-lookup"><span data-stu-id="538cf-113">You'll see the following image on Windows:</span></span>

![Écran de bienvenue de Visual Studio sur Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="538cf-115">Sélectionnez **créer un nouveau projet** dans le coin inférieur droit de l’image.</span><span class="sxs-lookup"><span data-stu-id="538cf-115">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="538cf-116">Visual Studio affiche la boîte **de dialogue Nouveau projet** :</span><span class="sxs-lookup"><span data-stu-id="538cf-116">Visual Studio displays the **New Project** dialog:</span></span>

![Écran nouveau projet de Visual Studio sur Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="538cf-118">S’il s’agit de la première fois que vous démarrez Visual Studio, la liste des **modèles de projet récents** est vide.</span><span class="sxs-lookup"><span data-stu-id="538cf-118">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="538cf-119">Dans la boîte de dialogue Nouveau projet, choisissez application console (.NET Core), puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="538cf-119">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="538cf-120">Donnez un nom à votre projet, tel que « HelloWorld », puis appuyez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="538cf-120">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="538cf-121">Visual Studio ouvre votre projet.</span><span class="sxs-lookup"><span data-stu-id="538cf-121">Visual Studio opens your project.</span></span> <span data-ttu-id="538cf-122">Il s’agit déjà d’un « Hello World ! » de base.</span><span class="sxs-lookup"><span data-stu-id="538cf-122">It's already a basic "Hello World!"</span></span> <span data-ttu-id="538cf-123">« Hello, World! ».</span><span class="sxs-lookup"><span data-stu-id="538cf-123">example.</span></span> <span data-ttu-id="538cf-124">Appuyez sur `Ctrl`  +  `F5` pour exécuter votre projet.</span><span class="sxs-lookup"><span data-stu-id="538cf-124">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="538cf-125">Visual Studio génère votre projet et convertit le code source en un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="538cf-125">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="538cf-126">Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="538cf-126">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="538cf-127">Vous devez voir le texte suivant dans la fenêtre :</span><span class="sxs-lookup"><span data-stu-id="538cf-127">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="538cf-128">Appuyez sur une touche pour fermer la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="538cf-128">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="538cf-129">macOS</span><span class="sxs-lookup"><span data-stu-id="538cf-129">macOS</span></span>](#tab/macos)

<span data-ttu-id="538cf-130">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="538cf-130">Start Visual Studio for Mac.</span></span> <span data-ttu-id="538cf-131">L’image suivante s’affiche sur Mac :</span><span class="sxs-lookup"><span data-stu-id="538cf-131">You'll see the following image on Mac:</span></span>

![Écran de bienvenue de Visual Studio sur Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="538cf-133">S’il s’agit de la première fois que vous démarrez Visual Studio pour Mac, la liste des **projets récents** est vide.</span><span class="sxs-lookup"><span data-stu-id="538cf-133">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="538cf-134">Sélectionnez **nouveau** dans le coin supérieur droit de l’image.</span><span class="sxs-lookup"><span data-stu-id="538cf-134">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="538cf-135">Visual Studio pour Mac affiche la boîte **de dialogue Nouveau projet** :</span><span class="sxs-lookup"><span data-stu-id="538cf-135">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Écran nouveau projet de Visual Studio sur Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="538cf-137">Dans la boîte de dialogue Nouveau projet, choisissez « .NET Core » et « application console », puis appuyez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="538cf-137">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="538cf-138">Vous devez sélectionner la version cible de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="538cf-138">You'll need to select the target framework.</span></span> <span data-ttu-id="538cf-139">La valeur par défaut est correcte. Appuyez sur suivant.</span><span class="sxs-lookup"><span data-stu-id="538cf-139">The default is fine, so press next.</span></span> <span data-ttu-id="538cf-140">Donnez un nom à votre projet, tel que « HelloWorld », puis appuyez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="538cf-140">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="538cf-141">Vous pouvez utiliser l’emplacement de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="538cf-141">You can use the default project location.</span></span> <span data-ttu-id="538cf-142">N’ajoutez pas ce projet au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="538cf-142">Don't add this project to source control.</span></span>

<span data-ttu-id="538cf-143">Visual Studio pour Mac ouvre votre projet.</span><span class="sxs-lookup"><span data-stu-id="538cf-143">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="538cf-144">Il s’agit déjà d’un « Hello World ! » de base.</span><span class="sxs-lookup"><span data-stu-id="538cf-144">It's already a basic "Hello World!"</span></span> <span data-ttu-id="538cf-145">« Hello, World! ».</span><span class="sxs-lookup"><span data-stu-id="538cf-145">example.</span></span> <span data-ttu-id="538cf-146">Appuyez sur `Ctrl`  +  `Fn`  +  `F5` pour exécuter votre projet.</span><span class="sxs-lookup"><span data-stu-id="538cf-146">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="538cf-147">Visual Studio pour Mac génère votre projet et convertit le code source en un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="538cf-147">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="538cf-148">Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="538cf-148">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="538cf-149">Vous devez voir le texte suivant dans la fenêtre :</span><span class="sxs-lookup"><span data-stu-id="538cf-149">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="538cf-150">Appuyez sur une touche pour mettre fin à la session.</span><span class="sxs-lookup"><span data-stu-id="538cf-150">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="538cf-151">Éléments d’un programme C#</span><span class="sxs-lookup"><span data-stu-id="538cf-151">Elements of a C# program</span></span>

<span data-ttu-id="538cf-152">Examinons les parties importantes de ce programme.</span><span class="sxs-lookup"><span data-stu-id="538cf-152">Let's examine the important parts of this program.</span></span> <span data-ttu-id="538cf-153">La première ligne contient un commentaire.</span><span class="sxs-lookup"><span data-stu-id="538cf-153">The first line contains a comment.</span></span> <span data-ttu-id="538cf-154">Les caractères `//` convertissent le reste de la ligne en un commentaire.</span><span class="sxs-lookup"><span data-stu-id="538cf-154">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="538cf-155">Vous pouvez également créer un commentaire à partir d’un bloc de texte en le plaçant entre les caractères `/*` et `*/`.</span><span class="sxs-lookup"><span data-stu-id="538cf-155">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="538cf-156">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="538cf-156">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="538cf-157">Une application console C# doit contenir une méthode `Main`, dans laquelle le contrôle commence et termine.</span><span class="sxs-lookup"><span data-stu-id="538cf-157">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="538cf-158">C’est dans la méthode `Main` que vous créez des objets et exécutez d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="538cf-158">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="538cf-159">La méthode `Main` est une méthode [static](../../language-reference/keywords/static.md) qui réside dans une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="538cf-159">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="538cf-160">Dans l’exemple « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="538cf-160">In the previous "Hello World!"</span></span> <span data-ttu-id="538cf-161">précédent, il réside dans une classe nommée `Hello`.</span><span class="sxs-lookup"><span data-stu-id="538cf-161">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="538cf-162">Vous pouvez déclarer la méthode `Main` de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="538cf-162">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="538cf-163">Elle peut retourner `void`.</span><span class="sxs-lookup"><span data-stu-id="538cf-163">It can return `void`.</span></span> <span data-ttu-id="538cf-164">Cela signifie que votre programme ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="538cf-164">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="538cf-165">Elle peut également retourner un entier.</span><span class="sxs-lookup"><span data-stu-id="538cf-165">It can also return an integer.</span></span> <span data-ttu-id="538cf-166">L’entier est le **Code de sortie** de votre application.</span><span class="sxs-lookup"><span data-stu-id="538cf-166">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="538cf-167">Elle peut accepter des arguments avec n’importe quel type de retour.</span><span class="sxs-lookup"><span data-stu-id="538cf-167">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="538cf-168">-ou-</span><span class="sxs-lookup"><span data-stu-id="538cf-168">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="538cf-169">Le paramètre `args` de la méthode `Main` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme.</span><span class="sxs-lookup"><span data-stu-id="538cf-169">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="538cf-170">Pour plus d’informations sur l’utilisation des arguments de ligne de commande, consultez les exemples dans [main () et arguments de ligne de commande](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="538cf-170">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="538cf-171">Entrée et sortie</span><span class="sxs-lookup"><span data-stu-id="538cf-171">Input and output</span></span>

<span data-ttu-id="538cf-172">Les programmes C# utilisent généralement les services d’entrée/sortie fournis par la bibliothèque Runtime de .NET.</span><span class="sxs-lookup"><span data-stu-id="538cf-172">C# programs generally use the input/output services provided by the run-time library of .NET.</span></span> <span data-ttu-id="538cf-173">L’instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="538cf-173">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="538cf-174">C’est l’une des méthodes de sortie de la classe <xref:System.Console> de la bibliothèque runtime.</span><span class="sxs-lookup"><span data-stu-id="538cf-174">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="538cf-175">Elle affiche son paramètre de chaîne dans le flux de sortie standard suivi d’une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="538cf-175">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="538cf-176">D’autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="538cf-176">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="538cf-177">Si vous incluez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement.</span><span class="sxs-lookup"><span data-stu-id="538cf-177">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="538cf-178">Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="538cf-178">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="538cf-179">Pour plus d’informations sur les méthodes d’entrée/sortie, consultez <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="538cf-179">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="538cf-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="538cf-180">See also</span></span>

- [<span data-ttu-id="538cf-181">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="538cf-181">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="538cf-182">Exemples et tutoriels</span><span class="sxs-lookup"><span data-stu-id="538cf-182">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="538cf-183">Main () et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="538cf-183">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="538cf-184">Mise en route de Visual C#</span><span class="sxs-lookup"><span data-stu-id="538cf-184">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
