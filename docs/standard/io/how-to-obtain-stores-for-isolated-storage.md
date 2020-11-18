---
title: 'Procédure : obtenir des magasins pour le stockage isolé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
ms.openlocfilehash: a3803f50c99b8c31030c6afe756e209c9350137f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830738"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Procédure : obtenir des magasins pour le stockage isolé
Un magasin isolé expose un système de fichiers virtuel dans un compartiment de données. La classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fournit plusieurs méthodes pour interagir avec un magasin isolé. Pour créer et récupérer des magasins, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> propose trois méthodes statiques :  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> retourne un stockage isolé par utilisateur et par assembly.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> retourne un stockage isolé par domaine et par assembly.  
  
     Les deux méthodes récupèrent un magasin qui appartient au code à partir duquel elles sont appelées.  
  
- La méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> retourne un magasin isolé spécifié en passant une combinaison de paramètres d’étendue.  
  
 Le code suivant retourne un magasin isolé par utilisateur, assembly et domaine.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Vous pouvez utiliser la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> pour spécifier qu’un magasin doit se déplacer avec un profil utilisateur itinérant. Pour plus d’informations sur la façon de configurer ce paramètre, consultez [Types d’isolation](types-of-isolation.md).  
  
 Les magasins isolés obtenus à partir de différents assemblys sont, par défaut, des magasins différents. Vous pouvez accéder au magasin d’un domaine ou d’un assembly différent en passant la preuve d’assembly ou de domaine dans les paramètres de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>. Pour ce faire, l’autorisation d’accéder au stockage isolé par l’identité de domaine d’application est requise. Pour plus d'informations, consultez les surcharges de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  
  
 Les méthodes <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> retournent un objet <xref:System.IO.IsolatedStorage.IsolatedStorageFile>. Pour vous aider à déterminer le type d’isolation le plus approprié à votre situation, consultez [Types d’isolation](types-of-isolation.md). Lorsque vous disposez d’un objet de fichier de stockage isolé, vous pouvez utiliser les méthodes de stockage isolé pour lire, écrire, créer et supprimer des fichiers et répertoires.  
  
 Il n’existe aucun mécanisme qui empêche le code de passer un objet <xref:System.IO.IsolatedStorage.IsolatedStorageFile> vers du code qui n’a pas de droits d’accès suffisants pour obtenir le magasin lui-même. Les identités de domaine et d’assembly et les autorisations pour le stockage isolé sont vérifiées uniquement lorsqu’une référence à un objet <xref:System.IO.IsolatedStorage.IsolatedStorage> est obtenue, en général dans la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>. La protection des références aux objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> est, par conséquent, la responsabilité du code qui utilise ces références.  
  
## <a name="example"></a>Exemple  
 Le code suivant fournit un exemple simple d’une classe obtenant un magasin isolé par utilisateur et par assembly. Le code peut ensuite être modifié afin de récupérer un magasin isolé par utilisateur, domaine et assembly en ajoutant <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> aux arguments passés par la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  
  
 Après avoir exécuté le code, vous pouvez confirmer qu’un magasin a été créé en tapant **StoreAdm /LIST** sur la ligne de commande. Cette commande exécute [l’outil Stockage isolé (Storeadm.exe)](../../framework/tools/storeadm-exe-isolated-storage-tool.md) et répertorie tous les magasins actuellement isolés pour l’utilisateur.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Stockage isolé](isolated-storage.md)
- [Types d'isolation](types-of-isolation.md)
- [Assemblys dans .NET](../assembly/index.md)
