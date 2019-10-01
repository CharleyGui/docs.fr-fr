---
title: 'Procédure : lire des fichiers texte avec plusieurs formats en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: eae60b2fc72ee8b8653d3a0517eeaaf8012e0372
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696750"
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="b9561-102">Procédure : lire des fichiers texte avec plusieurs formats en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9561-102">How to: Read From Text Files with Multiple Formats in Visual Basic</span></span>
<span data-ttu-id="b9561-103">L’objet <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux.</span><span class="sxs-lookup"><span data-stu-id="b9561-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="b9561-104">Vous pouvez traiter un fichier contenant plusieurs formats en utilisant la méthode `PeekChars` pour déterminer le format de chaque ligne à mesure que vous analysez le fichier.</span><span class="sxs-lookup"><span data-stu-id="b9561-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="b9561-105">Pour analyser un fichier texte avec plusieurs formats</span><span class="sxs-lookup"><span data-stu-id="b9561-105">To parse a text file with multiple formats</span></span>  
  
1. <span data-ttu-id="b9561-106">Ajoutez un fichier texte nommé testfile.txt à votre projet.</span><span class="sxs-lookup"><span data-stu-id="b9561-106">Add a text file named testfile.txt to your project.</span></span> <span data-ttu-id="b9561-107">Ajoutez le contenu suivant au fichier texte.</span><span class="sxs-lookup"><span data-stu-id="b9561-107">Add the following content to the text file.</span></span>  
  
    ```text  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2. <span data-ttu-id="b9561-108">Définissez le format attendu et le format utilisé quand une erreur est signalée.</span><span class="sxs-lookup"><span data-stu-id="b9561-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="b9561-109">La dernière entrée dans chaque tableau étant -1, le dernier champ est supposé avoir une largeur variable.</span><span class="sxs-lookup"><span data-stu-id="b9561-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="b9561-110">Cela se produit quand la dernière entrée du tableau est inférieure ou égale à 0.</span><span class="sxs-lookup"><span data-stu-id="b9561-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>  
  
     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]  
  
3. <span data-ttu-id="b9561-111">Créez un nouvel objet <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> en définissant la largeur et le format.</span><span class="sxs-lookup"><span data-stu-id="b9561-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>  
  
     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]  
  
4. <span data-ttu-id="b9561-112">Parcourez les lignes en boucle, en testant le format avant la lecture.</span><span class="sxs-lookup"><span data-stu-id="b9561-112">Loop through the rows, testing for format before reading.</span></span>  
  
     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]  
  
5. <span data-ttu-id="b9561-113">Écrivez les erreurs dans la console.</span><span class="sxs-lookup"><span data-stu-id="b9561-113">Write errors to the console.</span></span>  
  
     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="b9561-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9561-114">Example</span></span>  
 <span data-ttu-id="b9561-115">Voici l’exemple complet qui lit le fichier `testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="b9561-115">Following is the complete example that reads from the file `testfile.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b9561-116">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="b9561-116">Robust Programming</span></span>  
 <span data-ttu-id="b9561-117">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="b9561-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b9561-118">Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="b9561-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="b9561-119">Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="b9561-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="b9561-120">Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b9561-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="b9561-121">Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier</span><span class="sxs-lookup"><span data-stu-id="b9561-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="b9561-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b9561-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="b9561-123">Le chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b9561-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="b9561-124">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="b9561-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9561-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9561-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="b9561-126">Guide pratique pour lire des fichiers texte délimités par des virgules</span><span class="sxs-lookup"><span data-stu-id="b9561-126">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="b9561-127">Guide pratique pour lire des fichiers texte de largeur fixe</span><span class="sxs-lookup"><span data-stu-id="b9561-127">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="b9561-128">Analyse des fichiers texte avec l’objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="b9561-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
