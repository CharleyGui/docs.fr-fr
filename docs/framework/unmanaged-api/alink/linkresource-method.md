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
ms.openlocfilehash: 763b7a776007c2ce8dac42c6a5f7f00f6eb58a10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776943"
---
# <a name="linkresource-method"></a><span data-ttu-id="c1af6-102">LinkResource, méthode</span><span class="sxs-lookup"><span data-stu-id="c1af6-102">LinkResource Method</span></span>
<span data-ttu-id="c1af6-103">Liens dans une ressource.</span><span class="sxs-lookup"><span data-stu-id="c1af6-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1af6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1af6-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1af6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1af6-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c1af6-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c1af6-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="c1af6-107">Nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="c1af6-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="c1af6-108">Nouveau nom de fichier facultatif.</span><span class="sxs-lookup"><span data-stu-id="c1af6-108">Optional new file name.</span></span> <span data-ttu-id="c1af6-109">Si la valeur est non `pszFileName` null, sera copié dans pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="c1af6-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="c1af6-110">Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="c1af6-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c1af6-111">Indicateurs d’accessibilité tels `mrPublic` que `mrPrivate`et.</span><span class="sxs-lookup"><span data-stu-id="c1af6-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="c1af6-112">Ce paramètre peut être passé à la [méthode DefineManifestResource,](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="c1af6-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1af6-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c1af6-113">Return Value</span></span>  
 <span data-ttu-id="c1af6-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c1af6-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1af6-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1af6-115">Requirements</span></span>  
 <span data-ttu-id="c1af6-116">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c1af6-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1af6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1af6-117">See also</span></span>

- [<span data-ttu-id="c1af6-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="c1af6-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c1af6-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="c1af6-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c1af6-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="c1af6-120">ALink API</span></span>](index.md)
