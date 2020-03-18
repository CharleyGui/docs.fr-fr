---
title: Suppression de magasins
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
ms.openlocfilehash: 6b1e8e651fd8e18c79dd629c154fb6c4d74243e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707825"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Suppression de magasins
La classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fournit deux méthodes pour supprimer les fichiers de stockage isolés :  
  
- La méthode d’instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> n’accepte pas d’argument et supprime le magasin qui l’appelle. Aucune autorisation n’est nécessaire pour cette opération. Tout code pouvant accéder au magasin peut supprimer tout ou partie des données qu’il contient.  
  
- La méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> prend la valeur d’énumération <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> et supprime tous les magasins pour l’utilisateur qui exécute le code. Cette opération nécessite une autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> pour la valeur <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> .  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant illustre l’utilisation des méthodes d’instance et statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> . La classe obtient deux magasins. L’un est isolé pour l’utilisateur et l’assembly, et l’autre est isolé pour l’utilisateur, le domaine et l’assembly. Le magasin de l’utilisateur, du domaine et de l’assembly est ensuite supprimé en appelant la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> du fichier de stockage isolé  `isoStore1`. Ensuite, tous les magasins restants pour l’utilisateur sont supprimés en appelant la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
