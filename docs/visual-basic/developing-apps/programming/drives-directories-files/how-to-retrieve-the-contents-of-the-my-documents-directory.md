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
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Guide pratique pour récupérer le contenu du répertoire Mes documents en Visual Basic

Vous pouvez utiliser l’objet <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> pour lire la plupart des répertoires de **Tous les utilisateurs**, tels que **Mes documents** ou **Bureau**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Pour lire à partir du dossier Mes documents  
  
- Utilisez la méthode `ReadAllText` pour lire le texte de chaque fichier dans un répertoire spécifique. Le code suivant spécifie un répertoire et un fichier, puis il utilise `ReadAllText` pour les lire dans la chaîne nommée `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
