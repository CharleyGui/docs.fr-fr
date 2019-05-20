---
title: Hello World -- Votre premier programme - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 62aaf8785b0dfb646ea804dab6918940f1e33346
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635277"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="cb10a-102">Hello World -- Votre premier programme (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="cb10a-102">Hello World -- Your first program (C# Programming Guide)</span></span>

<span data-ttu-id="cb10a-103">La procédure suivante crée une version C# du traditionnel programme « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="cb10a-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="cb10a-104">.</span><span class="sxs-lookup"><span data-stu-id="cb10a-104">program.</span></span> <span data-ttu-id="cb10a-105">Le programme affiche la chaîne `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="cb10a-105">The program displays the string `Hello World!`</span></span>

<span data-ttu-id="cb10a-106">Pour plus d’exemples concernant les concepts de base, consultez [Bien démarrer avec Visual Basic et Visual C#](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cb10a-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="cb10a-107">Pour créer et exécuter une application console</span><span class="sxs-lookup"><span data-stu-id="cb10a-107">To create and run a console application</span></span>

1. <span data-ttu-id="cb10a-108">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb10a-108">Start Visual Studio.</span></span>

2. <span data-ttu-id="cb10a-109">Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="cb10a-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="cb10a-110">La boîte de dialogue **Nouveau projet** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="cb10a-110">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="cb10a-111">Développez **Installé**, **Modèles**, **Visual C#**, puis choisissez **Application console**.</span><span class="sxs-lookup"><span data-stu-id="cb10a-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>

4. <span data-ttu-id="cb10a-112">Dans la zone de texte **Nom**, entrez un nom pour votre projet, puis choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb10a-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="cb10a-113">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="cb10a-113">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="cb10a-114">Si Program.cs n’est pas ouvert dans l’**Éditeur de Code**, ouvrez le menu contextuel de **Program.cs** dans **l’Explorateur de solutions**, puis choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="cb10a-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="cb10a-115">Remplacez le contenu de Program.cs par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="cb10a-115">Replace the contents of Program.cs with the following code.</span></span>

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. <span data-ttu-id="cb10a-116">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="cb10a-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="cb10a-117">Une fenêtre d’invite de commandes s’affiche avec la ligne `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="cb10a-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>

<span data-ttu-id="cb10a-118">Ensuite, les parties importantes de ce programme sont examinées.</span><span class="sxs-lookup"><span data-stu-id="cb10a-118">Next, the important parts of this program are examined.</span></span>

## <a name="comments"></a><span data-ttu-id="cb10a-119">Commentaires</span><span class="sxs-lookup"><span data-stu-id="cb10a-119">Comments</span></span>

<span data-ttu-id="cb10a-120">La première ligne contient un commentaire.</span><span class="sxs-lookup"><span data-stu-id="cb10a-120">The first line contains a comment.</span></span> <span data-ttu-id="cb10a-121">Les caractères `//` convertissent le reste de la ligne en un commentaire.</span><span class="sxs-lookup"><span data-stu-id="cb10a-121">The characters `//` convert the rest of the line to a comment.</span></span>

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="cb10a-122">Vous pouvez également créer un commentaire à partir d’un bloc de texte en le plaçant entre les caractères `/*` et `*/`.</span><span class="sxs-lookup"><span data-stu-id="cb10a-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="cb10a-123">L'exemple suivant le démontre.</span><span class="sxs-lookup"><span data-stu-id="cb10a-123">This is shown in the following example.</span></span>

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a><span data-ttu-id="cb10a-124">Main (méthode)</span><span class="sxs-lookup"><span data-stu-id="cb10a-124">Main method</span></span>

<span data-ttu-id="cb10a-125">Une application console C# doit contenir une méthode `Main`, dans laquelle le contrôle commence et termine.</span><span class="sxs-lookup"><span data-stu-id="cb10a-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="cb10a-126">C’est dans la méthode `Main` que vous créez des objets et exécutez d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="cb10a-126">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="cb10a-127">La méthode `Main` est une méthode [static](../../../csharp/language-reference/keywords/static.md) qui réside dans une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="cb10a-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="cb10a-128">Dans l’exemple « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="cb10a-128">In the previous "Hello World!"</span></span> <span data-ttu-id="cb10a-129">précédent, il réside dans une classe nommée `Hello`.</span><span class="sxs-lookup"><span data-stu-id="cb10a-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="cb10a-130">Vous pouvez déclarer la méthode `Main` de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb10a-130">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="cb10a-131">Elle peut retourner `void`.</span><span class="sxs-lookup"><span data-stu-id="cb10a-131">It can return `void`.</span></span>

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="cb10a-132">Elle peut également retourner un entier.</span><span class="sxs-lookup"><span data-stu-id="cb10a-132">It can also return an integer.</span></span>

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="cb10a-133">Elle peut accepter des arguments avec n’importe quel type de retour.</span><span class="sxs-lookup"><span data-stu-id="cb10a-133">With either of the return types, it can take arguments.</span></span>

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     <span data-ttu-id="cb10a-134">- ou -</span><span class="sxs-lookup"><span data-stu-id="cb10a-134">-or-</span></span>

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="cb10a-135">Le paramètre `args` de la méthode `Main` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme.</span><span class="sxs-lookup"><span data-stu-id="cb10a-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="cb10a-136">Contrairement au langage C++, le tableau n’inclut pas le nom du fichier exécutable (exe).</span><span class="sxs-lookup"><span data-stu-id="cb10a-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>

<span data-ttu-id="cb10a-137">Pour plus d’informations sur l’utilisation des arguments de ligne de commande, consultez les exemples des rubriques [Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md) et [Guide pratique pour créer et utiliser des assemblys à l’aide de la ligne de commande](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="cb10a-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

<span data-ttu-id="cb10a-138">L’appel à <xref:System.Console.ReadKey%2A> à la fin de la méthode `Main` empêche la fenêtre de console de se fermer avant que vous ayez pu lire la sortie quand vous exécutez votre programme en mode débogage, avec la touche F5.</span><span class="sxs-lookup"><span data-stu-id="cb10a-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>

## <a name="input-and-output"></a><span data-ttu-id="cb10a-139">Entrée et sortie</span><span class="sxs-lookup"><span data-stu-id="cb10a-139">Input and output</span></span>

<span data-ttu-id="cb10a-140">Les programmes C# utilisent généralement les services d’entrée/sortie fournis par la bibliothèque runtime du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb10a-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="cb10a-141">L’instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb10a-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="cb10a-142">C’est l’une des méthodes de sortie de la classe <xref:System.Console> de la bibliothèque runtime.</span><span class="sxs-lookup"><span data-stu-id="cb10a-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="cb10a-143">Elle affiche son paramètre de chaîne dans le flux de sortie standard suivi d’une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="cb10a-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="cb10a-144">D’autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="cb10a-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="cb10a-145">Si vous incluez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement.</span><span class="sxs-lookup"><span data-stu-id="cb10a-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="cb10a-146">Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="cb10a-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="cb10a-147">Pour plus d’informations sur les méthodes d’entrée/sortie, consultez <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="cb10a-147">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="cb10a-148">Compilation et exécution en ligne de commande</span><span class="sxs-lookup"><span data-stu-id="cb10a-148">Command-line compilation and execution</span></span>

<span data-ttu-id="cb10a-149">Vous pouvez compiler le programme « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="cb10a-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="cb10a-150">à l’aide de la ligne de commande au lieu de l’environnement de développement intégré (IDE) Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb10a-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>

### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="cb10a-151">Pour compiler et exécuter à partir d’une invite de commandes</span><span class="sxs-lookup"><span data-stu-id="cb10a-151">To compile and run from a command prompt</span></span>

1. <span data-ttu-id="cb10a-152">Copiez-collez le code de la procédure précédente dans un éditeur de texte, puis enregistrez le fichier en tant que fichier texte.</span><span class="sxs-lookup"><span data-stu-id="cb10a-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="cb10a-153">Nommez le fichier `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="cb10a-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="cb10a-154">Les fichiers de code source C# utilisent l’extension `.cs`.</span><span class="sxs-lookup"><span data-stu-id="cb10a-154">C# source code files use the extension `.cs`.</span></span>

2. <span data-ttu-id="cb10a-155">Effectuez l’une des opérations suivantes pour ouvrir une fenêtre d’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="cb10a-155">Perform one of the following steps to open a command-prompt window:</span></span>

    - <span data-ttu-id="cb10a-156">Dans Windows 10, dans le menu **Démarrer**, recherchez `Developer Command Prompt`, puis choisissez **Invite de commandes développeur pour VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="cb10a-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="cb10a-157">Une fenêtre d’invite de commandes développeur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cb10a-157">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="cb10a-158">Dans Windows 7, ouvrez le menu **Démarrer**, développez le dossier de la version actuelle de Visual Studio, ouvrez le menu contextuel de **Visual Studio Tools**, puis choisissez **Invite de commandes de développeur de VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="cb10a-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="cb10a-159">Une fenêtre d’invite de commandes développeur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cb10a-159">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="cb10a-160">Activez les générations en mode ligne de commande à partir d’une fenêtre d’invite de commandes standard.</span><span class="sxs-lookup"><span data-stu-id="cb10a-160">Enable command-line builds from a standard Command Prompt window.</span></span>

         <span data-ttu-id="cb10a-161">Voir [Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="cb10a-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

3. <span data-ttu-id="cb10a-162">Dans la fenêtre d’invite de commandes, accédez au dossier qui contient le fichier `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="cb10a-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>

4. <span data-ttu-id="cb10a-163">Entrez la commande suivante pour compiler `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="cb10a-163">Enter the following command to compile `Hello.cs`.</span></span>

     `csc Hello.cs`

     <span data-ttu-id="cb10a-164">Si votre programme ne contient pas d’erreurs de compilation, un fichier exécutable nommé `Hello.exe` est créé.</span><span class="sxs-lookup"><span data-stu-id="cb10a-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>

5. <span data-ttu-id="cb10a-165">Dans la fenêtre d’invite de commandes, entrez la commande suivante pour exécuter le programme :</span><span class="sxs-lookup"><span data-stu-id="cb10a-165">In the command-prompt window, enter the following command to run the program:</span></span>

     `Hello`

 <span data-ttu-id="cb10a-166">Pour plus d’informations sur le compilateur C# et ses options, consultez [Options du compilateur C #](../../../csharp/language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="cb10a-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb10a-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb10a-167">See also</span></span>

- [<span data-ttu-id="cb10a-168">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cb10a-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cb10a-169">À l’intérieur d’un programme C#</span><span class="sxs-lookup"><span data-stu-id="cb10a-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)
- [<span data-ttu-id="cb10a-170">Chaînes</span><span class="sxs-lookup"><span data-stu-id="cb10a-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
- [<span data-ttu-id="cb10a-171">Exemples et tutoriels</span><span class="sxs-lookup"><span data-stu-id="cb10a-171">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="cb10a-172">Référence C#</span><span class="sxs-lookup"><span data-stu-id="cb10a-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="cb10a-173">Main() et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="cb10a-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="cb10a-174">Mises en route de Visual Basic et Visual C#</span><span class="sxs-lookup"><span data-stu-id="cb10a-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
