---
title: LinkResource, méthode
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 335d80255f7a3f5a22e8a69aa91c9e5b0843ea1e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741590"
---
# <a name="linkresource-method"></a><span data-ttu-id="9443c-102">LinkResource, méthode</span><span class="sxs-lookup"><span data-stu-id="9443c-102">LinkResource Method</span></span>
<span data-ttu-id="9443c-103">Liens dans une ressource.</span><span class="sxs-lookup"><span data-stu-id="9443c-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9443c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9443c-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9443c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9443c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9443c-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9443c-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="9443c-107">Nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="9443c-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="9443c-108">Nouveau nom de fichier facultatif.</span><span class="sxs-lookup"><span data-stu-id="9443c-108">Optional new file name.</span></span> <span data-ttu-id="9443c-109">Si non NULL, `pszFileName` sera copié vers pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="9443c-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="9443c-110">Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="9443c-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9443c-111">Accessibilité indicateurs tels que `mrPublic` et `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="9443c-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="9443c-112">Ce paramètre peut être passé à [DefineManifestResource, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="9443c-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9443c-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9443c-113">Return Value</span></span>  
 <span data-ttu-id="9443c-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="9443c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9443c-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9443c-115">Requirements</span></span>  
 <span data-ttu-id="9443c-116">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="9443c-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9443c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9443c-117">See also</span></span>

- [<span data-ttu-id="9443c-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="9443c-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9443c-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="9443c-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9443c-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="9443c-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
