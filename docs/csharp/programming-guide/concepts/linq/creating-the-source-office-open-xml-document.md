---
title: Création du document Office Open XML source (C#)
description: Créez un document WordprocessingML Office Open XML à utiliser avec les didacticiels C#. Cet article requiert Microsoft Office.
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: e6d6908ee6560218793454f3871705e74095f543
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103994"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="eeadf-104">Création du document Office Open XML source (C#)</span><span class="sxs-lookup"><span data-stu-id="eeadf-104">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="eeadf-105">Cette rubrique montre comment créer le document WordprocessingML Office Open XML utilisé par les autres exemples de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="eeadf-105">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="eeadf-106">Si vous suivez ces instructions, votre sortie correspondra à la sortie fournie dans chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="eeadf-106">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="eeadf-107">Toutefois, les exemples présentés dans ce didacticiel fonctionnent avec n'importe quel document WordprocessingML valide.</span><span class="sxs-lookup"><span data-stu-id="eeadf-107">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="eeadf-108">Pour créer le document utilisé par ce didacticiel, Microsoft Office 2007 ou une version ultérieure, ou bien Microsoft Office 2003 avec le Module de compatibilité Microsoft Office pour les formats de fichiers Word, Excel et PowerPoint 2007 doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eeadf-108">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="eeadf-109">Création du document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="eeadf-109">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="eeadf-110">Pour créer le document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="eeadf-110">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="eeadf-111">Créez un nouveau document Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="eeadf-111">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="eeadf-112">Collez le texte suivant dans le nouveau document :</span><span class="sxs-lookup"><span data-stu-id="eeadf-112">Paste the following text into the new document:</span></span>

    ```text
    Parsing WordprocessingML with LINQ to XML

    The following example prints to the console.

    using System;

    class Program {
        public static void Main(string[] args) {
            Console.WriteLine("Hello World");
        }
    }

    This example produces the following output:

    Hello World
    ```

3. <span data-ttu-id="eeadf-113">Mettez en forme la première ligne à l'aide du style « Titre 1 ».</span><span class="sxs-lookup"><span data-stu-id="eeadf-113">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="eeadf-114">Sélectionnez les lignes qui contiennent le code C#.</span><span class="sxs-lookup"><span data-stu-id="eeadf-114">Select the lines that contain the C# code.</span></span> <span data-ttu-id="eeadf-115">La première ligne commence par le mot clé `using`.</span><span class="sxs-lookup"><span data-stu-id="eeadf-115">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="eeadf-116">La dernière ligne est la dernière accolade fermante.</span><span class="sxs-lookup"><span data-stu-id="eeadf-116">The last line is the last closing brace.</span></span> <span data-ttu-id="eeadf-117">Mettez en forme les lignes avec la police Courrier.</span><span class="sxs-lookup"><span data-stu-id="eeadf-117">Format the lines with the courier font.</span></span> <span data-ttu-id="eeadf-118">Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».</span><span class="sxs-lookup"><span data-stu-id="eeadf-118">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="eeadf-119">Pour finir, sélectionnez la ligne entière qui contient la sortie et mettez-la en forme avec le style `Code`.</span><span class="sxs-lookup"><span data-stu-id="eeadf-119">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="eeadf-120">Enregistrez le document et nommez-le SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="eeadf-120">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eeadf-121">Si vous utilisez Microsoft Word 2003, sélectionnez **Document Word 2007** dans la liste déroulante **Type de fichier**.</span><span class="sxs-lookup"><span data-stu-id="eeadf-121">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
