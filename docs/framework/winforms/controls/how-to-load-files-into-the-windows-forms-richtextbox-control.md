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
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="21a3b-102">Comment : charger des fichiers dans le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21a3b-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="21a3b-103">Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms peut afficher du texte brut, du texte brut Unicode ou un fichier au format RTF( Rich-Text Format).</span><span class="sxs-lookup"><span data-stu-id="21a3b-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="21a3b-104">Pour cela, appelez la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="21a3b-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="21a3b-105">Vous pouvez également utiliser la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> pour charger des données à partir d’un flux de données.</span><span class="sxs-lookup"><span data-stu-id="21a3b-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="21a3b-106">Pour plus d'informations, consultez <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="21a3b-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="21a3b-107">Pour charger un fichier dans le contrôle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="21a3b-107">To load a file into the RichTextBox control</span></span>

1. <span data-ttu-id="21a3b-108">Déterminez le chemin du fichier à ouvrir à l’aide du composant <xref:System.Windows.Forms.OpenFileDialog> .</span><span class="sxs-lookup"><span data-stu-id="21a3b-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="21a3b-109">Pour obtenir une vue d’ensemble, consultez [vue d’ensemble du composant OpenFileDialog](openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="21a3b-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="21a3b-110">Appelez la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> en spécifiant le fichier à charger et, éventuellement, un type de fichier.</span><span class="sxs-lookup"><span data-stu-id="21a3b-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="21a3b-111">Dans l’exemple ci-dessous, le fichier à charger est spécifié par la propriété <xref:System.Windows.Forms.OpenFileDialog> du composant <xref:System.Windows.Forms.FileDialog.FileName%2A> .</span><span class="sxs-lookup"><span data-stu-id="21a3b-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="21a3b-112">Si vous appelez la méthode en spécifiant un nom de fichier comme seul argument, le type de fichier est supposé être RTF.</span><span class="sxs-lookup"><span data-stu-id="21a3b-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="21a3b-113">Pour spécifier un autre type de fichier, appelez la méthode en spécifiant une valeur pour l’énumération <xref:System.Windows.Forms.RichTextBoxStreamType> comme deuxième argument.</span><span class="sxs-lookup"><span data-stu-id="21a3b-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="21a3b-114">Dans l’exemple ci-dessous, le composant <xref:System.Windows.Forms.OpenFileDialog> s’affiche quand l’utilisateur clique sur un bouton.</span><span class="sxs-lookup"><span data-stu-id="21a3b-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="21a3b-115">Le fichier sélectionné est ensuite ouvert et affiché dans le contrôle <xref:System.Windows.Forms.RichTextBox> .</span><span class="sxs-lookup"><span data-stu-id="21a3b-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="21a3b-116">Cet exemple suppose qu’un formulaire contient un bouton,`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="21a3b-116">This example assumes a form has a button,`btnOpenFile`.</span></span>

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

    <span data-ttu-id="21a3b-117">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="21a3b-117">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="21a3b-118">Pour exécuter ce processus, votre assembly peut nécessiter un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="21a3b-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="21a3b-119">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="21a3b-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="21a3b-120">Pour plus d'informations, consultez [Code Access Security Basics](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="21a3b-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21a3b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21a3b-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="21a3b-122">RichTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="21a3b-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="21a3b-123">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21a3b-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
