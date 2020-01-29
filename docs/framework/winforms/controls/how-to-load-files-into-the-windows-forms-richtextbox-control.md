---
title: Charger des fichiers dans le contrôle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: c31e004ea4cd0821b5f18f0ab0fe2708e6ac4b59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736284"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Comment : charger des fichiers dans le contrôle RichTextBox Windows Forms

Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms peut afficher du texte brut, du texte brut Unicode ou un fichier au format RTF( Rich-Text Format). Pour cela, appelez la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> . Vous pouvez également utiliser la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> pour charger des données à partir d’un flux de données. Pour plus d'informations, consultez <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-load-a-file-into-the-richtextbox-control"></a>Pour charger un fichier dans le contrôle RichTextBox

1. Déterminez le chemin du fichier à ouvrir à l’aide du composant <xref:System.Windows.Forms.OpenFileDialog> . Pour obtenir une vue d’ensemble, consultez [vue d’ensemble du composant OpenFileDialog](openfiledialog-component-overview-windows-forms.md).

2. Appelez la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> en spécifiant le fichier à charger et, éventuellement, un type de fichier. Dans l’exemple ci-dessous, le fichier à charger est spécifié par la propriété <xref:System.Windows.Forms.OpenFileDialog> du composant <xref:System.Windows.Forms.FileDialog.FileName%2A> . Si vous appelez la méthode en spécifiant un nom de fichier comme seul argument, le type de fichier est supposé être RTF. Pour spécifier un autre type de fichier, appelez la méthode en spécifiant une valeur pour l’énumération <xref:System.Windows.Forms.RichTextBoxStreamType> comme deuxième argument.

    Dans l’exemple ci-dessous, le composant <xref:System.Windows.Forms.OpenFileDialog> s’affiche quand l’utilisateur clique sur un bouton. Le fichier sélectionné est ensuite ouvert et affiché dans le contrôle <xref:System.Windows.Forms.RichTextBox> . Cet exemple suppose qu’un formulaire contient un bouton,`btnOpenFile`.

    ```vb
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _
       ByVal e As System.EventArgs) Handles btnOpenFile.Click
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _
              RichTextBoxStreamType.RichText)
          End If
    End Sub
    ```

    ```csharp
    private void btnOpenFile_Click(object sender, System.EventArgs e)
    {
       if(openFileDialog1.ShowDialog() == DialogResult.OK)
       {
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);
       }
    }
    ```

    ```cpp
    private:
       void btnOpenFile_Click(System::Object ^  sender,
          System::EventArgs ^  e)
       {
          if(openFileDialog1->ShowDialog() == DialogResult::OK)
          {
             richTextBox1->LoadFile(openFileDialog1->FileName,
                RichTextBoxStreamType::RichText);
          }
       }
    ```

    (Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > Pour exécuter ce processus, votre assembly peut nécessiter un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> . Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. Pour plus d'informations, consultez [Code Access Security Basics](../../misc/code-access-security-basics.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
