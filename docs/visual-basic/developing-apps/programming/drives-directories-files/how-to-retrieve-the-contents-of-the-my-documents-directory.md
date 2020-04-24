---
title: 'Comment : récupérer le contenu du répertoire Mes Documents'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: cf4470020507c581999b9d72602ddb6e3e76ed74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334535"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="2977f-102">Guide pratique pour récupérer le contenu du répertoire Mes documents en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2977f-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="2977f-103">Vous pouvez utiliser l’objet <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> pour lire la plupart des répertoires de **Tous les utilisateurs**, tels que **Mes documents** ou **Bureau**.</span><span class="sxs-lookup"><span data-stu-id="2977f-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="2977f-104">Pour lire à partir du dossier Mes documents</span><span class="sxs-lookup"><span data-stu-id="2977f-104">To read from the My Documents folder</span></span>  
  
- <span data-ttu-id="2977f-105">Utilisez la méthode `ReadAllText` pour lire le texte de chaque fichier dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="2977f-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="2977f-106">Le code suivant spécifie un répertoire et un fichier, puis il utilise `ReadAllText` pour les lire dans la chaîne nommée `patients`.</span><span class="sxs-lookup"><span data-stu-id="2977f-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="2977f-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2977f-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
