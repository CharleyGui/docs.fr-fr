---
title: Manipulation de fichiers et de répertoires
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 4b77618e5cd525cf3ad012405f402681aa5bb52c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406662"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="d043f-102">Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d043f-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="d043f-103">Cette procédure pas à pas présente les notions de base d’E/S de fichier dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d043f-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="d043f-104">Elle décrit comment créer une petite application qui répertorie et examine des fichiers texte dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="d043f-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="d043f-105">Pour chaque fichier texte sélectionné, l’application fournit des attributs de fichier et la première ligne de contenu.</span><span class="sxs-lookup"><span data-stu-id="d043f-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="d043f-106">Elle comprend une option pour écrire des informations dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="d043f-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="d043f-107">Cette procédure pas à pas utilise des membres de `My.Computer.FileSystem Object`, qui sont disponibles dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d043f-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="d043f-108">Consultez la rubrique <xref:Microsoft.VisualBasic.FileIO.FileSystem> (éventuellement en anglais) pour plus d'informations.</span><span class="sxs-lookup"><span data-stu-id="d043f-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="d043f-109">À la fin de la procédure pas à pas, un exemple équivalent est fourni, qui utilise des classes de l’espace de noms <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="d043f-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="d043f-110">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="d043f-110">To create the project</span></span>  
  
1. <span data-ttu-id="d043f-111">Dans le menu **Fichier**, cliquez sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="d043f-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="d043f-112">La boîte de dialogue **Nouveau projet** apparaît.</span><span class="sxs-lookup"><span data-stu-id="d043f-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="d043f-113">Dans le volet **Modèles installés**, développez **Visual Basic**, puis cliquez sur **Windows**.</span><span class="sxs-lookup"><span data-stu-id="d043f-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="d043f-114">Dans le volet **Modèles** du milieu, cliquez sur **Application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="d043f-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="d043f-115">Dans la zone **Nom**, tapez `FileExplorer` pour définir le nom de projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d043f-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d043f-116">Visual Studio ajoute le projet à l’**Explorateur de solutions** et le concepteur Windows Forms s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="d043f-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="d043f-117">Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.</span><span class="sxs-lookup"><span data-stu-id="d043f-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="d043f-118">Control</span><span class="sxs-lookup"><span data-stu-id="d043f-118">Control</span></span>|<span data-ttu-id="d043f-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="d043f-119">Property</span></span>|<span data-ttu-id="d043f-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="d043f-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="d043f-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="d043f-121">**ListBox**</span></span>|<span data-ttu-id="d043f-122">**Nom**</span><span class="sxs-lookup"><span data-stu-id="d043f-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="d043f-123">**Button**</span><span class="sxs-lookup"><span data-stu-id="d043f-123">**Button**</span></span>|<span data-ttu-id="d043f-124">**Nom**</span><span class="sxs-lookup"><span data-stu-id="d043f-124">**Name**</span></span><br /><br /> <span data-ttu-id="d043f-125">**Texte**</span><span class="sxs-lookup"><span data-stu-id="d043f-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="d043f-126">**Parcourir**</span><span class="sxs-lookup"><span data-stu-id="d043f-126">**Browse**</span></span>|  
    |<span data-ttu-id="d043f-127">**Button**</span><span class="sxs-lookup"><span data-stu-id="d043f-127">**Button**</span></span>|<span data-ttu-id="d043f-128">**Nom**</span><span class="sxs-lookup"><span data-stu-id="d043f-128">**Name**</span></span><br /><br /> <span data-ttu-id="d043f-129">**Texte**</span><span class="sxs-lookup"><span data-stu-id="d043f-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="d043f-130">**Examiner**</span><span class="sxs-lookup"><span data-stu-id="d043f-130">**Examine**</span></span>|  
    |<span data-ttu-id="d043f-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="d043f-131">**CheckBox**</span></span>|<span data-ttu-id="d043f-132">**Nom**</span><span class="sxs-lookup"><span data-stu-id="d043f-132">**Name**</span></span><br /><br /> <span data-ttu-id="d043f-133">**Texte**</span><span class="sxs-lookup"><span data-stu-id="d043f-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="d043f-134">**Enregistrer les résultats**</span><span class="sxs-lookup"><span data-stu-id="d043f-134">**Save Results**</span></span>|  
    |<span data-ttu-id="d043f-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="d043f-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="d043f-136">**Nom**</span><span class="sxs-lookup"><span data-stu-id="d043f-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="d043f-137">Pour sélectionner un dossier et répertorier les fichiers dans un dossier</span><span class="sxs-lookup"><span data-stu-id="d043f-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="d043f-138">Créez un gestionnaire d’événements `Click` pour `browseButton` en double-cliquant sur le contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d043f-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="d043f-139">L'éditeur de code s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="d043f-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="d043f-140">Ajoutez le code ci-après au gestionnaire d'événements `Click`.</span><span class="sxs-lookup"><span data-stu-id="d043f-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="d043f-141">L’appel de `FolderBrowserDialog1.ShowDialog` ouvre la boîte de dialogue **Rechercher un dossier**.</span><span class="sxs-lookup"><span data-stu-id="d043f-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="d043f-142">Une fois que l’utilisateur a cliqué sur **OK**, la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> est envoyée en tant qu’argument à la méthode `ListFiles`, qui est ajoutée à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="d043f-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="d043f-143">Ajoutez la méthode `ListFiles` suivante.</span><span class="sxs-lookup"><span data-stu-id="d043f-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="d043f-144">Ce code efface d’abord le contrôle **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="d043f-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="d043f-145">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> récupère ensuite une collection de chaînes, une pour chaque fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="d043f-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="d043f-146">La méthode `GetFiles` accepte un argument de modèle de recherche pour récupérer les fichiers qui correspondent à un modèle particulier.</span><span class="sxs-lookup"><span data-stu-id="d043f-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="d043f-147">Dans cet exemple, seuls les fichiers ayant l’extension .txt sont retournés.</span><span class="sxs-lookup"><span data-stu-id="d043f-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="d043f-148">Les chaînes qui sont retournées par la méthode `GetFiles` sont ensuite ajoutées à **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="d043f-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="d043f-149">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d043f-149">Run the application.</span></span> <span data-ttu-id="d043f-150">Cliquez sur le bouton **Parcourir** .</span><span class="sxs-lookup"><span data-stu-id="d043f-150">Click the **Browse** button.</span></span> <span data-ttu-id="d043f-151">Dans la boîte de dialogue **Rechercher un dossier**, accédez à un dossier qui contient des fichiers .txt, puis sélectionnez le dossier et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d043f-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="d043f-152">`ListBox` contient une liste des fichiers.txt du dossier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d043f-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="d043f-153">Arrêtez l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="d043f-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="d043f-154">Pour obtenir les attributs d’un fichier et le contenu d’un fichier texte</span><span class="sxs-lookup"><span data-stu-id="d043f-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="d043f-155">Créez un gestionnaire d’événements `Click` pour `examineButton` en double-cliquant sur le contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d043f-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="d043f-156">Ajoutez le code ci-après au gestionnaire d'événements `Click`.</span><span class="sxs-lookup"><span data-stu-id="d043f-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="d043f-157">Le code vérifie qu’un élément est sélectionné dans le contrôle `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d043f-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="d043f-158">Il obtient ensuite l’entrée du chemin du fichier à partir de `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d043f-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="d043f-159">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> est utilisée pour vérifier si le fichier existe toujours.</span><span class="sxs-lookup"><span data-stu-id="d043f-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="d043f-160">Le chemin du fichier est envoyé en tant qu’argument à la méthode `GetTextForOutput`, qui est ajoutée à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="d043f-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="d043f-161">Cette méthode retourne une chaîne qui contient des informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="d043f-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="d043f-162">Les informations sur le fichier s’affichent dans un élément **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="d043f-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="d043f-163">Ajoutez la méthode `GetTextForOutput` suivante.</span><span class="sxs-lookup"><span data-stu-id="d043f-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="d043f-164">Le code utilise la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> pour obtenir des paramètres de fichier.</span><span class="sxs-lookup"><span data-stu-id="d043f-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="d043f-165">Les paramètres de fichier sont ajoutés à un <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="d043f-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="d043f-166">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lit le contenu du fichier dans un <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="d043f-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="d043f-167">La première ligne du contenu est obtenue à partir du `StreamReader` et est ajoutée au `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="d043f-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="d043f-168">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d043f-168">Run the application.</span></span> <span data-ttu-id="d043f-169">Cliquez sur **Parcourir** et recherchez un dossier qui contient des fichiers .txt.</span><span class="sxs-lookup"><span data-stu-id="d043f-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="d043f-170">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d043f-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="d043f-171">Sélectionnez un fichier dans le contrôle `ListBox`, puis cliquez sur **Examiner**.</span><span class="sxs-lookup"><span data-stu-id="d043f-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="d043f-172">`MessageBox` affiche les informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="d043f-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="d043f-173">Arrêtez l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="d043f-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="d043f-174">Pour ajouter une entrée de journal</span><span class="sxs-lookup"><span data-stu-id="d043f-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="d043f-175">Ajoutez le code suivant à la fin du gestionnaire d’événements `examineButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="d043f-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="d043f-176">Le code définit le chemin du fichier journal de sorte que ce dernier soit placé dans le même répertoire que celui du fichier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d043f-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="d043f-177">Le texte de l’entrée de journal prend comme valeur la date et l’heure actuelles, suivies des informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="d043f-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="d043f-178">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, avec l’argument `append` défini sur `True`, est utilisée pour créer l’entrée de journal.</span><span class="sxs-lookup"><span data-stu-id="d043f-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="d043f-179">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d043f-179">Run the application.</span></span> <span data-ttu-id="d043f-180">Accédez à un fichier texte, sélectionnez-le dans le contrôle `ListBox`, cochez la case **Enregistrer les résultats**, puis cliquez sur **Examiner**.</span><span class="sxs-lookup"><span data-stu-id="d043f-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="d043f-181">Vérifiez que l’entrée de journal est écrite dans le fichier `log.txt`.</span><span class="sxs-lookup"><span data-stu-id="d043f-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="d043f-182">Arrêtez l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="d043f-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="d043f-183">Pour utiliser le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="d043f-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="d043f-184">Créez un gestionnaire d’événements pour `Form1_Load` en double-cliquant sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d043f-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="d043f-185">Ajoutez le code suivant au gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d043f-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="d043f-186">Ce code définit le répertoire actif comme le répertoire par défaut de l’Explorateur de dossiers.</span><span class="sxs-lookup"><span data-stu-id="d043f-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="d043f-187">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d043f-187">Run the application.</span></span> <span data-ttu-id="d043f-188">Quand vous cliquez pour la première fois sur **Parcourir**, la boîte de dialogue **Rechercher un dossier** affiche le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d043f-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="d043f-189">Arrêtez l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="d043f-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="d043f-190">Pour activer des contrôles de manière sélective</span><span class="sxs-lookup"><span data-stu-id="d043f-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="d043f-191">Ajoutez la méthode `SetEnabled` suivante.</span><span class="sxs-lookup"><span data-stu-id="d043f-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="d043f-192">La méthode `SetEnabled` active ou désactive les contrôles, selon qu’un élément est sélectionné ou non dans le contrôle `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d043f-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="d043f-193">Créez un gestionnaire d’événements `SelectedIndexChanged` pour `filesListBox` en double-cliquant sur le contrôle `ListBox` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d043f-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="d043f-194">Ajoutez un appel à `SetEnabled` dans le nouveau gestionnaire d’événements `filesListBox_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="d043f-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="d043f-195">Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d’événements `browseButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="d043f-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="d043f-196">Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d’événements `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="d043f-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="d043f-197">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d043f-197">Run the application.</span></span> <span data-ttu-id="d043f-198">La case **Enregistrer les résultats** et le bouton **Examiner** sont désactivés si aucun élément n’est sélectionné dans le contrôle `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d043f-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="d043f-199">Exemple complet de l’utilisation de My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="d043f-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="d043f-200">L’exemple complet se trouve ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d043f-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="d043f-201">Exemple complet de l’utilisation de System.IO</span><span class="sxs-lookup"><span data-stu-id="d043f-201">Full example using System.IO</span></span>  

 <span data-ttu-id="d043f-202">L’exemple équivalent suivant utilise des classes de l’espace de noms <xref:System.IO> au lieu d’utiliser des objets `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="d043f-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="d043f-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d043f-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="d043f-204">Procédure pas à pas : manipulation de fichiers à l’aide de méthodes .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d043f-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](walkthrough-manipulating-files-by-using-net-framework-methods.md)
