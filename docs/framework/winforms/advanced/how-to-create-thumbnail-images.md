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
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923761"
---
# <a name="how-to-create-thumbnail-images"></a>Procédure : créer des images miniatures
Une image miniature est une petite version d’une image. Vous pouvez créer une image miniature en appelant la <xref:System.Drawing.Image.GetThumbnailImage%2A> méthode d’un <xref:System.Drawing.Image> objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant construit un <xref:System.Drawing.Image> objet à partir d’un fichier jpg. L’image d’origine a une largeur de 640 pixels et une hauteur de 479 pixels. Le code crée une image miniature qui a une largeur de 100 pixels et une hauteur de 100 pixels.  
  
 L’illustration suivante montre l’image miniature:  
  
 ![Capture d’écran montrant la miniature de sortie.](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> Dans cet exemple, une méthode de rappel est déclarée, mais jamais utilisée. Cela prend en charge toutes les versions de GDI+.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour être utilisé avec Windows Forms, et il <xref:System.Windows.Forms.PaintEventArgs> nécessite `e`, qui <xref:System.Windows.Forms.Control.Paint> est un paramètre du gestionnaire d’événements. Pour exécuter l’exemple, procédez comme suit:  
  
1. Créez une application Windows Forms.  
  
2. Ajoutez l’exemple de code au formulaire.  
  
3. Créer un gestionnaire pour l’événement du <xref:System.Windows.Forms.Control.Paint> formulaire  
  
4. Dans le <xref:System.Windows.Forms.Control.Paint> gestionnaire, appelez la `GetThumbnail` méthode et transmettez <xref:System.Windows.Forms.PaintEventArgs> `e` .  
  
5. Recherchez un fichier image dont vous souhaitez créer une miniature.  
  
6. Dans la `GetThumbnail` méthode, spécifiez le chemin d’accès et le nom de fichier de votre image.  
  
7. Appuyez sur F5 pour exécuter l’exemple.  
  
     Une image miniature 100 par 100 apparaît sur le formulaire.  
  
## <a name="see-also"></a>Voir aussi

- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
- [Utilisation des images, bitmaps, icônes et métafichiers](working-with-images-bitmaps-icons-and-metafiles.md)
