---
title: 'Procédure : afficher des images avec GDI+'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: da637152737510847830e885fdcd065ab92f16b3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505749"
---
# <a name="how-to-render-images-with-gdi"></a>Procédure : afficher des images avec GDI+
Vous pouvez utiliser GDI + pour afficher des images qui existent en tant que fichiers dans vos applications. Ce faire, vous devez créer un nouvel objet d’une <xref:System.Drawing.Image> classe (tels que <xref:System.Drawing.Bitmap>), en créant un <xref:System.Drawing.Graphics> de l’objet qui fait référence à la surface de dessin que vous souhaitez utiliser et en appelant le <xref:System.Drawing.Graphics.DrawImage%2A> méthode du <xref:System.Drawing.Graphics> objet. L’image est peinte sur la surface de dessin représentée par la classe graphics. Vous pouvez utiliser l’éditeur d’images pour créer et modifier des fichiers image au moment du design et les afficher avec GDI + au moment de l’exécution. Pour plus d’informations, consultez [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Pour afficher une image avec GDI+  
  
1. Créez un objet qui représente l’image à afficher. Cet objet doit être un membre d’une classe qui hérite de <xref:System.Drawing.Image>, tel que <xref:System.Drawing.Bitmap> ou <xref:System.Drawing.Imaging.Metafile>. Voici un exemple :  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the   
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2. Créer un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin que vous souhaitez utiliser. Pour plus d'informations, voir [Procédure : Créer des objets graphiques pour le dessin](how-to-create-graphics-objects-for-drawing.md).  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of   
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3. Appelez le <xref:System.Drawing.Graphics.DrawImage%2A> de l’objet graphics pour afficher l’image. Vous devez spécifier l’image à dessiner et ses coordonnées.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Mise en route de la programmation graphique](getting-started-with-graphics-programming.md)
- [Guide pratique pour Créer des objets graphiques pour le dessin](how-to-create-graphics-objects-for-drawing.md)
- [Stylets, lignes et rectangles dans GDI+](pens-lines-and-rectangles-in-gdi.md)
- [Guide pratique pour Dessiner du texte dans un formulaire Windows](how-to-draw-text-on-a-windows-form.md)
- [Graphiques et dessins dans Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Dessin de ligne ou de Figures fermées](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)
