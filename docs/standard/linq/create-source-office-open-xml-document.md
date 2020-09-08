---
title: Créer le document Office Open XML source-LINQ to XML
description: Découvrez comment créer le document WordprocessingML Office Open XML utilisé par les autres exemples de ce didacticiel.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: b3401d7309879661dcfc7062418ee75430dccf35
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552340"
---
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a><span data-ttu-id="a8817-103">Créer le document Office Open XML source (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a8817-103">Create the source Office Open XML document (LINQ to XML)</span></span>

<span data-ttu-id="a8817-104">Cet article explique comment créer le document WordprocessingML Office Open XML utilisé par les autres exemples de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="a8817-104">This article shows how to create the Office Open XML WordprocessingML document used by the other examples in this tutorial.</span></span> <span data-ttu-id="a8817-105">Si vous suivez ces instructions, votre sortie correspondra à la sortie fournie dans chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="a8817-105">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="a8817-106">Toutefois, les exemples présentés dans ce didacticiel fonctionnent avec n'importe quel document WordprocessingML valide.</span><span class="sxs-lookup"><span data-stu-id="a8817-106">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="a8817-107">Pour créer le document utilisé par ce didacticiel, Microsoft Office 2007 ou une version ultérieure, ou bien Microsoft Office 2003 avec le Module de compatibilité Microsoft Office pour les formats de fichiers Word, Excel et PowerPoint 2007 doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a8817-107">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="create-the-wordprocessingml-document"></a><span data-ttu-id="a8817-108">Créer le document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="a8817-108">Create the WordprocessingML document</span></span>

<span data-ttu-id="a8817-109">Pour créer le document WordprocessingML, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a8817-109">Use the following steps to create the WordprocessingML document:</span></span>

1. <span data-ttu-id="a8817-110">Créez un nouveau document Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="a8817-110">Create a new Microsoft Word document.</span></span>
1. <span data-ttu-id="a8817-111">Collez le texte suivant dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="a8817-111">Paste the following text into the new document.</span></span>
   1. <span data-ttu-id="a8817-112">Pour C#, utilisez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="a8817-112">For C#, use this text:</span></span>

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

   1. <span data-ttu-id="a8817-113">Pour Visual Basic, utilisez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="a8817-113">For Visual Basic, use this text:</span></span>

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

1. <span data-ttu-id="a8817-114">Mettez en forme la première ligne à l'aide du style « Titre 1 ».</span><span class="sxs-lookup"><span data-stu-id="a8817-114">Format the first line with the style "Heading 1".</span></span>
1. <span data-ttu-id="a8817-115">Pour C#, sélectionnez les lignes qui contiennent le code C#.</span><span class="sxs-lookup"><span data-stu-id="a8817-115">For C#, select the lines that contain the C# code.</span></span> <span data-ttu-id="a8817-116">La première ligne commence par le mot clé `using`.</span><span class="sxs-lookup"><span data-stu-id="a8817-116">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="a8817-117">La dernière ligne est la dernière accolade fermante.</span><span class="sxs-lookup"><span data-stu-id="a8817-117">The last line is the last closing brace.</span></span> <span data-ttu-id="a8817-118">Mettez en forme les lignes avec la police Courrier.</span><span class="sxs-lookup"><span data-stu-id="a8817-118">Format the lines with the courier font.</span></span> <span data-ttu-id="a8817-119">Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».</span><span class="sxs-lookup"><span data-stu-id="a8817-119">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="a8817-120">Pour Visual Basic, sélectionnez les lignes qui contiennent le code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a8817-120">For Visual Basic, select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="a8817-121">La première ligne commence par le mot clé `Imports`.</span><span class="sxs-lookup"><span data-stu-id="a8817-121">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="a8817-122">La dernière ligne est « End Class ».</span><span class="sxs-lookup"><span data-stu-id="a8817-122">The last line is "End Class".</span></span> <span data-ttu-id="a8817-123">Mettez en forme les lignes avec la police Courrier.</span><span class="sxs-lookup"><span data-stu-id="a8817-123">Format the lines with the courier font.</span></span> <span data-ttu-id="a8817-124">Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».</span><span class="sxs-lookup"><span data-stu-id="a8817-124">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="a8817-125">Pour finir, sélectionnez la ligne entière qui contient la sortie et mettez-la en forme avec le style `Code`.</span><span class="sxs-lookup"><span data-stu-id="a8817-125">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>
1. <span data-ttu-id="a8817-126">Enregistrez le document et nommez-le SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="a8817-126">Save the document, and name it SampleDoc.docx.</span></span>

> [!NOTE]
> <span data-ttu-id="a8817-127">Si vous utilisez Microsoft Word 2003, sélectionnez **document word 2007** dans la liste déroulante **type de fichier** .</span><span class="sxs-lookup"><span data-stu-id="a8817-127">If you're using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8817-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8817-128">See also</span></span>

- [<span data-ttu-id="a8817-129">Didacticiel : manipuler du contenu dans un document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="a8817-129">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
