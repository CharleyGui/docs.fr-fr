---
title: 'Comment : rendre des images avec GDI+'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182501"
---
# <a name="how-to-render-images-with-gdi"></a>Comment : rendre des images avec GDI+
Vous pouvez utiliser GDIMD pour rendre les images qui existent sous forme de fichiers dans vos applications. Vous le faites en créant <xref:System.Drawing.Image> un nouvel <xref:System.Drawing.Bitmap>objet d’une classe (comme), en créant un <xref:System.Drawing.Graphics> objet <xref:System.Drawing.Graphics.DrawImage%2A> qui <xref:System.Drawing.Graphics> se réfère à la surface de dessin que vous voulez utiliser, et en appelant la méthode de l’objet. L’image est peinte sur la surface de dessin représentée par la classe graphics. Vous pouvez utiliser l’éditeur d’images pour créer et modifier des fichiers d’images au moment de la conception, et les rendre avec GDIMD au moment de l’exécution. Pour plus d’informations, consultez [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Pour afficher une image avec GDI+  
  
1. Créez un objet qui représente l’image à afficher. Cet objet doit être membre d’une <xref:System.Drawing.Image>classe <xref:System.Drawing.Bitmap> qui <xref:System.Drawing.Imaging.Metafile>hérite de , comme ou . Voici un exemple :  
  
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
  
2. Créez <xref:System.Drawing.Graphics> un objet qui représente la surface de dessin que vous souhaitez utiliser. Pour plus d’informations, consultez [Guide pratique pour créer des objets graphiques pour le dessin](how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3. Appelez <xref:System.Drawing.Graphics.DrawImage%2A> l’objet graphique de votre objet graphique pour rendre l’image. Vous devez spécifier l’image à dessiner et ses coordonnées.  
  
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
- [Comment : créer des objets graphiques pour le dessin](how-to-create-graphics-objects-for-drawing.md)
- [Stylets, lignes et rectangles dans GDI+](pens-lines-and-rectangles-in-gdi.md)
- [Comment : dessiner du texte dans un Windows Form](how-to-draw-text-on-a-windows-form.md)
- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Dessin de ligne ou de figures fermées](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)
