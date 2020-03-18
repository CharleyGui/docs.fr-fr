---
title: Énumération de magasins
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
ms.openlocfilehash: 3ba38093e9e978c89cdb2bb7a584ed9e04c1096d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707526"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Énumération de magasins
Vous pouvez énumérer tous les magasins isolés pour l’utilisateur actif à l’aide de la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>. Cette méthode prend une valeur <xref:System.IO.IsolatedStorage.IsolatedStorageScope> et retourne un énumérateur <xref:System.IO.IsolatedStorage.IsolatedStorageFile>. Pour énumérer les magasins, vous devez avoir l’autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> qui spécifie la valeur <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>. Si vous appelez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> avec la valeur <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, elle retourne un tableau d’objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> qui sont définis pour l’utilisateur actif.  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant obtient un magasin qui est isolé par utilisateur et par assembly, crée quelques fichiers, et récupère ces fichiers à l’aide de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
