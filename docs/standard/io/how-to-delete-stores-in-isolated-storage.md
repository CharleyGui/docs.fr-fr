---
title: 'Procédure : supprimer des magasins dans le stockage isolé'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a935ec663dd178d35aff745e907d2aae48e5b65c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622591"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="587ba-102">Procédure : supprimer des magasins dans le stockage isolé</span><span class="sxs-lookup"><span data-stu-id="587ba-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="587ba-103">La classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fournit deux méthodes pour supprimer les fichiers de stockage isolés :</span><span class="sxs-lookup"><span data-stu-id="587ba-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="587ba-104">La méthode d’instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> n’accepte pas d’argument et supprime le magasin qui l’appelle.</span><span class="sxs-lookup"><span data-stu-id="587ba-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="587ba-105">Aucune autorisation n’est nécessaire pour cette opération.</span><span class="sxs-lookup"><span data-stu-id="587ba-105">No permissions are required for this operation.</span></span> <span data-ttu-id="587ba-106">Tout code pouvant accéder au magasin peut supprimer tout ou partie des données qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="587ba-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="587ba-107">La méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> prend la valeur d’énumération <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> et supprime tous les magasins pour l’utilisateur qui exécute le code.</span><span class="sxs-lookup"><span data-stu-id="587ba-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="587ba-108">Cette opération nécessite une autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> pour la valeur <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> .</span><span class="sxs-lookup"><span data-stu-id="587ba-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="587ba-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="587ba-109">Example</span></span>  
 <span data-ttu-id="587ba-110">L’exemple de code suivant illustre l’utilisation des méthodes d’instance et statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> .</span><span class="sxs-lookup"><span data-stu-id="587ba-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="587ba-111">La classe obtient deux magasins. L’un est isolé pour l’utilisateur et l’assembly, et l’autre est isolé pour l’utilisateur, le domaine et l’assembly.</span><span class="sxs-lookup"><span data-stu-id="587ba-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="587ba-112">Le magasin de l’utilisateur, du domaine et de l’assembly est ensuite supprimé en appelant la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> du fichier de stockage isolé  `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="587ba-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="587ba-113">Ensuite, tous les magasins restants pour l’utilisateur sont supprimés en appelant la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="587ba-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="587ba-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="587ba-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="587ba-115">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="587ba-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
