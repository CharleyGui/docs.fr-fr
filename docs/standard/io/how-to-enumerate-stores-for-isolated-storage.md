---
title: 'Procédure : énumérer des magasins pour le stockage isolé'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
ms.openlocfilehash: 732f121e6b1977a960cab207f8d56cd2a551383c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291862"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="4b005-102">Procédure : énumérer des magasins pour le stockage isolé</span><span class="sxs-lookup"><span data-stu-id="4b005-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="4b005-103">Vous pouvez énumérer tous les magasins isolés pour l’utilisateur actif à l’aide de la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b005-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="4b005-104">Cette méthode prend une valeur <xref:System.IO.IsolatedStorage.IsolatedStorageScope> et retourne un énumérateur <xref:System.IO.IsolatedStorage.IsolatedStorageFile>.</span><span class="sxs-lookup"><span data-stu-id="4b005-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="4b005-105">Pour énumérer les magasins, vous devez avoir l’autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> qui spécifie la valeur <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.</span><span class="sxs-lookup"><span data-stu-id="4b005-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="4b005-106">Si vous appelez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> avec la valeur <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, elle retourne un tableau d’objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> qui sont définis pour l’utilisateur actif.</span><span class="sxs-lookup"><span data-stu-id="4b005-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b005-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b005-107">Example</span></span>  
 <span data-ttu-id="4b005-108">L’exemple de code suivant obtient un magasin qui est isolé par utilisateur et par assembly, crée quelques fichiers, et récupère ces fichiers à l’aide de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b005-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4b005-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b005-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="4b005-110">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="4b005-110">Isolated Storage</span></span>](isolated-storage.md)
