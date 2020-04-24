---
title: 'Comment : appeler le compilateur de ligne de commande'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344257"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="a6e10-102">Comment : appeler le compilateur de ligne de commande (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6e10-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="a6e10-103">Vous pouvez appeler le compilateur de ligne de commande en tapant le nom de son fichier exécutable dans la ligne de commande, également appelée invite MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="a6e10-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="a6e10-104">Si vous compilez à partir de l’invite de commandes Windows par défaut, vous devez taper le chemin d’accès complet au fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="a6e10-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="a6e10-105">Pour remplacer ce comportement par défaut, vous pouvez utiliser l’Invite de commandes développeur pour Visual Studio ou modifier la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="a6e10-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="a6e10-106">Tous deux vous permettent de compiler à partir de n’importe quel répertoire en tapant simplement le nom du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a6e10-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="a6e10-107">Pour appeler le compilateur à l’aide de l’Invite de commandes développeur pour Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a6e10-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="a6e10-108">Ouvrez le dossier Program Visual Studio Tools dans le groupe de programmes Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a6e10-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="a6e10-109">Vous pouvez utiliser le Invite de commandes développeur pour Visual Studio pour accéder au compilateur à partir de n’importe quel répertoire sur votre ordinateur, si Visual Studio est installé.</span><span class="sxs-lookup"><span data-stu-id="a6e10-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="a6e10-110">Appelez le Invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a6e10-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="a6e10-111">Sur la ligne de commande, `vbc.exe` tapez *sourceFileName* , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="a6e10-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="a6e10-112">Par exemple, si vous avez stocké votre code source dans un `SourceFiles`répertoire appelé, vous ouvrez l’invite de commandes `cd SourceFiles` et tapez pour changer ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="a6e10-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="a6e10-113">Si le répertoire contient un fichier source nommé `Source.vb`, vous pouvez le compiler en tapant `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="a6e10-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="a6e10-114">Pour définir la variable d’environnement PATH sur le compilateur de l’invite de commandes Windows</span><span class="sxs-lookup"><span data-stu-id="a6e10-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="a6e10-115">Utilisez la fonctionnalité de recherche Windows pour rechercher vbc. exe sur votre disque local.</span><span class="sxs-lookup"><span data-stu-id="a6e10-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="a6e10-116">Le nom exact du répertoire dans lequel se trouve le compilateur dépend de l’emplacement du répertoire Windows et de la version de « .NET Framework » installée.</span><span class="sxs-lookup"><span data-stu-id="a6e10-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="a6e10-117">Si vous avez plus d’une version de « .NET Framework » installée, vous devez déterminer la version à utiliser (généralement la dernière version).</span><span class="sxs-lookup"><span data-stu-id="a6e10-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="a6e10-118">Dans le menu **Démarrer** , cliquez avec le bouton droit sur **poste de travail**, puis cliquez sur **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="a6e10-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="a6e10-119">Cliquez sous l'onglet **Avancé**, puis sur **Variables d'environnement**.</span><span class="sxs-lookup"><span data-stu-id="a6e10-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="a6e10-120">Dans le volet variables **système** , sélectionnez **path** dans la liste, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="a6e10-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="a6e10-121">Dans la boîte de dialogue Modifier la variable **système** , déplacez le point d’insertion à la fin de la chaîne dans le champ valeur de la **variable** et tapez un point-virgule (;) suivi du nom de répertoire complet trouvé à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="a6e10-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="a6e10-122">Cliquez sur **OK** pour confirmer vos modifications et fermer les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a6e10-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="a6e10-123">Après avoir modifié la variable d’environnement PATH, vous pouvez exécuter le compilateur Visual Basic à partir de l’invite de commandes Windows à partir de n’importe quel répertoire sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a6e10-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="a6e10-124">Pour appeler le compilateur à l’aide de l’invite de commandes Windows</span><span class="sxs-lookup"><span data-stu-id="a6e10-124">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="a6e10-125">Dans le menu **Démarrer** , cliquez sur le dossier **accessoires** , puis ouvrez l' **invite de commandes Windows**.</span><span class="sxs-lookup"><span data-stu-id="a6e10-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="a6e10-126">Sur la ligne de commande, `vbc.exe`tapez *sourceFileName* , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="a6e10-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="a6e10-127">Par exemple, si vous avez stocké votre code source dans un `SourceFiles`répertoire appelé, vous ouvrez l’invite de commandes `cd SourceFiles` et tapez pour changer ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="a6e10-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="a6e10-128">Si le répertoire contient un fichier source nommé `Source.vb`, vous pouvez le compiler en tapant `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="a6e10-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6e10-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6e10-129">See also</span></span>

- [<span data-ttu-id="a6e10-130">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6e10-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a6e10-131">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="a6e10-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
