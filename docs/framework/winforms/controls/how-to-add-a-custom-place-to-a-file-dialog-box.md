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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Procédure : ajouter un emplacement personnalisé à une boîte de dialogue fichier
Les boîtes de dialogue d’ouverture et d’enregistrement par défaut sur [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] ont une zone sur le côté gauche intitulée **Liens favoris**. Cette zone est appelée Emplacements personnalisés. Les <xref:System.Windows.Forms.OpenFileDialog> classes <xref:System.Windows.Forms.SaveFileDialog> et vous permettent d’ajouter des dossiers à <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> la collection.  
  
> [!NOTE]
> Pour qu’un emplacement <xref:System.Windows.Forms.OpenFileDialog> personnalisé apparaisse dans le ou <xref:System.Windows.Forms.SaveFileDialog>, la <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriété doit avoir la valeur `true` (valeur par défaut).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Pour ajouter un emplacement personnalisé à une boîte de dialogue Fichier  
  
- Ajoutez un chemin d’accès, un GUID de dossier connu <xref:System.Windows.Forms.FileDialogCustomPlace> ou un objet <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> à la collection de la boîte de dialogue.  
  
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
