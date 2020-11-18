---
title: 'Procédure : ajouter ou supprimer des entrées de liste Access Control (.NET Framework uniquement)'
ms.date: 01/14/2019
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
ms.openlocfilehash: 49cbb27c1b9d7ae0b05077c7f4fe01a2dfe87ccb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820798"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Procédure : ajouter ou supprimer des entrées de liste Access Control (.NET Framework uniquement)

Pour ajouter ou supprimer des entrées de la liste de contrôle d’accès (ACL) dans un fichier ou un répertoire, récupérez l’objet <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> dans le fichier ou le répertoire. Modifiez l’objet, puis appliquez-le de nouveau au fichier ou au répertoire.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Ajouter ou supprimer une entrée ACL dans un fichier  
  
1. Appelez la méthode <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> pour obtenir un objet <xref:System.Security.AccessControl.FileSecurity> contenant les entrées ACL actuelles d'un fichier.  
  
2. Ajoutez ou supprimez des entrées ACL à partir de l'objet <xref:System.Security.AccessControl.FileSecurity> retourné à l'étape 1.  
  
3. Pour appliquer les modifications, passez l’objet <xref:System.Security.AccessControl.FileSecurity> à la méthode <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Ajouter ou supprimer une entrée ACL dans un répertoire  
  
1. Appelez la méthode <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> pour obtenir un objet <xref:System.Security.AccessControl.DirectorySecurity> contenant les entrées ACL actuelles d'un répertoire.  
  
2. Ajoutez ou supprimez des entrées ACL à partir de l'objet <xref:System.Security.AccessControl.DirectorySecurity> retourné à l'étape 1.  
  
3. Pour appliquer les modifications, passez l’objet <xref:System.Security.AccessControl.DirectorySecurity> à la méthode <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemple  
 Vous devez utiliser un compte d’utilisateur ou de groupe valide pour exécuter cet exemple. Cet exemple utilise un objet <xref:System.IO.File>. Utilisez la même procédure pour les classes <xref:System.IO.FileInfo>, <xref:System.IO.Directory> et <xref:System.IO.DirectoryInfo>.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
