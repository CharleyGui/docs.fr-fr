---
title: Hello World--votre premier programme à l’aide de Visual Studio sur Windows C# ou Mac-Guide de programmation
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 0807e46d36a4cf031bc44ae0dc4efab79dd51d03
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991340"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="5a303-102">Hello World--votre premier programme</span><span class="sxs-lookup"><span data-stu-id="5a303-102">Hello World -- Your first program</span></span>

<span data-ttu-id="5a303-103">Dans cet article, vous allez utiliser Visual Studio pour créer le « Hello World ! » traditionnel</span><span class="sxs-lookup"><span data-stu-id="5a303-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="5a303-104">.</span><span class="sxs-lookup"><span data-stu-id="5a303-104">program.</span></span> <span data-ttu-id="5a303-105">Visual Studio est un environnement de développement intégré (IDE) professionnel avec de nombreuses fonctionnalités conçues pour le développement .NET.</span><span class="sxs-lookup"><span data-stu-id="5a303-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="5a303-106">Vous n’utiliserez que quelques-unes des fonctionnalités de Visual Studio pour créer ce programme.</span><span class="sxs-lookup"><span data-stu-id="5a303-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="5a303-107">Pour en savoir plus sur Visual Studio, consultez [prise en main avec C# Visual et Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5a303-107">To learn more about Visual Studio, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="5a303-108">Créer une application</span><span class="sxs-lookup"><span data-stu-id="5a303-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="5a303-109">Windows</span><span class="sxs-lookup"><span data-stu-id="5a303-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="5a303-110">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a303-110">Start Visual Studio.</span></span> <span data-ttu-id="5a303-111">L’image suivante s’affiche sur Windows :</span><span class="sxs-lookup"><span data-stu-id="5a303-111">You'll see the following image on Windows:</span></span>

![Écran de bienvenue de Visual Studio sur Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="5a303-113">Sélectionnez **créer un nouveau projet** dans le coin inférieur droit de l’image.</span><span class="sxs-lookup"><span data-stu-id="5a303-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="5a303-114">Visual Studio affiche la boîte **de dialogue Nouveau projet** :</span><span class="sxs-lookup"><span data-stu-id="5a303-114">Visual Studio displays the **New Project** dialog:</span></span>

![Écran nouveau projet de Visual Studio sur Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="5a303-116">S’il s’agit de la première fois que vous démarrez Visual Studio, la liste des **modèles de projet récents** est vide.</span><span class="sxs-lookup"><span data-stu-id="5a303-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="5a303-117">Dans la boîte de dialogue Nouveau projet, choisissez application console (.NET Core), puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5a303-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="5a303-118">Donnez un nom à votre projet, tel que « HelloWorld », puis appuyez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="5a303-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="5a303-119">Visual Studio ouvre votre projet.</span><span class="sxs-lookup"><span data-stu-id="5a303-119">Visual Studio opens your project.</span></span> <span data-ttu-id="5a303-120">Il s’agit déjà d’un « Hello World ! » de base.</span><span class="sxs-lookup"><span data-stu-id="5a303-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="5a303-121">« Hello, World! ».</span><span class="sxs-lookup"><span data-stu-id="5a303-121">example.</span></span> <span data-ttu-id="5a303-122">Appuyez `Ctrl`  +  sur pour exécuter votreprojet.`F5`</span><span class="sxs-lookup"><span data-stu-id="5a303-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="5a303-123">Visual Studio génère votre projet et convertit le code source en un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="5a303-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="5a303-124">Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="5a303-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="5a303-125">Vous devez voir le texte suivant dans la fenêtre :</span><span class="sxs-lookup"><span data-stu-id="5a303-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="5a303-126">Appuyez sur une touche pour fermer la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="5a303-126">Press a key to close the window.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="5a303-127">macOS</span><span class="sxs-lookup"><span data-stu-id="5a303-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="5a303-128">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="5a303-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="5a303-129">L’image suivante s’affiche sur Mac :</span><span class="sxs-lookup"><span data-stu-id="5a303-129">You'll see the following image on Mac:</span></span>

![Écran de bienvenue de Visual Studio sur Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="5a303-131">S’il s’agit de la première fois que vous démarrez Visual Studio pour Mac, la liste des **projets récents** est vide.</span><span class="sxs-lookup"><span data-stu-id="5a303-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="5a303-132">Sélectionnez **nouveau** dans le coin supérieur droit de l’image.</span><span class="sxs-lookup"><span data-stu-id="5a303-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="5a303-133">Visual Studio pour Mac affiche la boîte **de dialogue Nouveau projet** :</span><span class="sxs-lookup"><span data-stu-id="5a303-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Écran nouveau projet de Visual Studio sur Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="5a303-135">Dans la boîte de dialogue Nouveau projet, choisissez « .NET Core » et « application console », puis appuyez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5a303-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="5a303-136">Vous devez sélectionner la version cible de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a303-136">You'll need to select the target framework.</span></span> <span data-ttu-id="5a303-137">La valeur par défaut est correcte. Appuyez sur suivant.</span><span class="sxs-lookup"><span data-stu-id="5a303-137">The default is fine, so press next.</span></span> <span data-ttu-id="5a303-138">Donnez un nom à votre projet, tel que « HelloWorld », puis appuyez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="5a303-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="5a303-139">Vous pouvez utiliser l’emplacement de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a303-139">You can use the default project location.</span></span> <span data-ttu-id="5a303-140">N’ajoutez pas ce projet au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="5a303-140">Don't add this project to source control.</span></span>

<span data-ttu-id="5a303-141">Visual Studio pour Mac ouvre votre projet.</span><span class="sxs-lookup"><span data-stu-id="5a303-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="5a303-142">Il s’agit déjà d’un « Hello World ! » de base.</span><span class="sxs-lookup"><span data-stu-id="5a303-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="5a303-143">« Hello, World! ».</span><span class="sxs-lookup"><span data-stu-id="5a303-143">example.</span></span> <span data-ttu-id="5a303-144">Appuyez `Ctrl` surpour + exécuter votreprojet. +  `Fn` `F5`</span><span class="sxs-lookup"><span data-stu-id="5a303-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="5a303-145">Visual Studio pour Mac génère votre projet et convertit le code source en un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="5a303-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="5a303-146">Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="5a303-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="5a303-147">Vous devez voir le texte suivant dans la fenêtre :</span><span class="sxs-lookup"><span data-stu-id="5a303-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="5a303-148">Appuyez sur une touche pour mettre fin à la session.</span><span class="sxs-lookup"><span data-stu-id="5a303-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="5a303-149">Éléments d’un C# programme</span><span class="sxs-lookup"><span data-stu-id="5a303-149">Elements of a C# program</span></span>

<span data-ttu-id="5a303-150">Examinons les parties importantes de ce programme.</span><span class="sxs-lookup"><span data-stu-id="5a303-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="5a303-151">La première ligne contient un commentaire.</span><span class="sxs-lookup"><span data-stu-id="5a303-151">The first line contains a comment.</span></span> <span data-ttu-id="5a303-152">Les caractères `//` convertissent le reste de la ligne en un commentaire.</span><span class="sxs-lookup"><span data-stu-id="5a303-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="5a303-153">Vous pouvez également créer un commentaire à partir d’un bloc de texte en le plaçant entre les caractères `/*` et `*/`.</span><span class="sxs-lookup"><span data-stu-id="5a303-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="5a303-154">L'exemple suivant le démontre.</span><span class="sxs-lookup"><span data-stu-id="5a303-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="5a303-155">Une application console C# doit contenir une méthode `Main`, dans laquelle le contrôle commence et termine.</span><span class="sxs-lookup"><span data-stu-id="5a303-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="5a303-156">C’est dans la méthode `Main` que vous créez des objets et exécutez d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="5a303-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="5a303-157">La méthode `Main` est une méthode [static](../../language-reference/keywords/static.md) qui réside dans une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="5a303-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="5a303-158">Dans l’exemple « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="5a303-158">In the previous "Hello World!"</span></span> <span data-ttu-id="5a303-159">précédent, il réside dans une classe nommée `Hello`.</span><span class="sxs-lookup"><span data-stu-id="5a303-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="5a303-160">Vous pouvez déclarer la méthode `Main` de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a303-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="5a303-161">Elle peut retourner `void`.</span><span class="sxs-lookup"><span data-stu-id="5a303-161">It can return `void`.</span></span> <span data-ttu-id="5a303-162">Cela signifie que votre programme ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="5a303-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="5a303-163">Elle peut également retourner un entier.</span><span class="sxs-lookup"><span data-stu-id="5a303-163">It can also return an integer.</span></span> <span data-ttu-id="5a303-164">L’entier est le **Code de sortie** de votre application.</span><span class="sxs-lookup"><span data-stu-id="5a303-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="5a303-165">Elle peut accepter des arguments avec n’importe quel type de retour.</span><span class="sxs-lookup"><span data-stu-id="5a303-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="5a303-166">ou</span><span class="sxs-lookup"><span data-stu-id="5a303-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="5a303-167">Le paramètre `args` de la méthode `Main` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme.</span><span class="sxs-lookup"><span data-stu-id="5a303-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="5a303-168">Pour plus d’informations sur l’utilisation des arguments de ligne de commande, consultez les exemples dans [main () et arguments de ligne de commande](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a303-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="5a303-169">Entrée et sortie</span><span class="sxs-lookup"><span data-stu-id="5a303-169">Input and output</span></span>

<span data-ttu-id="5a303-170">Les programmes C# utilisent généralement les services d’entrée/sortie fournis par la bibliothèque runtime du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a303-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="5a303-171">L’instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a303-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="5a303-172">C’est l’une des méthodes de sortie de la classe <xref:System.Console> de la bibliothèque runtime.</span><span class="sxs-lookup"><span data-stu-id="5a303-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="5a303-173">Elle affiche son paramètre de chaîne dans le flux de sortie standard suivi d’une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="5a303-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="5a303-174">D’autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="5a303-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="5a303-175">Si vous incluez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement.</span><span class="sxs-lookup"><span data-stu-id="5a303-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="5a303-176">Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="5a303-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="5a303-177">Pour plus d’informations sur les méthodes d’entrée/sortie, consultez <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="5a303-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a303-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a303-178">See also</span></span>

- [<span data-ttu-id="5a303-179">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5a303-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5a303-180">Exemples et tutoriels</span><span class="sxs-lookup"><span data-stu-id="5a303-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="5a303-181">Main() et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="5a303-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="5a303-182">Mises en route de Visual Basic et Visual C#</span><span class="sxs-lookup"><span data-stu-id="5a303-182">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
