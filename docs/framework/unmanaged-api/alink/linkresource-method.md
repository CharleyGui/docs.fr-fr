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
ms.openlocfilehash: 4f2f13976dfd4e5601bf8b54bed7b851884fbb9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690445"
---
# <a name="linkresource-method"></a><span data-ttu-id="6e1f9-102">LinkResource, méthode</span><span class="sxs-lookup"><span data-stu-id="6e1f9-102">LinkResource Method</span></span>

<span data-ttu-id="6e1f9-103">Liens dans une ressource.</span><span class="sxs-lookup"><span data-stu-id="6e1f9-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e1f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e1f9-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e1f9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e1f9-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="6e1f9-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6e1f9-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="6e1f9-107">Nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="6e1f9-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="6e1f9-108">Nouveau nom de fichier facultatif.</span><span class="sxs-lookup"><span data-stu-id="6e1f9-108">Optional new file name.</span></span> <span data-ttu-id="6e1f9-109">Si la valeur est non NULL, `pszFileName` sera copié dans pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="6e1f9-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="6e1f9-110">Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="6e1f9-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6e1f9-111">Indicateurs d’accessibilité tels que `mrPublic` et `mrPrivate` .</span><span class="sxs-lookup"><span data-stu-id="6e1f9-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="6e1f9-112">Ce paramètre peut être passé à la [méthode DefineManifestResource,](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="6e1f9-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e1f9-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6e1f9-113">Return Value</span></span>  

 <span data-ttu-id="6e1f9-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="6e1f9-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e1f9-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6e1f9-115">Requirements</span></span>  

 <span data-ttu-id="6e1f9-116">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="6e1f9-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1f9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e1f9-117">See also</span></span>

- [<span data-ttu-id="6e1f9-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="6e1f9-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6e1f9-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="6e1f9-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6e1f9-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="6e1f9-120">ALink API</span></span>](index.md)
