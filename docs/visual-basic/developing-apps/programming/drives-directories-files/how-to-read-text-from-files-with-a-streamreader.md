---
title: 'Procédure : lire du texte à partir de fichiers avec un StreamReader'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 6d05dac9b612659a74e25c0ce87c7524316d31a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411601"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Guide pratique pour lire le texte des fichiers avec un StreamReader (Visual Basic)

L’objet `My.Computer.FileSystem` fournit des méthodes pour ouvrir un <xref:System.IO.TextReader> et <xref:System.IO.TextWriter>. Ces méthodes, `OpenTextFileWriter` et `OpenTextFileReader`, sont des méthodes avancées qui n’apparaissent pas dans IntelliSense, sauf si vous sélectionnez l’onglet **Tout**.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Pour lire une ligne dans un fichier avec un lecteur de texte  
  
- Utilisez la méthode `OpenTextFileReader` pour ouvrir le <xref:System.IO.TextReader>, en spécifiant le fichier. Cet exemple ouvre le fichier nommé `testfile.txt`, y lit une ligne et l’affiche dans une boîte de message.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 Le fichier lu doit être un fichier texte.  
  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu. Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.  
  
 Vérifiez toutes les entrées avant d'utiliser les données dans votre application. Le fichier n'a peut-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Pour lire un fichier, votre assembly nécessite un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission>. Si vous l’exécutez dans un contexte de confiance partielle, le code peut lever une exception en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md). L’utilisateur doit également avoir accès au fichier. Pour plus d’informations, consultez [Vue d’ensemble de la technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [SaveFileDialog, composant](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Lecture à partir de fichiers](reading-from-files.md)
