---
title: Choisir des dossiers avec le composant FolderBrowserDialog
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
ms.openlocfilehash: 313388442101f341cfed366143f3c9669fb45cbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742228"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Guide pratique pour sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms

Souvent, dans les applications Windows que vous créez, vous devez demander aux utilisateurs de sélectionner un dossier, le plus souvent pour enregistrer un ensemble de fichiers. Le composant Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> vous permet d’accomplir facilement cette tâche.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Pour sélectionner des dossiers avec le composant FolderBrowserDialog

1. Dans une procédure, vérifiez la propriété <xref:System.Windows.Forms.Form.DialogResult%2A> du composant <xref:System.Windows.Forms.FolderBrowserDialog> pour voir comment la boîte de dialogue a été fermée et obtenir la valeur de la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> du composant <xref:System.Windows.Forms.FolderBrowserDialog>.

2. Si vous devez définir le dossier de niveau supérieur qui s’affichera dans l’arborescence de la boîte de dialogue, définissez la propriété <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, qui prend un membre de l’énumération <xref:System.Environment.SpecialFolder>.

3. En outre, vous pouvez définir la propriété <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>, qui spécifie la chaîne de texte qui apparaît en haut de la vue de l’arborescence des dossiers.

    Dans l’exemple ci-dessous, le composant <xref:System.Windows.Forms.FolderBrowserDialog> est utilisé pour sélectionner un dossier, de la même façon que lorsque vous créez un projet dans Visual Studio et êtes invité à sélectionner un dossier dans lequel l’enregistrer. Dans cet exemple, le nom du dossier est ensuite affiché dans un contrôle <xref:System.Windows.Forms.TextBox> du formulaire. Il est judicieux de placer l’emplacement dans une zone modifiable, telle qu’un contrôle de <xref:System.Windows.Forms.TextBox>, afin que les utilisateurs puissent modifier leur sélection en cas d’erreur ou d’autres problèmes. Cet exemple suppose un formulaire avec un composant <xref:System.Windows.Forms.FolderBrowserDialog> et un contrôle <xref:System.Windows.Forms.TextBox>.

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
    > Pour utiliser cette classe, votre assembly nécessite un niveau de privilège accordé par la propriété <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>, qui fait partie de l’énumération <xref:System.Security.Permissions.FileIOPermissionAccess>. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. Pour plus d'informations, consultez [Code Access Security Basics](../../misc/code-access-security-basics.md).

Pour plus d’informations sur la façon d’enregistrer des fichiers, consultez [Guide pratique pour enregistrer des fichiers à l’aide du composant SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Vue d’ensemble du composant FolderBrowserDialog (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog, composant](folderbrowserdialog-component-windows-forms.md)
