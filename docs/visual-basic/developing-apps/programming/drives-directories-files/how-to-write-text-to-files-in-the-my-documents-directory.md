---
title: 'Procédure : écrire du texte dans des fichiers du répertoire Mes documents'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bb3a9bdc44f86fbcdb3c56ee088740efdfebe95d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546456"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Comment : insérer du texte dans les fichiers du répertoire Mes Documents dans Visual Basic

L’objet `My.Computer.FileSystem.SpecialDirectories` vous permet d’accéder à des répertoires spéciaux, comme le répertoire **Mes documents**.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Pour écrire de nouveaux fichiers texte dans le répertoire Mes Documents  
  
1. Utilisez la propriété `My.Computer.FileSystem.SpecialDirectories.MyDocuments` pour fournir le chemin.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Utilisez la méthode `WriteAllText` pour écrire du texte dans le fichier spécifié.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a> Exemple  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilation du code  

 Remplacez `test.txt` par le nom du fichier dans lequel vous voulez écrire.  
  
## <a name="robust-programming"></a>Programmation fiable  

 Ce code lève de nouveau toutes les exceptions qui peuvent se produire lors de l’écriture de texte dans le fichier. Vous pouvez réduire la probabilité d’exceptions en utilisant des contrôles Windows Forms comme les composants [OpenFileDialog](/dotnet/desktop/winforms/controls/openfiledialog-component-windows-forms) et [SaveFileDialog](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms) qui limitent les choix de l’utilisateur à des noms de fichier valides. Toutefois, l’utilisation de ces contrôles n’est pas infaillible. Le système de fichiers peut changer entre le moment où l’utilisateur sélectionne un fichier et celui où le code s’exécute. La gestion des exceptions est donc presque toujours nécessaire quand vous utilisez des fichiers.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Si vous l’exécutez dans un contexte de confiance partielle, le code peut lever une exception en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).  
  
 Cet exemple crée un fichier. Si une application doit créer un fichier, elle doit disposer de l’autorisation de création sur le dossier. Les autorisations sont définies à l’aide des listes de contrôle d’accès. Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation d’écriture, ce qui représente une autorisation inférieure. Quand cela est possible, il est plus sûr de créer le fichier pendant le déploiement et de n’accorder les privilèges de lecture que sur un seul fichier, plutôt que d’accorder des privilèges de création sur un dossier. En outre, il est plus sûr d’écrire des données dans des dossiers utilisateur que dans le dossier racine ou le dossier **Program Files** . Pour plus d’informations, consultez [Vue d’ensemble de la technologie ACL](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
