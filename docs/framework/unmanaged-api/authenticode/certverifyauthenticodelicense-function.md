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
ms.openlocfilehash: 7cd25a24533b04dc45ee734f9e9639391311405a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099740"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="ebc5d-102">CertVerifyAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="ebc5d-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="ebc5d-103">Vérifie la validité d'une licence XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebc5d-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebc5d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ebc5d-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="ebc5d-106">[en entrée] La licence XrML Authenticode à vérifier.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="ebc5d-107">Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="ebc5d-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ebc5d-108">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-108">[in] Optional.</span></span> <span data-ttu-id="ebc5d-109">Une combinaison des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ebc5d-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="ebc5d-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="ebc5d-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="ebc5d-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="ebc5d-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="ebc5d-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="ebc5d-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="ebc5d-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="ebc5d-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="ebc5d-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="ebc5d-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="ebc5d-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="ebc5d-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="ebc5d-116">[en sortie] Pour recevoir les informations du signataire.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="ebc5d-117">Si la licence n'était pas signée, `dwError` est défini à TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="ebc5d-118">Il incombe à l’appelant de libérer des ressources à l’aide de la fonction [certfreeauthenticodesignerinfo,](certfreeauthenticodesignerinfo-function.md) après utilisation.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="ebc5d-119">Consultez [structure AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="ebc5d-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="ebc5d-120">[en sortie] Pour recevoir les informations de l'horodateur, si elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="ebc5d-121">Si la licence n'était pas horodatée, `dwError` est défini à TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="ebc5d-122">Il incombe à l’appelant de libérer des ressources à l’aide de la fonction [certfreeauthenticodetimestamperinfo,](certfreeauthenticodetimestamperinfo-function.md) après utilisation.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="ebc5d-123">Consultez [structure AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="ebc5d-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebc5d-124">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ebc5d-124">Return Value</span></span>  
 <span data-ttu-id="ebc5d-125">Retourne `S_OK` en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="ebc5d-126">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="ebc5d-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc5d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebc5d-127">See also</span></span>

- [<span data-ttu-id="ebc5d-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ebc5d-128">Authenticode</span></span>](index.md)
- [<span data-ttu-id="ebc5d-129">GetHashFromHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="ebc5d-129">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="ebc5d-130">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ebc5d-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
