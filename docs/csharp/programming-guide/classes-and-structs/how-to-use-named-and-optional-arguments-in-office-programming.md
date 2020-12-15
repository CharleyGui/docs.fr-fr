---
title: Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office-Guide de programmation C#
description: Découvrez comment utiliser des arguments nommés et des arguments facultatifs pour faciliter l’accès aux interfaces COM, telles que les API Microsoft Office Automation.
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: de0545131385c13a79fd35df74e3a04da98ad8fb
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512474"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="23850-103">Comment utiliser des arguments nommés et facultatifs dans la programmation Office (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="23850-103">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="23850-104">Les arguments nommés et les arguments facultatifs, qui ont été introduits avec C#4, rendent la programmation en C# plus pratique, plus souple et plus lisible.</span><span class="sxs-lookup"><span data-stu-id="23850-104">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="23850-105">De plus, ces fonctionnalités facilitent considérablement l’accès aux interfaces COM, telles que les API Microsoft Office Automation.</span><span class="sxs-lookup"><span data-stu-id="23850-105">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="23850-106">Dans l’exemple suivant, la méthode [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) a seize paramètres qui représentent les caractéristiques d’une table, comme le nombre de colonnes et de lignes, la mise en forme, les bordures, les polices et les couleurs.</span><span class="sxs-lookup"><span data-stu-id="23850-106">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="23850-107">Ces seize paramètres sont facultatifs, car la plupart du temps, il n’est pas nécessaire de spécifier des valeurs pour chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="23850-107">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="23850-108">Toutefois, en l’absence d’arguments nommés et facultatifs, une valeur ou une valeur d’espace réservé doit être fournie pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="23850-108">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="23850-109">Avec les arguments nommés et facultatifs, vous spécifiez des valeurs uniquement pour les paramètres qui sont nécessaires à votre projet.</span><span class="sxs-lookup"><span data-stu-id="23850-109">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="23850-110">Pour que vous puissiez effectuer ces procédures, Microsoft Office Word doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="23850-110">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="23850-111">Pour créer une application console</span><span class="sxs-lookup"><span data-stu-id="23850-111">To create a new console application</span></span>

1. <span data-ttu-id="23850-112">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="23850-112">Start Visual Studio.</span></span>

2. <span data-ttu-id="23850-113">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="23850-113">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="23850-114">Dans le volet **Catégories de modèles**, développez **Visual C#**, puis cliquez sur **Windows**.</span><span class="sxs-lookup"><span data-stu-id="23850-114">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="23850-115">Regardez en haut du volet **Modèles** pour vérifier que **.NET Framework 4**, ou version ultérieure, apparaît dans la zone **Framework cible**.</span><span class="sxs-lookup"><span data-stu-id="23850-115">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="23850-116">Dans le volet **Modèles**, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="23850-116">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="23850-117">Attribuez un nom à votre projet dans le champ **Nom**.</span><span class="sxs-lookup"><span data-stu-id="23850-117">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="23850-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23850-118">Click **OK**.</span></span>

     <span data-ttu-id="23850-119">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="23850-119">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="23850-120">Pour ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="23850-120">To add a reference</span></span>

1. <span data-ttu-id="23850-121">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="23850-121">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="23850-122">La boîte de dialogue **Ajouter une référence** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="23850-122">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="23850-123">Dans la page **.NET**, sélectionnez **Microsoft.Office.Interop.Word** dans la liste **Nom du composant**.</span><span class="sxs-lookup"><span data-stu-id="23850-123">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="23850-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23850-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="23850-125">Pour ajouter les directives using nécessaires</span><span class="sxs-lookup"><span data-stu-id="23850-125">To add necessary using directives</span></span>

1. <span data-ttu-id="23850-126">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Program.cs*, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="23850-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="23850-127">Ajoutez les `using` directives suivantes en haut du fichier de code :</span><span class="sxs-lookup"><span data-stu-id="23850-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="23850-128">Pour afficher du texte dans un document Word</span><span class="sxs-lookup"><span data-stu-id="23850-128">To display text in a Word document</span></span>

1. <span data-ttu-id="23850-129">Dans la `Program` classe de *Program.cs*, ajoutez la méthode suivante pour créer une application Word et un document Word.</span><span class="sxs-lookup"><span data-stu-id="23850-129">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="23850-130">La méthode [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) comprend quatre paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="23850-130">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="23850-131">Cet exemple utilise leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="23850-131">This example uses their default values.</span></span> <span data-ttu-id="23850-132">Par conséquent, aucun argument n’est nécessaire dans l’instruction appelante.</span><span class="sxs-lookup"><span data-stu-id="23850-132">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="23850-133">Ajoutez le code suivant à la fin de la méthode pour définir l’emplacement d’affichage du texte dans le document et le texte à afficher :</span><span class="sxs-lookup"><span data-stu-id="23850-133">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="23850-134">Pour exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="23850-134">To run the application</span></span>

1. <span data-ttu-id="23850-135">Ajoutez l’instruction suivante à main :</span><span class="sxs-lookup"><span data-stu-id="23850-135">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="23850-136">Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="23850-136">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="23850-137">Un document Word contenant le texte spécifié s’affiche.</span><span class="sxs-lookup"><span data-stu-id="23850-137">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="23850-138">Pour convertir le texte en tableau</span><span class="sxs-lookup"><span data-stu-id="23850-138">To change the text to a table</span></span>
  
1. <span data-ttu-id="23850-139">Utilisez la méthode `ConvertToTable` pour inclure le texte dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="23850-139">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="23850-140">La méthode comprend seize paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="23850-140">The method has sixteen optional parameters.</span></span> <span data-ttu-id="23850-141">IntelliSense place les paramètres facultatifs entre crochets, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="23850-141">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![Liste de paramètres pour la méthode ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="23850-143">Les arguments nommés et facultatifs permettent de spécifier des valeurs uniquement pour les paramètres que vous voulez modifier.</span><span class="sxs-lookup"><span data-stu-id="23850-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="23850-144">Ajoutez le code suivant à la fin de la méthode `DisplayInWord` pour créer un tableau simple.</span><span class="sxs-lookup"><span data-stu-id="23850-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="23850-145">L’argument spécifie que les virgules présentes dans le texte de la chaîne comprise dans `range` séparent les cellules du tableau.</span><span class="sxs-lookup"><span data-stu-id="23850-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="23850-146">Dans les versions antérieures de C#, l’appel à `ConvertToTable` requiert un argument de référence pour chaque paramètre, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="23850-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="23850-147">Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="23850-147">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="23850-148">Pour tester d’autres paramètres</span><span class="sxs-lookup"><span data-stu-id="23850-148">To experiment with other parameters</span></span>

1. <span data-ttu-id="23850-149">Pour modifier la table afin qu’elle ait une colonne et trois lignes, remplacez la dernière ligne de `DisplayInWord` par l’instruction suivante, puis tapez <kbd>CTRL</kbd> + <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="23850-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="23850-150">Pour spécifier un format prédéfini pour la table, remplacez la dernière ligne de `DisplayInWord` par l’instruction suivante, puis tapez <kbd>CTRL</kbd> + <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="23850-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="23850-151">Le format peut être n’importe quelle constante [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>).</span><span class="sxs-lookup"><span data-stu-id="23850-151">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="23850-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="23850-152">Example</span></span>

<span data-ttu-id="23850-153">Le code suivant contient l’exemple complet :</span><span class="sxs-lookup"><span data-stu-id="23850-153">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="23850-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23850-154">See also</span></span>

- [<span data-ttu-id="23850-155">Arguments nommés et facultatifs</span><span class="sxs-lookup"><span data-stu-id="23850-155">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
