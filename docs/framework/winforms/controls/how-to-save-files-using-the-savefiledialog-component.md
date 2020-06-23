---
title: Guide pratique pour enregistrer des fichiers à l'aide du composant SaveFileDialog
description: Découvrez comment utiliser le composant SaveFileDialog pour parcourir le système de fichiers et sélectionner les fichiers à enregistrer.
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
ms.openlocfilehash: cd773c3d4aa2b907eb09dd87c3fdbe138bf533bb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904401"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="46ff5-103">Guide pratique pour enregistrer des fichiers à l'aide du composant SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="46ff5-103">How to: Save Files Using the SaveFileDialog Component</span></span>

<span data-ttu-id="46ff5-104">Le <xref:System.Windows.Forms.SaveFileDialog> composant permet aux utilisateurs de parcourir le système de fichiers et de sélectionner les fichiers à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="46ff5-104">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="46ff5-105">La boîte de dialogue retourne le chemin et le nom du fichier que l’utilisateur a sélectionné dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="46ff5-105">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="46ff5-106">Cependant, vous devez écrire le code pour écrire réellement les fichiers sur le disque.</span><span class="sxs-lookup"><span data-stu-id="46ff5-106">However, you must write the code to actually write the files to disk.</span></span>

### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="46ff5-107">Pour enregistrer un fichier à l’aide du composant SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="46ff5-107">To save a file using the SaveFileDialog component</span></span>

- <span data-ttu-id="46ff5-108">Affichez la boîte de dialogue **Enregistrer le fichier** et appelez une méthode pour enregistrer le fichier sélectionné par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="46ff5-108">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>

  <span data-ttu-id="46ff5-109">Utilisez la <xref:System.Windows.Forms.SaveFileDialog> méthode du composant <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="46ff5-109">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="46ff5-110">Cette méthode vous donne un <xref:System.IO.Stream> objet dans lequel vous pouvez écrire.</span><span class="sxs-lookup"><span data-stu-id="46ff5-110">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>

  <span data-ttu-id="46ff5-111">L’exemple ci-dessous utilise la <xref:System.Windows.Forms.DialogResult> propriété pour récupérer le nom du fichier et la <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="46ff5-111">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="46ff5-112">La <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> méthode vous donne un flux dans lequel écrire le fichier.</span><span class="sxs-lookup"><span data-stu-id="46ff5-112">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>

  <span data-ttu-id="46ff5-113">Dans l’exemple ci-dessous, il existe un <xref:System.Windows.Forms.Button> contrôle avec une image qui lui est assignée.</span><span class="sxs-lookup"><span data-stu-id="46ff5-113">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="46ff5-114">Lorsque vous cliquez sur le bouton, un <xref:System.Windows.Forms.SaveFileDialog> composant est instancié avec un filtre qui autorise les fichiers de type. gif,. jpeg et. bmp.</span><span class="sxs-lookup"><span data-stu-id="46ff5-114">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="46ff5-115">Si un fichier de ce type est sélectionné dans la boîte de dialogue Enregistrer le fichier, l’image du bouton est enregistrée.</span><span class="sxs-lookup"><span data-stu-id="46ff5-115">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="46ff5-116">Pour obtenir ou définir la <xref:System.Windows.Forms.FileDialog.FileName%2A> propriété, votre assembly nécessite un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="46ff5-116">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="46ff5-117">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="46ff5-117">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="46ff5-118">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="46ff5-118">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

  <span data-ttu-id="46ff5-119">L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôle dont la <xref:System.Windows.Forms.ButtonBase.Image%2A> propriété a la valeur d’un fichier de type. gif,. jpeg ou. bmp.</span><span class="sxs-lookup"><span data-stu-id="46ff5-119">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>

  > [!NOTE]
  > <span data-ttu-id="46ff5-120">La <xref:System.Windows.Forms.FileDialog> propriété de la classe <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> (qui, en raison de l’héritage, fait partie de la <xref:System.Windows.Forms.SaveFileDialog> classe) utilise un index de base un.</span><span class="sxs-lookup"><span data-stu-id="46ff5-120">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="46ff5-121">Ceci est important si vous écrivez du code pour enregistrer les données dans un format spécifique (par exemple pour enregistrer un fichier au format texte brut ou au format binaire).</span><span class="sxs-lookup"><span data-stu-id="46ff5-121">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="46ff5-122">Cette propriété est présentée dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="46ff5-122">This property is featured in the example below.</span></span>

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

  <span data-ttu-id="46ff5-123">(Visual C# et Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="46ff5-123">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  <span data-ttu-id="46ff5-124">Pour plus d’informations sur l’écriture de flux de fichier, consultez <xref:System.IO.FileStream.BeginWrite%2A> et <xref:System.IO.FileStream.Write%2A> .</span><span class="sxs-lookup"><span data-stu-id="46ff5-124">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>

  > [!NOTE]
  > <span data-ttu-id="46ff5-125">Certains contrôles, tels que le <xref:System.Windows.Forms.RichTextBox> contrôle, peuvent enregistrer des fichiers.</span><span class="sxs-lookup"><span data-stu-id="46ff5-125">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span>

## <a name="see-also"></a><span data-ttu-id="46ff5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46ff5-126">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="46ff5-127">SaveFileDialog, composant</span><span class="sxs-lookup"><span data-stu-id="46ff5-127">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
