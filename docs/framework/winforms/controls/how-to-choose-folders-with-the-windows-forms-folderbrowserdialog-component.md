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
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="49dff-102">Guide pratique pour sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49dff-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>

<span data-ttu-id="49dff-103">Souvent, dans les applications Windows que vous créez, vous devez demander aux utilisateurs de sélectionner un dossier, le plus souvent pour enregistrer un ensemble de fichiers.</span><span class="sxs-lookup"><span data-stu-id="49dff-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="49dff-104">Le composant Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> vous permet d’accomplir facilement cette tâche.</span><span class="sxs-lookup"><span data-stu-id="49dff-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="49dff-105">Pour sélectionner des dossiers avec le composant FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="49dff-105">To choose folders with the FolderBrowserDialog component</span></span>

1. <span data-ttu-id="49dff-106">Dans une procédure, vérifiez la propriété <xref:System.Windows.Forms.Form.DialogResult%2A> du composant <xref:System.Windows.Forms.FolderBrowserDialog> pour voir comment la boîte de dialogue a été fermée et obtenir la valeur de la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> du composant <xref:System.Windows.Forms.FolderBrowserDialog>.</span><span class="sxs-lookup"><span data-stu-id="49dff-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>

2. <span data-ttu-id="49dff-107">Si vous devez définir le dossier de niveau supérieur qui s’affichera dans l’arborescence de la boîte de dialogue, définissez la propriété <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, qui prend un membre de l’énumération <xref:System.Environment.SpecialFolder>.</span><span class="sxs-lookup"><span data-stu-id="49dff-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>

3. <span data-ttu-id="49dff-108">En outre, vous pouvez définir la propriété <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>, qui spécifie la chaîne de texte qui apparaît en haut de la vue de l’arborescence des dossiers.</span><span class="sxs-lookup"><span data-stu-id="49dff-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>

    <span data-ttu-id="49dff-109">Dans l’exemple ci-dessous, le composant <xref:System.Windows.Forms.FolderBrowserDialog> est utilisé pour sélectionner un dossier, de la même façon que lorsque vous créez un projet dans Visual Studio et êtes invité à sélectionner un dossier dans lequel l’enregistrer.</span><span class="sxs-lookup"><span data-stu-id="49dff-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="49dff-110">Dans cet exemple, le nom du dossier est ensuite affiché dans un contrôle <xref:System.Windows.Forms.TextBox> du formulaire.</span><span class="sxs-lookup"><span data-stu-id="49dff-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="49dff-111">Il est judicieux de placer l’emplacement dans une zone modifiable, telle qu’un contrôle de <xref:System.Windows.Forms.TextBox>, afin que les utilisateurs puissent modifier leur sélection en cas d’erreur ou d’autres problèmes.</span><span class="sxs-lookup"><span data-stu-id="49dff-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="49dff-112">Cet exemple suppose un formulaire avec un composant <xref:System.Windows.Forms.FolderBrowserDialog> et un contrôle <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="49dff-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>

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
    > <span data-ttu-id="49dff-113">Pour utiliser cette classe, votre assembly nécessite un niveau de privilège accordé par la propriété <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>, qui fait partie de l’énumération <xref:System.Security.Permissions.FileIOPermissionAccess>.</span><span class="sxs-lookup"><span data-stu-id="49dff-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="49dff-114">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="49dff-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="49dff-115">Pour plus d'informations, consultez [Code Access Security Basics](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="49dff-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="49dff-116">Pour plus d’informations sur la façon d’enregistrer des fichiers, consultez [Guide pratique pour enregistrer des fichiers à l’aide du composant SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="49dff-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49dff-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49dff-117">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="49dff-118">Vue d’ensemble du composant FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="49dff-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="49dff-119">FolderBrowserDialog, composant</span><span class="sxs-lookup"><span data-stu-id="49dff-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
