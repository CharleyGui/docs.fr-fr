---
title: Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers-Guide de programmation C#
description: Découvrez comment fournir une boîte de dialogue de progression pour les opérations de fichier à l’aide de la méthode CopyFile (String, String, UIOption).
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 2ea18d924b47fc10412d37479f1b09f7eef7ad3b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301968"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="86366-103">Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="86366-103">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>
<span data-ttu-id="86366-104">Vous pouvez fournir une boîte de dialogue standard qui montre la progression des opérations sur les fichiers dans Windows si vous utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> de l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86366-104">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="86366-105">Pour ajouter une référence dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86366-105">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="86366-106">Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="86366-106">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="86366-107">La boîte de dialogue **Gestionnaire de références** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="86366-107">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="86366-108">Dans la zone **Assemblys**, choisissez **Framework** s’il n’est pas déjà sélectionné.</span><span class="sxs-lookup"><span data-stu-id="86366-108">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="86366-109">Dans la liste des noms, cochez la case **Microsoft.VisualBasic**, puis choisissez le bouton **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="86366-109">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86366-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="86366-110">Example</span></span>  
 <span data-ttu-id="86366-111">Le code suivant copie le répertoire spécifié par `sourcePath` dans le répertoire spécifié par `destinationPath`.</span><span class="sxs-lookup"><span data-stu-id="86366-111">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="86366-112">Ce code fournit également une boîte de dialogue standard qui affiche une estimation du temps restant avant la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="86366-112">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="86366-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86366-113">See also</span></span>

- [<span data-ttu-id="86366-114">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="86366-114">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
