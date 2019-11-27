---
title: 'Comment : lire des fichiers texte délimités par des virgules'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 9b93893e2221b156b65ce8e945089269ea28c989
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335074"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="ab327-102">Guide pratique pour lire des fichiers texte délimités par des virgules en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab327-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="ab327-103">L’objet `TextFieldParser` permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux.</span><span class="sxs-lookup"><span data-stu-id="ab327-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="ab327-104">La propriété `TextFieldType` définit s’il s’agit d’un fichier délimité ou d’un fichier avec des champs de texte de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="ab327-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="ab327-105">Pour analyser un fichier texte délimité par des virgules</span><span class="sxs-lookup"><span data-stu-id="ab327-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="ab327-106">Créez un `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="ab327-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="ab327-107">Le code suivant crée le `TextFieldParser` nommé `MyReader` et ouvre le fichier `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="ab327-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="ab327-108">Définissez le type `TextField` et le séparateur.</span><span class="sxs-lookup"><span data-stu-id="ab327-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="ab327-109">Le code suivant définit la propriété `TextFieldType` comme `Delimited` et le délimiteur comme ",".</span><span class="sxs-lookup"><span data-stu-id="ab327-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="ab327-110">Parcourez les champs du fichier à l’aide d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="ab327-110">Loop through the fields in the file.</span></span> <span data-ttu-id="ab327-111">Si des lignes sont endommagées, signalez une erreur et poursuivez l’analyse.</span><span class="sxs-lookup"><span data-stu-id="ab327-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="ab327-112">Le code suivant parcourt le fichier à l’aide d’une boucle, affiche chaque champ l’un après l’autre et signale les champs dont le format n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="ab327-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="ab327-113">Fermez les blocs `While` et `Using` avec `End While` et `End Using`.</span><span class="sxs-lookup"><span data-stu-id="ab327-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="ab327-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab327-114">Example</span></span>  

 <span data-ttu-id="ab327-115">Cet exemple lit le fichier `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="ab327-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ab327-116">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ab327-116">Robust programming</span></span>  

 <span data-ttu-id="ab327-117">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="ab327-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ab327-118">Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="ab327-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="ab327-119">Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="ab327-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="ab327-120">Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="ab327-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="ab327-121">Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier</span><span class="sxs-lookup"><span data-stu-id="ab327-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="ab327-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ab327-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="ab327-123">Le chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ab327-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="ab327-124">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="ab327-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab327-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab327-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="ab327-126">Guide pratique : lire des fichiers texte de largeur fixe</span><span class="sxs-lookup"><span data-stu-id="ab327-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="ab327-127">Guide pratique : lire des fichiers texte avec plusieurs formats</span><span class="sxs-lookup"><span data-stu-id="ab327-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="ab327-128">Analyse des fichiers texte avec l’objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="ab327-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="ab327-129">Procédure pas à pas : manipulation de fichiers et de répertoires dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab327-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="ab327-130">Dépannage : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="ab327-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
