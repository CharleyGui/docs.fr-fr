---
title: manipulation de fichiers à l’aide de méthodes .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333785"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="23007-102">Procédure pas à pas : manipulation de fichiers à l'aide de méthodes du .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23007-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="23007-103">Cette procédure pas à pas illustre comment ouvrir et lire un fichier à l’aide de la classe <xref:System.IO.StreamReader>, vérifier si une tentative d’accès à un fichier est en cours, rechercher une chaîne dans un fichier lu avec une instance de la classe <xref:System.IO.StreamReader> et écrire dans un fichier à l’aide de la classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="23007-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="23007-104">Création de l’application</span><span class="sxs-lookup"><span data-stu-id="23007-104">Creating the Application</span></span>

<span data-ttu-id="23007-105">Démarrez Visual Studio et commencez le projet par la création d’un formulaire qui permet à l’utilisateur d’écrire dans le fichier désigné.</span><span class="sxs-lookup"><span data-stu-id="23007-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="23007-106">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="23007-106">To create the project</span></span>

1. <span data-ttu-id="23007-107">Dans le menu **Fichier**, sélectionnez **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="23007-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="23007-108">Dans le volet **Nouveau projet**, cliquez sur **Application Windows**.</span><span class="sxs-lookup"><span data-stu-id="23007-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="23007-109">Dans la zone **nom** , `MyDiary` tapez, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23007-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="23007-110">Visual Studio ajoute le projet à **Explorateur de solutions**et le **Concepteur Windows Forms** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="23007-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="23007-111">Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.</span><span class="sxs-lookup"><span data-stu-id="23007-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="23007-112">**Dessin**</span><span class="sxs-lookup"><span data-stu-id="23007-112">**Object**</span></span>|<span data-ttu-id="23007-113">**Propriétés**</span><span class="sxs-lookup"><span data-stu-id="23007-113">**Properties**</span></span>|<span data-ttu-id="23007-114">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="23007-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="23007-115">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-115">**Name**</span></span><br /><br /> <span data-ttu-id="23007-116">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="23007-117">**Envoyer l’entrée**</span><span class="sxs-lookup"><span data-stu-id="23007-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="23007-118">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-118">**Name**</span></span><br /><br /> <span data-ttu-id="23007-119">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="23007-120">**Effacer l’entrée**</span><span class="sxs-lookup"><span data-stu-id="23007-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="23007-121">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-121">**Name**</span></span><br /><br /> <span data-ttu-id="23007-122">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-122">**Text**</span></span><br /><br /> <span data-ttu-id="23007-123">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="23007-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="23007-124">**Saisissez quelque chose.**</span><span class="sxs-lookup"><span data-stu-id="23007-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="23007-125">Écriture dans le fichier</span><span class="sxs-lookup"><span data-stu-id="23007-125">Writing to the File</span></span>

<span data-ttu-id="23007-126">Pour permettre l’écriture dans un fichier via l’application, utilisez la classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="23007-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="23007-127">La classe <xref:System.IO.StreamWriter> est conçue pour la sortie de caractères dans un encodage particulier, tandis que la classe <xref:System.IO.Stream> est conçue pour l’entrée et la sortie d’octets.</span><span class="sxs-lookup"><span data-stu-id="23007-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="23007-128">Utilisez <xref:System.IO.StreamWriter> pour écrire des lignes d’informations dans un fichier texte standard.</span><span class="sxs-lookup"><span data-stu-id="23007-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="23007-129">Pour plus d’informations sur la classe <xref:System.IO.StreamWriter>, consultez <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="23007-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="23007-130">Pour ajouter une fonctionnalité d’écriture</span><span class="sxs-lookup"><span data-stu-id="23007-130">To add writing functionality</span></span>

1. <span data-ttu-id="23007-131">Dans le menu **Affichage**, choisissez **Code** pour ouvrir l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="23007-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="23007-132">Étant donné que l’application référence l’espace de noms <xref:System.IO>, ajoutez les instructions ci-après tout au début de votre code, avant la déclaration de classe du formulaire, `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="23007-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="23007-133">Avant d’écrire dans le fichier, vous devez créer une instance d’une classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="23007-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="23007-134">Dans le menu **Affichage**, choisissez **Concepteur** pour retourner au **Concepteur Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="23007-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="23007-135">Double-cliquez sur le bouton `Submit` pour créer un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour ce bouton, puis ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="23007-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="23007-136">L’environnement de développement intégré (IDE, Integrated Development Environment) Visual Studio revient à l’éditeur de code et positionne le point d’insertion dans le gestionnaire d’événements, à l’emplacement où vous devez ajouter le code.</span><span class="sxs-lookup"><span data-stu-id="23007-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="23007-137">Pour écrire dans le fichier, utilisez la méthode <xref:System.IO.StreamWriter.Write%2A> de la classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="23007-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="23007-138">Ajoutez le code ci-dessous immédiatement après `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="23007-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="23007-139">La levée d’une exception en cas de fichier introuvable ne doit pas vous inquiéter, car le fichier est créé s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="23007-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="23007-140">Vérifiez que l’utilisateur ne peut soumettre aucune entrée vide en ajoutant le code suivant immédiatement après `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="23007-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="23007-141">Comme il s’agit d’un agenda, l’utilisateur veut assigner une date à chaque entrée.</span><span class="sxs-lookup"><span data-stu-id="23007-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="23007-142">Insérez le code suivant après `fw = New StreamWriter("C:\MyDiary.txt", True)` pour affecter la date actuelle à la variable `Today`.</span><span class="sxs-lookup"><span data-stu-id="23007-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="23007-143">Pour finir, attachez le code pour effacer <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="23007-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="23007-144">Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Clear`.</span><span class="sxs-lookup"><span data-stu-id="23007-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="23007-145">Ajout de fonctionnalités d’affichage à l’agenda</span><span class="sxs-lookup"><span data-stu-id="23007-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="23007-146">Dans cette section, vous ajoutez une fonctionnalité qui affiche la dernière entrée dans le contrôle `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="23007-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="23007-147">Vous pouvez également ajouter un <xref:System.Windows.Forms.ComboBox> qui affiche différentes entrées et à partir duquel un utilisateur peut sélectionner une entrée à afficher dans le `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="23007-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="23007-148">Une instance de la classe <xref:System.IO.StreamReader> lit à partir de `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="23007-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="23007-149">Comme la classe <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader> est destiné à être utilisé avec des fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="23007-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="23007-150">Pour cette section de la procédure pas à pas, ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.</span><span class="sxs-lookup"><span data-stu-id="23007-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="23007-151">Control</span><span class="sxs-lookup"><span data-stu-id="23007-151">Control</span></span>|<span data-ttu-id="23007-152">Propriétés</span><span class="sxs-lookup"><span data-stu-id="23007-152">Properties</span></span>|<span data-ttu-id="23007-153">Valeurs</span><span class="sxs-lookup"><span data-stu-id="23007-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="23007-154">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-154">**Name**</span></span><br /><br /> <span data-ttu-id="23007-155">**Parent**</span><span class="sxs-lookup"><span data-stu-id="23007-155">**Visible**</span></span><br /><br /> <span data-ttu-id="23007-156">**Taille**</span><span class="sxs-lookup"><span data-stu-id="23007-156">**Size**</span></span><br /><br /> <span data-ttu-id="23007-157">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="23007-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="23007-158">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-158">**Name**</span></span><br /><br /> <span data-ttu-id="23007-159">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="23007-160">**Affichage**</span><span class="sxs-lookup"><span data-stu-id="23007-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="23007-161">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-161">**Name**</span></span><br /><br /> <span data-ttu-id="23007-162">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="23007-163">**Obtenir des entrées**</span><span class="sxs-lookup"><span data-stu-id="23007-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="23007-164">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-164">**Name**</span></span><br /><br /> <span data-ttu-id="23007-165">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-165">**Text**</span></span><br /><br /> <span data-ttu-id="23007-166">**Activé**</span><span class="sxs-lookup"><span data-stu-id="23007-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="23007-167">**Sélectionner une entrée**</span><span class="sxs-lookup"><span data-stu-id="23007-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="23007-168">Pour remplir la zone de liste déroulante</span><span class="sxs-lookup"><span data-stu-id="23007-168">To populate the combo box</span></span>

1. <span data-ttu-id="23007-169">Le contrôle `PickEntries`<xref:System.Windows.Forms.ComboBox> permet d’afficher les dates auxquelles un utilisateur soumet une entrée. Ainsi, celui-ci peut sélectionner une entrée associée à une date déterminée.</span><span class="sxs-lookup"><span data-stu-id="23007-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="23007-170">Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> au bouton `GetEntries` et ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="23007-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="23007-171">Pour tester votre code, appuyez sur F5 pour compiler l’application, puis cliquez sur **Obtenir des entrées**.</span><span class="sxs-lookup"><span data-stu-id="23007-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="23007-172">Cliquez sur la flèche déroulante dans le <xref:System.Windows.Forms.ComboBox> pour afficher les dates d’entrée.</span><span class="sxs-lookup"><span data-stu-id="23007-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="23007-173">Pour sélectionner et afficher des entrées individuelles</span><span class="sxs-lookup"><span data-stu-id="23007-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="23007-174">Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `Display` et ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="23007-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="23007-175">Pour tester votre code, appuyez sur F5 pour compiler l’application, puis soumettez une entrée.</span><span class="sxs-lookup"><span data-stu-id="23007-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="23007-176">Cliquez sur **Obtenir des entrées**, sélectionnez une entrée dans le <xref:System.Windows.Forms.ComboBox>, puis cliquez sur **Afficher**.</span><span class="sxs-lookup"><span data-stu-id="23007-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="23007-177">Le contenu de l’entrée sélectionnée s’affiche dans le `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="23007-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="23007-178">Autorisation aux utilisateurs de supprimer ou de modifier des entrées</span><span class="sxs-lookup"><span data-stu-id="23007-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="23007-179">Enfin, vous pouvez inclure des fonctionnalités supplémentaires qui permettent aux utilisateurs de supprimer ou de modifier une entrée à l’aide des boutons `DeleteEntry` et `EditEntry`.</span><span class="sxs-lookup"><span data-stu-id="23007-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="23007-180">Ces deux boutons restent désactivés si aucune entrée n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="23007-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="23007-181">Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.</span><span class="sxs-lookup"><span data-stu-id="23007-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="23007-182">Control</span><span class="sxs-lookup"><span data-stu-id="23007-182">Control</span></span>|<span data-ttu-id="23007-183">Propriétés</span><span class="sxs-lookup"><span data-stu-id="23007-183">Properties</span></span>|<span data-ttu-id="23007-184">Valeurs</span><span class="sxs-lookup"><span data-stu-id="23007-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="23007-185">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-185">**Name**</span></span><br /><br /> <span data-ttu-id="23007-186">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-186">**Text**</span></span><br /><br /> <span data-ttu-id="23007-187">**Activé**</span><span class="sxs-lookup"><span data-stu-id="23007-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="23007-188">**Supprimer l’entrée**</span><span class="sxs-lookup"><span data-stu-id="23007-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="23007-189">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-189">**Name**</span></span><br /><br /> <span data-ttu-id="23007-190">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-190">**Text**</span></span><br /><br /> <span data-ttu-id="23007-191">**Activé**</span><span class="sxs-lookup"><span data-stu-id="23007-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="23007-192">**Modifier l’entrée**</span><span class="sxs-lookup"><span data-stu-id="23007-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="23007-193">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23007-193">**Name**</span></span><br /><br /> <span data-ttu-id="23007-194">**Text**</span><span class="sxs-lookup"><span data-stu-id="23007-194">**Text**</span></span><br /><br /> <span data-ttu-id="23007-195">**Activé**</span><span class="sxs-lookup"><span data-stu-id="23007-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="23007-196">**Envoyer la modification**</span><span class="sxs-lookup"><span data-stu-id="23007-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="23007-197">Pour activer la suppression et la modification d’entrées</span><span class="sxs-lookup"><span data-stu-id="23007-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="23007-198">Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Display`, après `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="23007-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="23007-199">Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `DeleteEntry` et ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="23007-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="23007-200">Quand un utilisateur affiche une entrée, le bouton `EditEntry` devient disponible.</span><span class="sxs-lookup"><span data-stu-id="23007-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="23007-201">Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Display` après `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="23007-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="23007-202">Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `EditEntry` et ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="23007-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="23007-203">Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `SubmitEdit` et ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="23007-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="23007-204">Pour tester votre code, appuyez sur F5 pour compiler l’application.</span><span class="sxs-lookup"><span data-stu-id="23007-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="23007-205">Cliquez sur **Obtenir des entrées**, sélectionnez une entrée, puis cliquez sur **Afficher**.</span><span class="sxs-lookup"><span data-stu-id="23007-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="23007-206">L’entrée s’affiche dans le `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="23007-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="23007-207">Cliquez sur **Modifier l’entrée**.</span><span class="sxs-lookup"><span data-stu-id="23007-207">Click **Edit Entry**.</span></span> <span data-ttu-id="23007-208">L’entrée s’affiche dans le `Entry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="23007-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="23007-209">Modifiez l’entrée dans le `Entry` <xref:System.Windows.Forms.TextBox> , puis cliquez sur **Envoyer la modification**.</span><span class="sxs-lookup"><span data-stu-id="23007-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="23007-210">Ouvrez le fichier `MyDiary.txt` pour confirmer vos corrections.</span><span class="sxs-lookup"><span data-stu-id="23007-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="23007-211">À présent, sélectionnez une entrée et cliquez sur **Supprimer l’entrée**.</span><span class="sxs-lookup"><span data-stu-id="23007-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="23007-212">Quand le <xref:System.Windows.Forms.MessageBox> demande confirmation, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23007-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="23007-213">Fermez l’application et ouvrez `MyDiary.txt` pour confirmer la suppression.</span><span class="sxs-lookup"><span data-stu-id="23007-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="23007-214">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23007-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="23007-215">Procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="23007-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
