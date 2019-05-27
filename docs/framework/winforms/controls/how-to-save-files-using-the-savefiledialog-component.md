---
title: 'Procédure : enregistrer des fichiers à l’aide du composant SaveFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: 18d9b93b78d3ed588eafa48831448983ccd61fe8
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053507"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Procédure : enregistrer des fichiers à l’aide du composant SaveFileDialog
Le <xref:System.Windows.Forms.SaveFileDialog> composant permet aux utilisateurs de parcourir le système de fichiers et de sélectionner les fichiers à enregistrer. La boîte de dialogue retourne le chemin et le nom du fichier que l’utilisateur a sélectionné dans la boîte de dialogue. Cependant, vous devez écrire le code pour écrire réellement les fichiers sur le disque.  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a>Pour enregistrer un fichier à l’aide du composant SaveFileDialog  
  
- Affichez la boîte de dialogue **Enregistrer le fichier** et appelez une méthode pour enregistrer le fichier sélectionné par l’utilisateur.  
  
     Utilisez le <xref:System.Windows.Forms.SaveFileDialog> du composant <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> méthode pour enregistrer le fichier. Cette méthode vous donne un <xref:System.IO.Stream> objet vous pouvez écrire.  
  
     L’exemple ci-dessous utilise la <xref:System.Windows.Forms.DialogResult> propriété pour obtenir le nom du fichier et le <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode pour enregistrer le fichier. Le <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> méthode vous donne un flux à écrire le fichier.  
  
     Dans l’exemple ci-dessous, il existe un <xref:System.Windows.Forms.Button> contrôle avec une image qui lui est assignée. Lorsque vous cliquez sur le bouton, un <xref:System.Windows.Forms.SaveFileDialog> est instancié avec un filtre qui autorise les fichiers de type .gif, .jpeg et .bmp. Si un fichier de ce type est sélectionné dans la boîte de dialogue Enregistrer le fichier, l’image du bouton est enregistrée.  
  
    > [!IMPORTANT]
    >  Pour obtenir ou définir le <xref:System.Windows.Forms.FileDialog.FileName%2A> propriété, votre assembly nécessite un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../misc/code-access-security-basics.md).  
  
     L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôler avec son <xref:System.Windows.Forms.ButtonBase.Image%2A> propriété définie dans un fichier de type .gif, .jpeg ou .bmp.  
  
    > [!NOTE]
    >  Le <xref:System.Windows.Forms.FileDialog> la classe <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> propriété (qui, en raison de l’héritage, fait partie de la <xref:System.Windows.Forms.SaveFileDialog> classe) utilise un index de base un. Ceci est important si vous écrivez du code pour enregistrer les données dans un format spécifique (par exemple pour enregistrer un fichier au format texte brut ou au format binaire). Cette propriété est présentée dans l’exemple ci-dessous.  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast\<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     (Visual C# et Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     Pour plus d’informations sur l’écriture de flux de fichiers, consultez <xref:System.IO.FileStream.BeginWrite%2A> et <xref:System.IO.FileStream.Write%2A>.  
  
    > [!NOTE]
    >  Certains contrôles, tels que le <xref:System.Windows.Forms.RichTextBox> , ont la possibilité d’enregistrer des fichiers. Pour plus d’informations, consultez la section « Composant SaveFileDialog » de l’article technique de MSDN Online Library, [Les principaux codes des boîtes de dialogue de Windows Forms](https://go.microsoft.com/fwlink/?LinkID=102575).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog, composant](savefiledialog-component-windows-forms.md)
