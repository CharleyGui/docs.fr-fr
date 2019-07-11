---
title: Méthode ICLRStrongName::StrongNameGetBlobFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e13f0ebbdc4e5fe3974208f91ab57f86dd29c910
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748012"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="ff787-102">Méthode ICLRStrongName::StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="ff787-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="ff787-103">Obtient une représentation binaire de l’image de l’assembly à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ff787-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff787-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff787-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff787-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff787-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="ff787-106">[in] L’adresse mémoire du manifeste d’assembly mappé.</span><span class="sxs-lookup"><span data-stu-id="ff787-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ff787-107">[in] La taille, en octets, de l’image à `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="ff787-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="ff787-108">[in] Une mémoire tampon pour contenir la représentation binaire de l’image.</span><span class="sxs-lookup"><span data-stu-id="ff787-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="ff787-109">[in, out] La taille maximale en octets, demandée de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="ff787-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="ff787-110">Au retour, la taille réelle, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="ff787-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff787-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ff787-111">Return Value</span></span>  
 <span data-ttu-id="ff787-112">`S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="ff787-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff787-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ff787-113">Requirements</span></span>  
 <span data-ttu-id="ff787-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff787-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff787-115">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ff787-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ff787-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff787-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff787-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff787-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff787-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff787-118">See also</span></span>

- [<span data-ttu-id="ff787-119">StrongNameGetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="ff787-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="ff787-120">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ff787-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
