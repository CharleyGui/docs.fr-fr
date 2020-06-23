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
# <a name="how-to-open-files-with-the-openfiledialog"></a>Comment : ouvrir des fichiers avec OpenFileDialog

Le <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> composant ouvre la boîte de dialogue Windows permettant de parcourir et de sélectionner des fichiers. Pour ouvrir et lire les fichiers sélectionnés, vous pouvez utiliser la <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> méthode ou créer une instance de la <xref:System.IO.StreamReader?displayProperty=nameWithType> classe. Les exemples suivants illustrent ces deux approches.

Dans .NET Framework, pour obtenir ou définir la propriété, vous devez disposer d' <xref:System.Windows.Forms.FileDialog.FileName%2A> un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe. Les exemples exécutent une <xref:System.Security.Permissions.FileIOPermission> vérification d’autorisation et peuvent lever une exception en raison de privilèges insuffisants si elle est exécutée dans un contexte de confiance partielle. Pour plus d’informations, consultez principes de base de la [sécurité d’accès du code](../../misc/code-access-security-basics.md).

Vous pouvez générer et exécuter ces exemples comme des applications .NET Framework à partir de la ligne de commande C# ou Visual Basic. Pour plus d’informations, consultez génération à partir de la [ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

À compter de .NET Core 3,0, vous pouvez également générer et exécuter les exemples en tant qu’applications Windows .NET Core à partir d’un dossier qui contient un fichier projet .NET Core Windows Forms * \<folder name> . csproj* .

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Exemple : lire un fichier en tant que flux avec StreamReader  
  
L’exemple suivant utilise le <xref:System.Windows.Forms.Button> Gestionnaire d’événements du contrôle Windows Forms <xref:System.Windows.Forms.Control.Click> pour ouvrir <xref:System.Windows.Forms.OpenFileDialog> avec la <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> méthode. Une fois que l’utilisateur a choisi un fichier et qu’il a sélectionné **OK**, une instance de la <xref:System.IO.StreamReader> classe lit le fichier et affiche son contenu dans la zone de texte du formulaire. Pour plus d’informations sur la lecture à partir des flux de fichiers, consultez <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> et <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> .  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Exemple : ouvrir un fichier à partir d’une sélection filtrée avec OpenFile

L’exemple suivant utilise le <xref:System.Windows.Forms.Button> Gestionnaire d' <xref:System.Windows.Forms.Control.Click> événements du contrôle pour ouvrir le <xref:System.Windows.Forms.OpenFileDialog> avec un filtre qui affiche uniquement les fichiers texte. Une fois que l’utilisateur a choisi un fichier texte et sélectionne **OK**, la <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode est utilisée pour ouvrir le fichier dans le bloc-notes.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog, composant](openfiledialog-component-windows-forms.md)
