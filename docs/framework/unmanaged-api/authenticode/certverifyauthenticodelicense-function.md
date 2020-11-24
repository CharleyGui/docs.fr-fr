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
ms.openlocfilehash: 388814d1c63f048c0aa231a1d0058a390cba9493
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674058"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="08673-102">CertVerifyAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="08673-102">CertVerifyAuthenticodeLicense Function</span></span>

<span data-ttu-id="08673-103">Vérifie la validité d'une licence XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="08673-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08673-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08673-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08673-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08673-105">Parameters</span></span>  

 `pLicenseBlob`  
 <span data-ttu-id="08673-106">[en entrée] La licence XrML Authenticode à vérifier.</span><span class="sxs-lookup"><span data-stu-id="08673-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="08673-107">Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="08673-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="08673-108">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="08673-108">[in] Optional.</span></span> <span data-ttu-id="08673-109">Une combinaison des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="08673-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="08673-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="08673-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="08673-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="08673-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="08673-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="08673-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="08673-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="08673-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="08673-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="08673-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="08673-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="08673-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="08673-116">[en sortie] Pour recevoir les informations du signataire.</span><span class="sxs-lookup"><span data-stu-id="08673-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="08673-117">Si la licence n'était pas signée, `dwError` est défini à TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="08673-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="08673-118">Il incombe à l’appelant de libérer des ressources à l’aide de la fonction [certfreeauthenticodesignerinfo,](certfreeauthenticodesignerinfo-function.md) après utilisation.</span><span class="sxs-lookup"><span data-stu-id="08673-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="08673-119">Consultez [AXL_AUTHENTICODE_SIGNER_INFO structure](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="08673-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="08673-120">[en sortie] Pour recevoir les informations de l'horodateur, si elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="08673-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="08673-121">Si la licence n'était pas horodatée, `dwError` est défini à TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="08673-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="08673-122">Il incombe à l’appelant de libérer des ressources à l’aide de la fonction [certfreeauthenticodetimestamperinfo,](certfreeauthenticodetimestamperinfo-function.md) après utilisation.</span><span class="sxs-lookup"><span data-stu-id="08673-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="08673-123">Consultez [AXL_AUTHENTICODE_TIMESTAMPER_INFO structure](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="08673-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08673-124">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="08673-124">Return Value</span></span>  

 <span data-ttu-id="08673-125">Retourne `S_OK` en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="08673-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="08673-126">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="08673-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08673-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08673-127">See also</span></span>

- [<span data-ttu-id="08673-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="08673-128">Authenticode</span></span>](index.md)
- [<span data-ttu-id="08673-129">GetHashFromHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="08673-129">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="08673-130">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="08673-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
