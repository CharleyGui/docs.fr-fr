---
title: Choisir des dossiers avec le composant FolderBrowserDialog
description: Découvrez comment utiliser le composant Windows Forms FolderBrowserDialog dans les applications Windows que vous créez pour inviter les utilisateurs à sélectionner un dossier.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: 11d01bbaec3b82bc221960ebab5e33ca1aa302db
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903673"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Guide pratique pour sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms

Souvent, dans les applications Windows que vous créez, vous devez demander aux utilisateurs de sélectionner un dossier, le plus souvent pour enregistrer un ensemble de fichiers. Le <xref:System.Windows.Forms.FolderBrowserDialog> composant Windows Forms vous permet d’accomplir facilement cette tâche.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Pour sélectionner des dossiers avec le composant FolderBrowserDialog

1. Dans une procédure, vérifiez la <xref:System.Windows.Forms.FolderBrowserDialog> propriété du composant <xref:System.Windows.Forms.Form.DialogResult%2A> pour voir comment la boîte de dialogue a été fermée et obtenir la valeur de la <xref:System.Windows.Forms.FolderBrowserDialog> propriété du composant <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> .

2. Si vous devez définir le dossier de niveau supérieur qui s’affichera dans l’arborescence de la boîte de dialogue, définissez la <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriété, qui prend un membre de l' <xref:System.Environment.SpecialFolder> énumération.

3. En outre, vous pouvez définir la <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> propriété, qui spécifie la chaîne de texte qui apparaît en haut de la vue de l’arborescence des dossiers.

    Dans l’exemple ci-dessous, le <xref:System.Windows.Forms.FolderBrowserDialog> composant est utilisé pour sélectionner un dossier, de la même façon que lorsque vous créez un projet dans Visual Studio et êtes invité à sélectionner un dossier dans lequel l’enregistrer. Dans cet exemple, le nom du dossier est ensuite affiché dans un <xref:System.Windows.Forms.TextBox> contrôle du formulaire. Il est judicieux de placer l’emplacement dans une zone modifiable, telle qu’un <xref:System.Windows.Forms.TextBox> contrôle, afin que les utilisateurs puissent modifier leur sélection en cas d’erreur ou d’autres problèmes. Cet exemple suppose un formulaire avec un <xref:System.Windows.Forms.FolderBrowserDialog> composant et un <xref:System.Windows.Forms.TextBox> contrôle.

    ```vb
    Public Sub ChooseFolder()
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then
            TextBox1.Text = FolderBrowserDialog1.SelectedPath
        End If
    End Sub
    ```

    ```csharp
    public void ChooseFolder()
    {
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)
        {
            textBox1.Text = folderBrowserDialog1.SelectedPath;
        }
    }
    ```

    ```cpp
    public:
       void ChooseFolder()
       {
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)
          {
             textBox1->Text = folderBrowserDialog1->SelectedPath;
          }
       }
    ```

    > [!IMPORTANT]
    > Pour utiliser cette classe, votre assembly nécessite un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> propriété, qui fait partie de l' <xref:System.Security.Permissions.FileIOPermissionAccess> énumération. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../misc/code-access-security-basics.md).

Pour plus d’informations sur la façon d’enregistrer des fichiers, consultez [Guide pratique pour enregistrer des fichiers à l’aide du composant SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Vue d’ensemble du composant FolderBrowserDialog (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog, composant](folderbrowserdialog-component-windows-forms.md)
