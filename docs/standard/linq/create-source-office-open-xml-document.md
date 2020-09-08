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
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a>Créer le document Office Open XML source (LINQ to XML)

Cet article explique comment créer le document WordprocessingML Office Open XML utilisé par les autres exemples de ce didacticiel. Si vous suivez ces instructions, votre sortie correspondra à la sortie fournie dans chaque exemple.

Toutefois, les exemples présentés dans ce didacticiel fonctionnent avec n'importe quel document WordprocessingML valide.

Pour créer le document utilisé par ce didacticiel, Microsoft Office 2007 ou une version ultérieure, ou bien Microsoft Office 2003 avec le Module de compatibilité Microsoft Office pour les formats de fichiers Word, Excel et PowerPoint 2007 doit être installé sur votre ordinateur.

## <a name="create-the-wordprocessingml-document"></a>Créer le document WordprocessingML

Pour créer le document WordprocessingML, procédez comme suit :

1. Créez un nouveau document Microsoft Word.
1. Collez le texte suivant dans le nouveau document.
   1. Pour C#, utilisez le texte suivant :

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

   1. Pour Visual Basic, utilisez le texte suivant :

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

1. Mettez en forme la première ligne à l'aide du style « Titre 1 ».
1. Pour C#, sélectionnez les lignes qui contiennent le code C#. La première ligne commence par le mot clé `using`. La dernière ligne est la dernière accolade fermante. Mettez en forme les lignes avec la police Courrier. Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».
1. Pour Visual Basic, sélectionnez les lignes qui contiennent le code Visual Basic. La première ligne commence par le mot clé `Imports`. La dernière ligne est « End Class ». Mettez en forme les lignes avec la police Courrier. Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».
1. Pour finir, sélectionnez la ligne entière qui contient la sortie et mettez-la en forme avec le style `Code`.
1. Enregistrez le document et nommez-le SampleDoc.docx.

> [!NOTE]
> Si vous utilisez Microsoft Word 2003, sélectionnez **document word 2007** dans la liste déroulante **type de fichier** .

## <a name="see-also"></a>Voir aussi

- [Didacticiel : manipuler du contenu dans un document WordprocessingML](xml-shape-wordprocessingml-documents.md)
