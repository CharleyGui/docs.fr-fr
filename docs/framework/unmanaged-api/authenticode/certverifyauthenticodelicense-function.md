---
title: CertVerifyAuthenticodeLicense, fonction
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf7e997282351cc10dd6da1fc405366ea67c7307
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741099"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="cb724-102">CertVerifyAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="cb724-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="cb724-103">Vérifie la validité d'une licence XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="cb724-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb724-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb724-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb724-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cb724-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="cb724-106">[en entrée] La licence XrML Authenticode à vérifier.</span><span class="sxs-lookup"><span data-stu-id="cb724-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="cb724-107">Consultez le [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span><span class="sxs-lookup"><span data-stu-id="cb724-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cb724-108">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb724-108">[in] Optional.</span></span> <span data-ttu-id="cb724-109">Une combinaison des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb724-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="cb724-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="cb724-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="cb724-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="cb724-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="cb724-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="cb724-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="cb724-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="cb724-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="cb724-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="cb724-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="cb724-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="cb724-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="cb724-116">[en sortie] Pour recevoir les informations du signataire.</span><span class="sxs-lookup"><span data-stu-id="cb724-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="cb724-117">Si la licence n'était pas signée, `dwError` est défini à TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="cb724-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="cb724-118">Il incombe l’appelant de libérer des ressources à l’aide de la [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) fonction après utilisation.</span><span class="sxs-lookup"><span data-stu-id="cb724-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="cb724-119">Consultez [axl_authenticode_signer_info, Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="cb724-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="cb724-120">[en sortie] Pour recevoir les informations de l'horodateur, si elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="cb724-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="cb724-121">Si la licence n'était pas horodatée, `dwError` est défini à TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="cb724-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="cb724-122">Il incombe l’appelant de libérer des ressources à l’aide de la [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) fonction après utilisation.</span><span class="sxs-lookup"><span data-stu-id="cb724-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="cb724-123">Consultez [axl_authenticode_timestamper_info, Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="cb724-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb724-124">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cb724-124">Return Value</span></span>  
 <span data-ttu-id="cb724-125">Retourne `S_OK` en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="cb724-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="cb724-126">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="cb724-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb724-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb724-127">See also</span></span>

- [<span data-ttu-id="cb724-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="cb724-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [<span data-ttu-id="cb724-129">GetHashFromHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="cb724-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="cb724-130">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="cb724-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
