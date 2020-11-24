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
ms.openlocfilehash: 53daa88b761f46dab26b1c12c73741e880512d8d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682690"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="c4b6d-102">Procédure : ajouter ou supprimer des entrées de liste Access Control (.NET Framework uniquement)</span><span class="sxs-lookup"><span data-stu-id="c4b6d-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>

<span data-ttu-id="c4b6d-103">Pour ajouter ou supprimer des entrées de la liste de contrôle d’accès (ACL) dans un fichier ou un répertoire, récupérez l’objet <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> dans le fichier ou le répertoire.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="c4b6d-104">Modifiez l’objet, puis appliquez-le de nouveau au fichier ou au répertoire.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="c4b6d-105">Ajouter ou supprimer une entrée ACL dans un fichier</span><span class="sxs-lookup"><span data-stu-id="c4b6d-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="c4b6d-106">Appelez la méthode <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> pour obtenir un objet <xref:System.Security.AccessControl.FileSecurity> contenant les entrées ACL actuelles d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="c4b6d-107">Ajoutez ou supprimez des entrées ACL à partir de l'objet <xref:System.Security.AccessControl.FileSecurity> retourné à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="c4b6d-108">Pour appliquer les modifications, passez l’objet <xref:System.Security.AccessControl.FileSecurity> à la méthode <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="c4b6d-109">Ajouter ou supprimer une entrée ACL dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="c4b6d-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="c4b6d-110">Appelez la méthode <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> pour obtenir un objet <xref:System.Security.AccessControl.DirectorySecurity> contenant les entrées ACL actuelles d'un répertoire.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="c4b6d-111">Ajoutez ou supprimez des entrées ACL à partir de l'objet <xref:System.Security.AccessControl.DirectorySecurity> retourné à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="c4b6d-112">Pour appliquer les modifications, passez l’objet <xref:System.Security.AccessControl.DirectorySecurity> à la méthode <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b6d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4b6d-113">Example</span></span>  

 <span data-ttu-id="c4b6d-114">Vous devez utiliser un compte d’utilisateur ou de groupe valide pour exécuter cet exemple.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="c4b6d-115">Cet exemple utilise un objet <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="c4b6d-116">Utilisez la même procédure pour les classes <xref:System.IO.FileInfo>, <xref:System.IO.Directory> et <xref:System.IO.DirectoryInfo>.</span><span class="sxs-lookup"><span data-stu-id="c4b6d-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
