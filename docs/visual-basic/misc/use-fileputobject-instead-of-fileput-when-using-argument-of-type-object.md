---
title: Utilisez ’FilePutObject’ à la place de ’FilePut’ quand l’argument est de type ’Object’.
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: c6ae755ad3eca4b1c50b83049885b6cf66f13c07
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100332"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="d2a00-102">Utilisez ’FilePutObject’ à la place de ’FilePut’ quand l’argument est de type ’Object’.</span><span class="sxs-lookup"><span data-stu-id="d2a00-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>

<span data-ttu-id="d2a00-103">La méthode `FilePut` comprend un argument de type `Object`.</span><span class="sxs-lookup"><span data-stu-id="d2a00-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="d2a00-104">`FilePutObject` doit être utilisé à la place de `FilePut` pour éviter toute ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="d2a00-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2a00-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d2a00-105">To correct this error</span></span>  
  
- <span data-ttu-id="d2a00-106">Remplacez `FilePut` par `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="d2a00-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="d2a00-107">Convertissez l’argument `Object` en type plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="d2a00-107">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="d2a00-108">Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="d2a00-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a00-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2a00-109">See also</span></span>

- [<span data-ttu-id="d2a00-110">My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="d2a00-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="d2a00-111">My. Computer. FileSystem. WriteAllBytes,</span><span class="sxs-lookup"><span data-stu-id="d2a00-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
