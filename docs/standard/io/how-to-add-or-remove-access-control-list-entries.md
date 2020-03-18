---
title: 'Comment : Ajouter ou supprimer les entrées de la liste de contrôle d’accès (.NET Framework uniquement)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
ms.openlocfilehash: 5f41c518b8732adff95593cab29d7085adcc9ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708126"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Comment : Ajouter ou supprimer les entrées de la liste de contrôle d’accès (.NET Framework uniquement)
Pour ajouter ou supprimer des entrées de la liste de contrôle d’accès (ACL) dans un fichier ou un répertoire, récupérez l’objet <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> dans le fichier ou le répertoire. Modifiez l’objet, puis appliquez-le de nouveau au fichier ou au répertoire.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Ajouter ou supprimer une entrée ACL dans un fichier  
  
1. Appelez la méthode <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> pour obtenir un objet <xref:System.Security.AccessControl.FileSecurity> contenant les entrées ACL actuelles d'un fichier.  
  
2. Ajoutez ou supprimez des entrées ACL à partir de l'objet <xref:System.Security.AccessControl.FileSecurity> retourné à l'étape 1.  
  
3. Pour appliquer les modifications, passez l’objet <xref:System.Security.AccessControl.FileSecurity> à la méthode <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Ajouter ou supprimer une entrée ACL dans un répertoire  
  
1. Appelez la méthode <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> pour obtenir un objet <xref:System.Security.AccessControl.DirectorySecurity> contenant les entrées ACL actuelles d'un répertoire.  
  
2. Ajoutez ou supprimez des entrées ACL à partir de l'objet <xref:System.Security.AccessControl.DirectorySecurity> retourné à l'étape 1.  
  
3. Pour appliquer les modifications, passez l’objet <xref:System.Security.AccessControl.DirectorySecurity> à la méthode <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a> Exemple  
 Vous devez utiliser un compte d’utilisateur ou de groupe valide pour exécuter cet exemple. Cet exemple utilise un objet <xref:System.IO.File>. Utilisez la même procédure pour les classes <xref:System.IO.FileInfo>, <xref:System.IO.Directory> et <xref:System.IO.DirectoryInfo>.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
