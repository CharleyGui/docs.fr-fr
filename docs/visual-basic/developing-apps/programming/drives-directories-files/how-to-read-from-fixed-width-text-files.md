---
title: 'Comment: lire à partir de fichiers texte à largeur fixe'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334624"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="9bff8-102">Guide pratique pour lire des fichiers texte de largeur fixe en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bff8-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="9bff8-103">L’objet `TextFieldParser` permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux.</span><span class="sxs-lookup"><span data-stu-id="9bff8-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="9bff8-104">La propriété `TextFieldType` définit si le fichier analysé est un fichier délimité ou un fichier qui comporte des champs de texte de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="9bff8-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="9bff8-105">Dans un fichier texte de largeur fixe, le champ situé à la fin peut avoir une largeur variable.</span><span class="sxs-lookup"><span data-stu-id="9bff8-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="9bff8-106">Pour spécifier que le champ situé à la fin a une largeur variable, définissez-le pour que sa largeur soit inférieure ou égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="9bff8-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="9bff8-107">Pour analyser un fichier texte de largeur fixe</span><span class="sxs-lookup"><span data-stu-id="9bff8-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="9bff8-108">Créez un `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="9bff8-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="9bff8-109">Le code suivant crée le `TextFieldParser` nommé `Reader` et ouvre le fichier `test.log`.</span><span class="sxs-lookup"><span data-stu-id="9bff8-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="9bff8-110">Définissez la propriété `TextFieldType` en tant que `FixedWidth`, en définissant la largeur et le format.</span><span class="sxs-lookup"><span data-stu-id="9bff8-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="9bff8-111">Le code suivant définit les colonnes de texte. La première a une largeur de 5 caractères, la deuxième de 10 caractères, la troisième de 11 caractères et la quatrième a une largeur variable.</span><span class="sxs-lookup"><span data-stu-id="9bff8-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="9bff8-112">Parcourez les champs du fichier à l’aide d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="9bff8-112">Loop through the fields in the file.</span></span> <span data-ttu-id="9bff8-113">Si des lignes sont endommagées, signalez une erreur et poursuivez l’analyse.</span><span class="sxs-lookup"><span data-stu-id="9bff8-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="9bff8-114">Fermez les blocs `While` et `Using` avec `End While` et `End Using`.</span><span class="sxs-lookup"><span data-stu-id="9bff8-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="9bff8-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9bff8-115">Example</span></span>  

 <span data-ttu-id="9bff8-116">Cet exemple lit le fichier `test.log`.</span><span class="sxs-lookup"><span data-stu-id="9bff8-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9bff8-117">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="9bff8-117">Robust programming</span></span>  

 <span data-ttu-id="9bff8-118">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="9bff8-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9bff8-119">Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="9bff8-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="9bff8-120">Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="9bff8-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="9bff8-121">Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="9bff8-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="9bff8-122">Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier</span><span class="sxs-lookup"><span data-stu-id="9bff8-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="9bff8-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9bff8-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="9bff8-124">Le chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="9bff8-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="9bff8-125">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="9bff8-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bff8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bff8-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="9bff8-127">Comment : lire des fichiers texte délimités par des virgules</span><span class="sxs-lookup"><span data-stu-id="9bff8-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="9bff8-128">Comment : lire des fichiers texte avec plusieurs formats</span><span class="sxs-lookup"><span data-stu-id="9bff8-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="9bff8-129">Analyse des fichiers texte avec l'objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="9bff8-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="9bff8-130">Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bff8-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="9bff8-131">Dépannage : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="9bff8-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
