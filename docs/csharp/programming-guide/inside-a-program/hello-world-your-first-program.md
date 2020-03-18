---
title: Hello World -- Votre premier programme utilisant Visual Studio sur Windows ou Mac - Guide de programmation C
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712141"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="392b4-102">Bonjour Monde -- Votre premier programme</span><span class="sxs-lookup"><span data-stu-id="392b4-102">Hello World -- Your first program</span></span>

<span data-ttu-id="392b4-103">Dans cet article, vous utiliserez Visual Studio pour créer le traditionnel "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="392b4-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="392b4-104">.</span><span class="sxs-lookup"><span data-stu-id="392b4-104">program.</span></span> <span data-ttu-id="392b4-105">Visual Studio est un environnement de développement intégré professionnel (IDE) avec de nombreuses fonctionnalités conçues pour le développement .NET.</span><span class="sxs-lookup"><span data-stu-id="392b4-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="392b4-106">Vous n’utiliserez que quelques-unes des fonctionnalités de Visual Studio pour créer ce programme.</span><span class="sxs-lookup"><span data-stu-id="392b4-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="392b4-107">Pour en savoir plus sur Visual Studio, voir [Getting Started with Visual C .](/visualstudio/ide/quickstart-csharp-console)</span><span class="sxs-lookup"><span data-stu-id="392b4-107">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="392b4-108">Créer une application</span><span class="sxs-lookup"><span data-stu-id="392b4-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="392b4-109">Windows</span><span class="sxs-lookup"><span data-stu-id="392b4-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="392b4-110">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="392b4-110">Start Visual Studio.</span></span> <span data-ttu-id="392b4-111">Vous verrez l’image suivante sur Windows :</span><span class="sxs-lookup"><span data-stu-id="392b4-111">You'll see the following image on Windows:</span></span>

![Écran de bienvenue Visual Studio sur Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="392b4-113">Sélectionnez **Créer un nouveau projet** dans le coin inférieur droit de l’image.</span><span class="sxs-lookup"><span data-stu-id="392b4-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="392b4-114">Visual Studio affiche le dialogue **du nouveau projet** :</span><span class="sxs-lookup"><span data-stu-id="392b4-114">Visual Studio displays the **New Project** dialog:</span></span>

![Visual Studio nouvel écran de projet sur Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="392b4-116">Si c’est la première fois que vous lancez Visual Studio, la liste **des modèles de projets récents** est vide.</span><span class="sxs-lookup"><span data-stu-id="392b4-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="392b4-117">Sur le nouveau dialogue de projet, choisissez "Console App (.NET Core)" et appuyez ensuite **sur Next**.</span><span class="sxs-lookup"><span data-stu-id="392b4-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="392b4-118">Donnez à votre projet un nom, tel que "HelloWorld", puis appuyez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="392b4-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="392b4-119">Visual Studio ouvre votre projet.</span><span class="sxs-lookup"><span data-stu-id="392b4-119">Visual Studio opens your project.</span></span> <span data-ttu-id="392b4-120">C’est déjà un "Bonjour Monde!"</span><span class="sxs-lookup"><span data-stu-id="392b4-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="392b4-121">« Hello, World! ».</span><span class="sxs-lookup"><span data-stu-id="392b4-121">example.</span></span> <span data-ttu-id="392b4-122">Appuyez `Ctrl`  +  `F5` pour exécuter votre projet.</span><span class="sxs-lookup"><span data-stu-id="392b4-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="392b4-123">Visual Studio construit votre projet, convertissant le code source en un exécutable.</span><span class="sxs-lookup"><span data-stu-id="392b4-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="392b4-124">Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="392b4-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="392b4-125">Vous devriez voir le texte suivant dans la fenêtre:</span><span class="sxs-lookup"><span data-stu-id="392b4-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="392b4-126">Appuyez sur une touche pour fermer la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="392b4-126">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="392b4-127">macOS</span><span class="sxs-lookup"><span data-stu-id="392b4-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="392b4-128">Démarrer Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="392b4-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="392b4-129">Vous verrez l’image suivante sur Mac :</span><span class="sxs-lookup"><span data-stu-id="392b4-129">You'll see the following image on Mac:</span></span>

![Écran de bienvenue Visual Studio sur Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="392b4-131">Si c’est la première fois que vous avez commencé Visual Studio pour Mac, la liste **des projets récents** est vide.</span><span class="sxs-lookup"><span data-stu-id="392b4-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="392b4-132">Sélectionnez **Nouveau** dans le coin supérieur droit de l’image.</span><span class="sxs-lookup"><span data-stu-id="392b4-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="392b4-133">Visual Studio pour Mac affiche le dialogue **du nouveau projet** :</span><span class="sxs-lookup"><span data-stu-id="392b4-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Visual Studio nouvel écran de projet sur Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="392b4-135">Sur le nouveau dialogue de projet, choisissez ".NET Core", et "Console App" et appuyez ensuite sur **Next**.</span><span class="sxs-lookup"><span data-stu-id="392b4-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="392b4-136">Vous devrez sélectionner le cadre cible.</span><span class="sxs-lookup"><span data-stu-id="392b4-136">You'll need to select the target framework.</span></span> <span data-ttu-id="392b4-137">La valeur par défaut est très bien, alors appuyez ensuite.</span><span class="sxs-lookup"><span data-stu-id="392b4-137">The default is fine, so press next.</span></span> <span data-ttu-id="392b4-138">Donnez à votre projet un nom, tel que "HelloWorld", puis appuyez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="392b4-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="392b4-139">Vous pouvez utiliser l’emplacement par défaut du projet.</span><span class="sxs-lookup"><span data-stu-id="392b4-139">You can use the default project location.</span></span> <span data-ttu-id="392b4-140">N’ajoutez pas ce projet au contrôle des sources.</span><span class="sxs-lookup"><span data-stu-id="392b4-140">Don't add this project to source control.</span></span>

<span data-ttu-id="392b4-141">Visual Studio pour Mac ouvre votre projet.</span><span class="sxs-lookup"><span data-stu-id="392b4-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="392b4-142">C’est déjà un "Bonjour Monde!"</span><span class="sxs-lookup"><span data-stu-id="392b4-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="392b4-143">« Hello, World! ».</span><span class="sxs-lookup"><span data-stu-id="392b4-143">example.</span></span> <span data-ttu-id="392b4-144">`Ctrl`  +  `Fn` Appuyez  +  `F5` pour exécuter votre projet.</span><span class="sxs-lookup"><span data-stu-id="392b4-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="392b4-145">Visual Studio pour Mac construit votre projet, convertissant le code source en un exécutable.</span><span class="sxs-lookup"><span data-stu-id="392b4-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="392b4-146">Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="392b4-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="392b4-147">Vous devriez voir le texte suivant dans la fenêtre:</span><span class="sxs-lookup"><span data-stu-id="392b4-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="392b4-148">Appuyez sur une clé pour terminer la session.</span><span class="sxs-lookup"><span data-stu-id="392b4-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="392b4-149">Éléments d’un programme C</span><span class="sxs-lookup"><span data-stu-id="392b4-149">Elements of a C# program</span></span>

<span data-ttu-id="392b4-150">Examinons les parties importantes de ce programme.</span><span class="sxs-lookup"><span data-stu-id="392b4-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="392b4-151">La première ligne contient un commentaire.</span><span class="sxs-lookup"><span data-stu-id="392b4-151">The first line contains a comment.</span></span> <span data-ttu-id="392b4-152">Les caractères `//` convertissent le reste de la ligne en un commentaire.</span><span class="sxs-lookup"><span data-stu-id="392b4-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="392b4-153">Vous pouvez également créer un commentaire à partir d’un bloc de texte en le plaçant entre les caractères `/*` et `*/`.</span><span class="sxs-lookup"><span data-stu-id="392b4-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="392b4-154">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="392b4-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="392b4-155">Une application console C# doit contenir une méthode `Main`, dans laquelle le contrôle commence et termine.</span><span class="sxs-lookup"><span data-stu-id="392b4-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="392b4-156">C’est dans la méthode `Main` que vous créez des objets et exécutez d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="392b4-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="392b4-157">La méthode `Main` est une méthode [static](../../language-reference/keywords/static.md) qui réside dans une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="392b4-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="392b4-158">Dans l’exemple « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="392b4-158">In the previous "Hello World!"</span></span> <span data-ttu-id="392b4-159">précédent, il réside dans une classe nommée `Hello`.</span><span class="sxs-lookup"><span data-stu-id="392b4-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="392b4-160">Vous pouvez déclarer la méthode `Main` de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="392b4-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="392b4-161">Elle peut retourner `void`.</span><span class="sxs-lookup"><span data-stu-id="392b4-161">It can return `void`.</span></span> <span data-ttu-id="392b4-162">Cela signifie que votre programme ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="392b4-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="392b4-163">Elle peut également retourner un entier.</span><span class="sxs-lookup"><span data-stu-id="392b4-163">It can also return an integer.</span></span> <span data-ttu-id="392b4-164">L’integer est le **code de sortie** de votre application.</span><span class="sxs-lookup"><span data-stu-id="392b4-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="392b4-165">Elle peut accepter des arguments avec n’importe quel type de retour.</span><span class="sxs-lookup"><span data-stu-id="392b4-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="392b4-166">-ou-</span><span class="sxs-lookup"><span data-stu-id="392b4-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="392b4-167">Le paramètre `args` de la méthode `Main` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme.</span><span class="sxs-lookup"><span data-stu-id="392b4-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="392b4-168">Pour plus d’informations sur la façon d’utiliser les arguments de la ligne de commande, voir les exemples dans [Main() et Command-Line Arguments](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="392b4-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="392b4-169">Entrée et sortie</span><span class="sxs-lookup"><span data-stu-id="392b4-169">Input and output</span></span>

<span data-ttu-id="392b4-170">Les programmes C# utilisent généralement les services d’entrée/sortie fournis par la bibliothèque runtime du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="392b4-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="392b4-171">L’instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="392b4-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="392b4-172">C’est l’une des méthodes de sortie de la classe <xref:System.Console> de la bibliothèque runtime.</span><span class="sxs-lookup"><span data-stu-id="392b4-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="392b4-173">Elle affiche son paramètre de chaîne dans le flux de sortie standard suivi d’une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="392b4-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="392b4-174">D’autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="392b4-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="392b4-175">Si vous incluez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement.</span><span class="sxs-lookup"><span data-stu-id="392b4-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="392b4-176">Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="392b4-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="392b4-177">Pour plus d’informations sur les méthodes d’entrée/sortie, consultez <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="392b4-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="392b4-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="392b4-178">See also</span></span>

- [<span data-ttu-id="392b4-179">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="392b4-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="392b4-180">Échantillons et tutoriels</span><span class="sxs-lookup"><span data-stu-id="392b4-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="392b4-181">Main() et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="392b4-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="392b4-182">Mise en route de Visual C#</span><span class="sxs-lookup"><span data-stu-id="392b4-182">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
