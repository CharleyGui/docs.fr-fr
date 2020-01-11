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
ms.openlocfilehash: a0bcc62a1715fb455f0affee64a351cabe0ba3f6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901121"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="ebb38-102">Méthode ICLRStrongName::StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="ebb38-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="ebb38-103">Obtient une représentation binaire de l’image de l’assembly à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ebb38-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebb38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebb38-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebb38-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="ebb38-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="ebb38-106">dans Adresse mémoire du manifeste de l’assembly mappé.</span><span class="sxs-lookup"><span data-stu-id="ebb38-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ebb38-107">dans Taille, en octets, de l’image à `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="ebb38-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="ebb38-108">dans Mémoire tampon destinée à contenir la représentation binaire de l’image.</span><span class="sxs-lookup"><span data-stu-id="ebb38-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="ebb38-109">[in, out] Taille maximale demandée, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="ebb38-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="ebb38-110">Lors du retour, taille réelle, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="ebb38-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebb38-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ebb38-111">Return Value</span></span>  
 <span data-ttu-id="ebb38-112">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="ebb38-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebb38-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ebb38-113">Requirements</span></span>  
 <span data-ttu-id="ebb38-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebb38-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebb38-115">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="ebb38-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ebb38-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ebb38-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebb38-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebb38-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb38-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebb38-118">See also</span></span>

- [<span data-ttu-id="ebb38-119">StrongNameGetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="ebb38-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="ebb38-120">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ebb38-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
