---
title: "Comment : anticiper des conditions d'espace insuffisant avec le stockage isolé"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
ms.openlocfilehash: 5666019e1a65880221261ef5ad704f82c37263b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708113"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Comment : anticiper des conditions d'espace insuffisant avec le stockage isolé

Le code qui utilise le stockage isolé est limité par un [quota](../../../docs/standard/io/isolated-storage.md#quotas) qui spécifie la taille maximale du compartiment de données dans lequel des fichiers et répertoires de stockage isolé existent. Le quota est défini par la stratégie de sécurité et peut être configuré par les administrateurs. Si la taille maximale autorisée est dépassée lorsque vous tenez d’écrire des données, une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> est levée et l’opération échoue. Cela permet d’éviter des attaques malveillantes par déni de service, qui pourraient amener l’application à refuser des requêtes parce que le stockage des données est rempli.

Pour vous aider à déterminer si une tentative d’écriture donnée est susceptible d’échouer pour cette raison, la classe <xref:System.IO.IsolatedStorage.IsolatedStorage> fournit trois propriétés en lecture seule : <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Vous pouvez utiliser ces propriétés pour déterminer si l’écriture dans le magasin entraînera le dépassement de la taille maximale autorisée de ce dernier. N’oubliez pas que le stockage isolé est accessible simultanément. Par conséquent, lorsque vous calculez la quantité de stockage restant, l’espace de stockage peut être consommé pendant que vous tentez d’écrire dans le magasin. Toutefois, vous pouvez utiliser la taille maximale du magasin pour aider à déterminer si la limite maximale de stockage disponible est sur le point d’être atteinte.

La propriété <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> dépend de la preuve du bon fonctionnement de l’assembly. Pour cette raison, vous devez récupérer cette propriété uniquement sur des objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> créés à l’aide de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>. Les objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> qui ont été créés d’une autre façon (par exemple, les objets retournés à partir de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> ne retourneront pas une taille maximale précise.

## <a name="example"></a> Exemple

L’exemple de code suivant obtient un magasin isolé, crée quelques fichiers et récupère la propriété <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>. L’espace restant est indiqué en octets.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
- [Obtention de magasins](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
