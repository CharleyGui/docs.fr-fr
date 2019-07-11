---
title: Méthode ICLRStrongName::StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c535d3d73b6d3d0165ea2d744ef625a16bd76cd4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747835"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="31fa0-102">Méthode ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="31fa0-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="31fa0-103">Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.</span><span class="sxs-lookup"><span data-stu-id="31fa0-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fa0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31fa0-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31fa0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31fa0-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="31fa0-106">[in] Le nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="31fa0-106">[in] The requested key container name.</span></span> <span data-ttu-id="31fa0-107">`wszKeyContainer` doit être une chaîne non vide ou une valeur null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="31fa0-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="31fa0-108">[in] Une valeur qui spécifie s’il faut laisser la clé enregistrée.</span><span class="sxs-lookup"><span data-stu-id="31fa0-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="31fa0-109">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="31fa0-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="31fa0-110">0 x 00000000 - utilisée lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="31fa0-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="31fa0-111">0 x 00000001 (`SN_LEAVE_KEY`)-Spécifie que la clé doit être inscrit à gauche.</span><span class="sxs-lookup"><span data-stu-id="31fa0-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="31fa0-112">[out] La paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="31fa0-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="31fa0-113">[out] La taille, en octets, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="31fa0-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31fa0-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="31fa0-114">Return Value</span></span>  
 <span data-ttu-id="31fa0-115">`S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="31fa0-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31fa0-116">Notes</span><span class="sxs-lookup"><span data-stu-id="31fa0-116">Remarks</span></span>  
 <span data-ttu-id="31fa0-117">Le [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) méthode crée une clé 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="31fa0-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="31fa0-118">Une fois que la clé est récupérée, vous devez appeler la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="31fa0-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31fa0-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31fa0-119">Requirements</span></span>  
 <span data-ttu-id="31fa0-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31fa0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31fa0-121">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="31fa0-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="31fa0-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31fa0-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31fa0-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31fa0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fa0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31fa0-124">See also</span></span>

- [<span data-ttu-id="31fa0-125">StrongNameKeyGenEx, méthode</span><span class="sxs-lookup"><span data-stu-id="31fa0-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="31fa0-126">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="31fa0-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
