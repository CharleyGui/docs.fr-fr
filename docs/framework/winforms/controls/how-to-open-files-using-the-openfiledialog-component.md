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
# <a name="how-to-open-files-with-the-openfiledialog"></a>Comment: Ouvrir les fichiers avec l’OpenFileDialog

Le <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> composant ouvre la boîte de dialogue Windows pour la navigation et la sélection des fichiers. Pour ouvrir et lire les fichiers <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> sélectionnés, vous pouvez <xref:System.IO.StreamReader?displayProperty=nameWithType> utiliser la méthode, ou créer un exemple de la classe. Les exemples suivants montrent les deux approches.

Dans le cadre .NET, <xref:System.Windows.Forms.FileDialog.FileName%2A> pour obtenir ou définir <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> la propriété nécessite un niveau de privilège accordé par la classe. Les exemples <xref:System.Security.Permissions.FileIOPermission> exécutent une vérification d’autorisation, et peuvent jeter une exception en raison de privilèges insuffisants s’ils sont exécutés dans un contexte de fiducie partielle. Pour plus d’informations, voir [Les bases de sécurité d’accès au Code](../../misc/code-access-security-basics.md).

Vous pouvez créer et exécuter ces exemples sous forme d’applications cadres .NET de la ligne de commande C ou Visual Basic. Pour plus d’informations, voir [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

En commençant par .NET Core 3.0, vous pouvez également construire et exécuter les exemples comme Windows .NET Core applications à partir d’un dossier qui a un nom de dossier .NET Core Windows Forms * \<>.csproj* fichier de projet.

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Exemple : Lisez un fichier en streaming avec StreamReader  
  
L’exemple suivant utilise <xref:System.Windows.Forms.Button> le <xref:System.Windows.Forms.Control.Click> gestionnaire d’événements <xref:System.Windows.Forms.OpenFileDialog> du <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> contrôle des formulaires Windows pour l’ouvrir avec la méthode. Une fois que l’utilisateur **OK**choisit un fichier <xref:System.IO.StreamReader> et sélectionne OK , une instance de la classe lit le fichier et affiche son contenu dans la boîte de texte du formulaire. Pour plus d’informations sur la <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>lecture des flux de fichiers, voir et .  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Exemple : Ouvrez un fichier à partir d’une sélection filtrée avec OpenFile

L’exemple suivant <xref:System.Windows.Forms.Button> utilise <xref:System.Windows.Forms.Control.Click> le gestionnaire d’événements du contrôle pour ouvrir le <xref:System.Windows.Forms.OpenFileDialog> filtre qui affiche uniquement les fichiers texte. Une fois que l’utilisateur choisit un <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> fichier texte et sélectionne **OK,** la méthode est utilisée pour ouvrir le fichier dans Notepad.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.OpenFileDialog>
- [Composant OpenFileDialog](openfiledialog-component-windows-forms.md)
