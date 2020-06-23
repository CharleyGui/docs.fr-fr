---
title: 'Comment : ouvrir des fichiers avec le composant OpenFileDialog'
ms.date: 02/11/2019
description: Découvrez comment utiliser le composant OpenFileDialog pour ouvrir la boîte de dialogue Windows permettant de parcourir et de sélectionner des fichiers.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904427"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="52ce0-103">Comment : ouvrir des fichiers avec OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="52ce0-103">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="52ce0-104">Le <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> composant ouvre la boîte de dialogue Windows permettant de parcourir et de sélectionner des fichiers.</span><span class="sxs-lookup"><span data-stu-id="52ce0-104">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="52ce0-105">Pour ouvrir et lire les fichiers sélectionnés, vous pouvez utiliser la <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> méthode ou créer une instance de la <xref:System.IO.StreamReader?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="52ce0-105">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="52ce0-106">Les exemples suivants illustrent ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="52ce0-106">The following examples show both approaches.</span></span>

<span data-ttu-id="52ce0-107">Dans .NET Framework, pour obtenir ou définir la propriété, vous devez disposer d' <xref:System.Windows.Forms.FileDialog.FileName%2A> un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="52ce0-107">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="52ce0-108">Les exemples exécutent une <xref:System.Security.Permissions.FileIOPermission> vérification d’autorisation et peuvent lever une exception en raison de privilèges insuffisants si elle est exécutée dans un contexte de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="52ce0-108">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="52ce0-109">Pour plus d’informations, consultez principes de base de la [sécurité d’accès du code](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="52ce0-109">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="52ce0-110">Vous pouvez générer et exécuter ces exemples comme des applications .NET Framework à partir de la ligne de commande C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="52ce0-110">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="52ce0-111">Pour plus d’informations, consultez génération à partir de la [ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="52ce0-111">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="52ce0-112">À compter de .NET Core 3,0, vous pouvez également générer et exécuter les exemples en tant qu’applications Windows .NET Core à partir d’un dossier qui contient un fichier projet .NET Core Windows Forms \* \<folder name> . csproj\* .</span><span class="sxs-lookup"><span data-stu-id="52ce0-112">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="52ce0-113">Exemple : lire un fichier en tant que flux avec StreamReader</span><span class="sxs-lookup"><span data-stu-id="52ce0-113">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="52ce0-114">L’exemple suivant utilise le <xref:System.Windows.Forms.Button> Gestionnaire d’événements du contrôle Windows Forms <xref:System.Windows.Forms.Control.Click> pour ouvrir <xref:System.Windows.Forms.OpenFileDialog> avec la <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="52ce0-114">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="52ce0-115">Une fois que l’utilisateur a choisi un fichier et qu’il a sélectionné **OK**, une instance de la <xref:System.IO.StreamReader> classe lit le fichier et affiche son contenu dans la zone de texte du formulaire.</span><span class="sxs-lookup"><span data-stu-id="52ce0-115">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="52ce0-116">Pour plus d’informations sur la lecture à partir des flux de fichiers, consultez <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> et <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="52ce0-116">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="52ce0-117">Exemple : ouvrir un fichier à partir d’une sélection filtrée avec OpenFile</span><span class="sxs-lookup"><span data-stu-id="52ce0-117">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="52ce0-118">L’exemple suivant utilise le <xref:System.Windows.Forms.Button> Gestionnaire d' <xref:System.Windows.Forms.Control.Click> événements du contrôle pour ouvrir le <xref:System.Windows.Forms.OpenFileDialog> avec un filtre qui affiche uniquement les fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="52ce0-118">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="52ce0-119">Une fois que l’utilisateur a choisi un fichier texte et sélectionne **OK**, la <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode est utilisée pour ouvrir le fichier dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="52ce0-119">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="52ce0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52ce0-120">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="52ce0-121">OpenFileDialog, composant</span><span class="sxs-lookup"><span data-stu-id="52ce0-121">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
