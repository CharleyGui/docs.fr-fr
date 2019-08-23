---
title: 'Procédure : ajouter un emplacement personnalisé à une boîte de dialogue fichier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916351"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="6e5f2-102">Procédure : ajouter un emplacement personnalisé à une boîte de dialogue fichier</span><span class="sxs-lookup"><span data-stu-id="6e5f2-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="6e5f2-103">Les boîtes de dialogue d’ouverture et d’enregistrement par défaut sur [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] ont une zone sur le côté gauche intitulée **Liens favoris**.</span><span class="sxs-lookup"><span data-stu-id="6e5f2-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="6e5f2-104">Cette zone est appelée Emplacements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="6e5f2-104">This area is called custom places.</span></span> <span data-ttu-id="6e5f2-105">Les <xref:System.Windows.Forms.OpenFileDialog> classes <xref:System.Windows.Forms.SaveFileDialog> et vous permettent d’ajouter des dossiers à <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> la collection.</span><span class="sxs-lookup"><span data-stu-id="6e5f2-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e5f2-106">Pour qu’un emplacement <xref:System.Windows.Forms.OpenFileDialog> personnalisé apparaisse dans le ou <xref:System.Windows.Forms.SaveFileDialog>, la <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriété doit avoir la valeur `true` (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="6e5f2-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="6e5f2-107">Pour ajouter un emplacement personnalisé à une boîte de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="6e5f2-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="6e5f2-108">Ajoutez un chemin d’accès, un GUID de dossier connu <xref:System.Windows.Forms.FileDialogCustomPlace> ou un objet <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> à la collection de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6e5f2-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="6e5f2-109">L’exemple de code suivant montre comment ajouter un chemin :</span><span class="sxs-lookup"><span data-stu-id="6e5f2-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6e5f2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e5f2-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6e5f2-111">GUID de dossier connus pour des emplacements personnalisés de boîtes de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="6e5f2-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
