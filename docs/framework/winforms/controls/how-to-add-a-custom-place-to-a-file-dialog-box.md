---
title: Guide pratique pour ajouter un emplacement personnalisé à une boîte de dialogue Fichier
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 7172e484451cf932413920910ec9124b3388bd76
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976993"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="d5ecb-102">Guide pratique pour ajouter un emplacement personnalisé à une boîte de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="d5ecb-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="d5ecb-103">Les boîtes de dialogue Ouvrir et enregistrer par défaut sous Windows Vista ont une zone sur le côté gauche de la boîte de dialogue intitulée **liens favoris**.</span><span class="sxs-lookup"><span data-stu-id="d5ecb-103">The default open and save dialog boxes on Windows Vista have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="d5ecb-104">Cette zone est appelée Emplacements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d5ecb-104">This area is called custom places.</span></span> <span data-ttu-id="d5ecb-105">Les classes <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> vous permettent d’ajouter des dossiers à la collection de <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5ecb-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5ecb-106">Pour qu’un emplacement personnalisé apparaisse dans le <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, la propriété <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> doit avoir la valeur `true` (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="d5ecb-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="d5ecb-107">Pour ajouter un emplacement personnalisé à une boîte de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="d5ecb-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="d5ecb-108">Ajoutez un chemin d’accès, un GUID de dossier connu ou un objet <xref:System.Windows.Forms.FileDialogCustomPlace> à la collection <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d5ecb-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="d5ecb-109">L’exemple de code suivant montre comment ajouter un chemin :</span><span class="sxs-lookup"><span data-stu-id="d5ecb-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d5ecb-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5ecb-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d5ecb-111">GUID de dossier connus pour des emplacements personnalisés de boîtes de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="d5ecb-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
