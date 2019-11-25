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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Guide pratique pour ajouter un emplacement personnalisé à une boîte de dialogue Fichier
Les boîtes de dialogue Ouvrir et enregistrer par défaut sous Windows Vista ont une zone sur le côté gauche de la boîte de dialogue intitulée **liens favoris**. Cette zone est appelée Emplacements personnalisés. Les classes <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> vous permettent d’ajouter des dossiers à la collection de <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>.  
  
> [!NOTE]
> Pour qu’un emplacement personnalisé apparaisse dans le <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, la propriété <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> doit avoir la valeur `true` (valeur par défaut).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Pour ajouter un emplacement personnalisé à une boîte de dialogue Fichier  
  
- Ajoutez un chemin d’accès, un GUID de dossier connu ou un objet <xref:System.Windows.Forms.FileDialogCustomPlace> à la collection <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> de la boîte de dialogue.  
  
     L’exemple de code suivant montre comment ajouter un chemin :  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [GUID de dossier connus pour des emplacements personnalisés de boîtes de dialogue Fichier](known-folder-guids-for-file-dialog-custom-places.md)
