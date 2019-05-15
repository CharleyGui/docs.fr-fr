---
title: 'Procédure : créer un fichier en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: f24fdd6ce1fea7540c33e4a2fdfc06885825f76a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628987"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Procédure : créer un fichier en Visual Basic
Cet exemple crée un fichier texte vide à l’emplacement spécifié à l’aide de la méthode <xref:System.IO.File.Create%2A> de la classe <xref:System.IO.File>.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Utilisez la variable `file` pour écrire dans le fichier.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si le fichier existe déjà, il est remplacé.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le chemin d'accès est mal formé. Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (<xref:System.ArgumentException>).  
  
- Le chemin est en lecture seule (<xref:System.IO.IOException>).  
  
- Le nom du chemin est `Nothing` (<xref:System.ArgumentNullException>).  
  
- Le nom du chemin est trop long (<xref:System.IO.PathTooLongException>).  
  
- Le chemin n’est pas valide (<xref:System.IO.DirectoryNotFoundException>).  
  
- Le chemin n’est constitué que d’un signe deux-points « : » (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Une <xref:System.Security.SecurityException> peut être levée dans les environnements de confiance partielle.  
  
 L’appel à la méthode <xref:System.IO.File.Create%2A> nécessite <xref:System.Security.Permissions.FileIOPermission>.  
  
 Une <xref:System.UnauthorizedAccessException> est levée si l’utilisateur n’est pas autorisé à créer le fichier.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Utilisation de bibliothèques à partir de code d’un niveau de confiance partiel](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md)
