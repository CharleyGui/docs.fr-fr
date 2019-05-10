---
title: 'Procédure : créer des images miniatures'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 275041372bd5e7da5dd0b32dc0a3d70a38bd0dcd
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063765"
---
# <a name="how-to-create-thumbnail-images"></a>Procédure : créer des images miniatures
Une image miniature est une version réduite d’une image. Vous pouvez créer une image miniature en appelant le <xref:System.Drawing.Image.GetThumbnailImage%2A> méthode d’un <xref:System.Drawing.Image> objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant construit un <xref:System.Drawing.Image> objet à partir d’un fichier JPG. L’image d’origine a une largeur de 640 pixels et une hauteur de 479 pixels. Le code crée une image miniature qui a une largeur de 100 pixels et une hauteur de 100 pixels.  
  
 L’illustration suivante montre l’image miniature :  
  
 ![Capture d’écran montrant la miniature de sortie.](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
>  Dans cet exemple, une méthode de rappel est déclarée mais jamais utilisée. Cela prend en charge toutes les versions de GDI +.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements. Pour exécuter l’exemple, procédez comme suit :  
  
1. Créez une application Windows Forms.  
  
2. Ajoutez l’exemple de code au formulaire.  
  
3. Créez un gestionnaire pour le formulaire <xref:System.Windows.Forms.Control.Paint> événement  
  
4. Dans le <xref:System.Windows.Forms.Control.Paint> gestionnaire, appelez le `GetThumbnail` (méthode) et passez `e` pour <xref:System.Windows.Forms.PaintEventArgs>.  
  
5. Rechercher un fichier image que vous souhaitez faire une miniature.  
  
6. Dans le `GetThumbnail` (méthode), spécifiez le chemin d’accès et le nom à votre image de fichier.  
  
7. Appuyez sur F5 pour exécuter l’exemple.  
  
     Une image miniature de 100 par 100 s’affiche sur le formulaire.  
  
## <a name="see-also"></a>Voir aussi

- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
- [Utilisation des images, bitmaps, icônes et métafichiers](working-with-images-bitmaps-icons-and-metafiles.md)
