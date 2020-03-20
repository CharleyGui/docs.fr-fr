---
title: 'Comment : Ouvrez les fichiers avec le composant OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182129"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="fec2b-102">Comment: Ouvrir les fichiers avec l’OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="fec2b-102">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="fec2b-103">Le <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> composant ouvre la boîte de dialogue Windows pour la navigation et la sélection des fichiers.</span><span class="sxs-lookup"><span data-stu-id="fec2b-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="fec2b-104">Pour ouvrir et lire les fichiers <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> sélectionnés, vous pouvez <xref:System.IO.StreamReader?displayProperty=nameWithType> utiliser la méthode, ou créer un exemple de la classe.</span><span class="sxs-lookup"><span data-stu-id="fec2b-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fec2b-105">Les exemples suivants montrent les deux approches.</span><span class="sxs-lookup"><span data-stu-id="fec2b-105">The following examples show both approaches.</span></span>

<span data-ttu-id="fec2b-106">Dans le cadre .NET, <xref:System.Windows.Forms.FileDialog.FileName%2A> pour obtenir ou définir <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> la propriété nécessite un niveau de privilège accordé par la classe.</span><span class="sxs-lookup"><span data-stu-id="fec2b-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fec2b-107">Les exemples <xref:System.Security.Permissions.FileIOPermission> exécutent une vérification d’autorisation, et peuvent jeter une exception en raison de privilèges insuffisants s’ils sont exécutés dans un contexte de fiducie partielle.</span><span class="sxs-lookup"><span data-stu-id="fec2b-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="fec2b-108">Pour plus d’informations, voir [Les bases de sécurité d’accès au Code](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="fec2b-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="fec2b-109">Vous pouvez créer et exécuter ces exemples sous forme d’applications cadres .NET de la ligne de commande C ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fec2b-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="fec2b-110">Pour plus d’informations, voir [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="fec2b-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="fec2b-111">En commençant par .NET Core 3.0, vous pouvez également construire et exécuter les exemples comme Windows .NET Core applications à partir d’un dossier qui a un nom de dossier .NET Core Windows Forms \* \<>.csproj\* fichier de projet.</span><span class="sxs-lookup"><span data-stu-id="fec2b-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="fec2b-112">Exemple : Lisez un fichier en streaming avec StreamReader</span><span class="sxs-lookup"><span data-stu-id="fec2b-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="fec2b-113">L’exemple suivant utilise <xref:System.Windows.Forms.Button> le <xref:System.Windows.Forms.Control.Click> gestionnaire d’événements <xref:System.Windows.Forms.OpenFileDialog> du <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> contrôle des formulaires Windows pour l’ouvrir avec la méthode.</span><span class="sxs-lookup"><span data-stu-id="fec2b-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="fec2b-114">Une fois que l’utilisateur **OK**choisit un fichier <xref:System.IO.StreamReader> et sélectionne OK , une instance de la classe lit le fichier et affiche son contenu dans la boîte de texte du formulaire.</span><span class="sxs-lookup"><span data-stu-id="fec2b-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="fec2b-115">Pour plus d’informations sur la <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>lecture des flux de fichiers, voir et .</span><span class="sxs-lookup"><span data-stu-id="fec2b-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="fec2b-116">Exemple : Ouvrez un fichier à partir d’une sélection filtrée avec OpenFile</span><span class="sxs-lookup"><span data-stu-id="fec2b-116">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="fec2b-117">L’exemple suivant <xref:System.Windows.Forms.Button> utilise <xref:System.Windows.Forms.Control.Click> le gestionnaire d’événements du contrôle pour ouvrir le <xref:System.Windows.Forms.OpenFileDialog> filtre qui affiche uniquement les fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="fec2b-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="fec2b-118">Une fois que l’utilisateur choisit un <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> fichier texte et sélectionne **OK,** la méthode est utilisée pour ouvrir le fichier dans Notepad.</span><span class="sxs-lookup"><span data-stu-id="fec2b-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="fec2b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fec2b-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="fec2b-120">Composant OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="fec2b-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
