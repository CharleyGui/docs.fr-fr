---
title: Génération à partir de la ligne de commande avec csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789872"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="094c7-102">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="094c7-102">Command-line build with csc.exe</span></span>

<span data-ttu-id="094c7-103">Vous pouvez appeler le compilateur C# en tapant le nom de son fichier exécutable (*csc.exe*) dans une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="094c7-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="094c7-104">Si vous utilisez la fenêtre **Invite de commandes développeur pour Visual Studio**, toutes les variables d’environnement nécessaires sont définies automatiquement.</span><span class="sxs-lookup"><span data-stu-id="094c7-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="094c7-105">Pour plus d’informations sur la façon d’accéder à cet outil, consultez la rubrique [Invite de commandes développeur pour Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="094c7-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="094c7-106">Si vous utilisez une fenêtre d’invite de commandes standard, vous devez ajuster votre chemin avant de pouvoir appeler *csc.exe* à partir de n’importe quel sous-répertoire de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="094c7-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="094c7-107">Vous devez également exécuter *vsvars32.bat* pour définir les variables d’environnement appropriées pour prendre en charge les générations à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="094c7-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="094c7-108">Pour plus d’informations sur *vsvars32. bat*, y compris des instructions sur la façon de le Rechercher et de l’exécuter, consultez Guide pratique [pour définir des variables d’environnement pour la ligne de commande Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="094c7-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="094c7-109">Si vous utilisez un ordinateur disposant uniquement du Kit de développement logiciel (SDK) Windows, vous pouvez utiliser le compilateur C# dans l’**invite de commandes du kit SDK**, disponible à partir de l’option de menu **Microsoft .NET Framework SDK**.</span><span class="sxs-lookup"><span data-stu-id="094c7-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="094c7-110">Vous pouvez également utiliser MSBuild pour générer des programmes en C# par programmation.</span><span class="sxs-lookup"><span data-stu-id="094c7-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="094c7-111">Pour plus d’informations, consultez [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="094c7-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="094c7-112">Le fichier exécutable *csc.exe* se trouve généralement dans le dossier Microsoft.NET\Framework\\ *\<Version>* sous le répertoire *Windows*.</span><span class="sxs-lookup"><span data-stu-id="094c7-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="094c7-113">Son emplacement peut varier en fonction de la configuration exacte de l’ordinateur utilisé.</span><span class="sxs-lookup"><span data-stu-id="094c7-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="094c7-114">Si plusieurs versions du .NET Framework sont installées sur votre ordinateur, vous trouverez plusieurs versions de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="094c7-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="094c7-115">Pour plus d’informations sur ces installations, consultez [Guide pratique pour déterminer les versions installées du .NET Framework](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="094c7-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="094c7-116">Quand vous générez un projet à l’aide de l’IDE de Visual Studio, vous pouvez introduire la commande **csc** et ses options de compilation associées dans la fenêtre **Sortie**.</span><span class="sxs-lookup"><span data-stu-id="094c7-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="094c7-117">Pour afficher ces informations, suivez les instructions figurant dans [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) pour définir le niveau de détail des données de journal sur **Normal** ou **Détaillé**.</span><span class="sxs-lookup"><span data-stu-id="094c7-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="094c7-118">Après avoir régénéré votre projet, recherchez **csc** dans la fenêtre **Sortie** pour rechercher l’appel du compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="094c7-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="094c7-119">**Dans cette rubrique**</span><span class="sxs-lookup"><span data-stu-id="094c7-119">**In this topic**</span></span>

- [<span data-ttu-id="094c7-120">Règles de syntaxe de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="094c7-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="094c7-121">Exemples de lignes de commande</span><span class="sxs-lookup"><span data-stu-id="094c7-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="094c7-122">Différences entre les résultats de la compilation en C# et ceux de la compilation en C++</span><span class="sxs-lookup"><span data-stu-id="094c7-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="094c7-123">Règles de syntaxe de ligne de commande pour le compilateur C#</span><span class="sxs-lookup"><span data-stu-id="094c7-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="094c7-124">Le compilateur C# utilise les règles suivantes quand il interprète les arguments spécifiés dans la ligne de commande du système d’exploitation :</span><span class="sxs-lookup"><span data-stu-id="094c7-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="094c7-125">Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.</span><span class="sxs-lookup"><span data-stu-id="094c7-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="094c7-126">Le signe insertion (^) n’est pas reconnu comme caractère d’échappement ni comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="094c7-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="094c7-127">Ce caractère est traité par l’analyseur de ligne de commande du système d’exploitation avant d’être passé au tableau `argv` du programme.</span><span class="sxs-lookup"><span data-stu-id="094c7-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="094c7-128">Une chaîne placée entre guillemets doubles ("chaîne") est interprétée comme un argument unique, quels que soient les espaces blancs inclus.</span><span class="sxs-lookup"><span data-stu-id="094c7-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="094c7-129">Une chaîne entre guillemets peut être incorporée dans un argument.</span><span class="sxs-lookup"><span data-stu-id="094c7-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="094c7-130">Un guillemet double précédé d’une barre oblique inverse (\\") est interprété comme un caractère guillemet double littéral (").</span><span class="sxs-lookup"><span data-stu-id="094c7-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="094c7-131">Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.</span><span class="sxs-lookup"><span data-stu-id="094c7-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="094c7-132">Si un nombre pair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le tableau `argv` pour chaque paire de barres obliques inverses, et le guillemet double est interprété comme un délimiteur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="094c7-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="094c7-133">Si un nombre impair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le tableau `argv` pour chaque paire de barres obliques inverses, et le guillemet double est « ignoré » en raison de la barre oblique inverse restante.</span><span class="sxs-lookup"><span data-stu-id="094c7-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="094c7-134">Cela entraîne l’ajout d’un guillemet double littéral (") dans le tableau `argv`.</span><span class="sxs-lookup"><span data-stu-id="094c7-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="094c7-135">Exemples de lignes de commande pour le compilateur C#</span><span class="sxs-lookup"><span data-stu-id="094c7-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="094c7-136">Compile *File.cs*, ce qui produit *File.exe* :</span><span class="sxs-lookup"><span data-stu-id="094c7-136">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="094c7-137">Compile *File.cs*, ce qui produit *File.dll* :</span><span class="sxs-lookup"><span data-stu-id="094c7-137">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="094c7-138">Compile *File.cs* et crée *My.exe* :</span><span class="sxs-lookup"><span data-stu-id="094c7-138">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="094c7-139">Compile tous les fichiers C# du répertoire actif avec les optimisations activées et définit le symbole DEBUG.</span><span class="sxs-lookup"><span data-stu-id="094c7-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="094c7-140">La sortie est *File2.exe* :</span><span class="sxs-lookup"><span data-stu-id="094c7-140">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="094c7-141">Compile tous les fichiers C# du répertoire actif, ce qui produit une version Debug de *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="094c7-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="094c7-142">Aucun logo ni aucun avertissement n’est affiché :</span><span class="sxs-lookup"><span data-stu-id="094c7-142">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="094c7-143">Compile tous les fichiers C# du répertoire actif vers *Something.xyz* (une DLL) :</span><span class="sxs-lookup"><span data-stu-id="094c7-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="094c7-144">Différences entre les résultats de la compilation en C# et ceux de la compilation en C++</span><span class="sxs-lookup"><span data-stu-id="094c7-144">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="094c7-145">Aucun fichier objet ( *.obj*) n’est créé par l’appel du compilateur C#. Les fichiers de sortie sont créés directement.</span><span class="sxs-lookup"><span data-stu-id="094c7-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="094c7-146">Le compilateur C# n’a donc pas besoin d’un éditeur de liens.</span><span class="sxs-lookup"><span data-stu-id="094c7-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="094c7-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="094c7-147">See also</span></span>

- [<span data-ttu-id="094c7-148">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="094c7-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="094c7-149">Options du compilateur C# par ordre alphabétique</span><span class="sxs-lookup"><span data-stu-id="094c7-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="094c7-150">Options du compilateur C# par catégorie</span><span class="sxs-lookup"><span data-stu-id="094c7-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="094c7-151">Main() et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="094c7-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="094c7-152">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="094c7-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="094c7-153">Comment afficher les arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="094c7-153">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="094c7-154">Valeurs de retour Main()</span><span class="sxs-lookup"><span data-stu-id="094c7-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
