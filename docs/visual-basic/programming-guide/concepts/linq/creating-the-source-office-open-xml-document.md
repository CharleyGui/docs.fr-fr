---
title: Création du document Office Open XML source
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 9f44c8d0f4080224c461736fdbdf3acd854e4a89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410836"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="ee421-102">Création du document Office Open XML source (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee421-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="ee421-103">Cette rubrique montre comment créer le document WordprocessingML Office Open XML utilisé par les autres exemples de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="ee421-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="ee421-104">Si vous suivez ces instructions, votre sortie correspondra à la sortie fournie dans chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="ee421-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="ee421-105">Toutefois, les exemples présentés dans ce didacticiel fonctionnent avec n'importe quel document WordprocessingML valide.</span><span class="sxs-lookup"><span data-stu-id="ee421-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="ee421-106">Pour créer le document utilisé par ce didacticiel, Microsoft Office 2007 ou une version ultérieure, ou bien Microsoft Office 2003 avec le Module de compatibilité Microsoft Office pour les formats de fichiers Word, Excel et PowerPoint 2007 doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ee421-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="ee421-107">Création du document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ee421-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="ee421-108">Pour créer le document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ee421-108">To create the WordprocessingML document</span></span>  
  
1. <span data-ttu-id="ee421-109">Créez un nouveau document Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="ee421-109">Create a new Microsoft Word document.</span></span>  
  
2. <span data-ttu-id="ee421-110">Collez le texte suivant dans le nouveau document :</span><span class="sxs-lookup"><span data-stu-id="ee421-110">Paste the following text into the new document:</span></span>  
  
    ```text  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. <span data-ttu-id="ee421-111">Mettez en forme la première ligne à l'aide du style « Titre 1 ».</span><span class="sxs-lookup"><span data-stu-id="ee421-111">Format the first line with the style "Heading 1".</span></span>  
  
4. <span data-ttu-id="ee421-112">Sélectionnez les lignes qui contiennent le code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ee421-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="ee421-113">La première ligne commence par le mot clé `Imports`.</span><span class="sxs-lookup"><span data-stu-id="ee421-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="ee421-114">La dernière ligne est « End Class ».</span><span class="sxs-lookup"><span data-stu-id="ee421-114">The last line is "End Class".</span></span> <span data-ttu-id="ee421-115">Mettez en forme les lignes avec la police Courrier.</span><span class="sxs-lookup"><span data-stu-id="ee421-115">Format the lines with the courier font.</span></span> <span data-ttu-id="ee421-116">Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».</span><span class="sxs-lookup"><span data-stu-id="ee421-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5. <span data-ttu-id="ee421-117">Pour finir, sélectionnez la ligne entière qui contient la sortie et mettez-la en forme avec le style `Code`.</span><span class="sxs-lookup"><span data-stu-id="ee421-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6. <span data-ttu-id="ee421-118">Enregistrez le document et nommez-le SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="ee421-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ee421-119">Si vous utilisez Microsoft Word 2003, sélectionnez **Document Word 2007** dans la liste déroulante **Type de fichier**.</span><span class="sxs-lookup"><span data-stu-id="ee421-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee421-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee421-120">See also</span></span>

- [<span data-ttu-id="ee421-121">Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee421-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
