---
title: Méthode ICLRStrongName::StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: 6375fd8e4a314403267a4cdf2e8356677e9e7a06
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899487"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="6f802-102">Méthode ICLRStrongName::StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="6f802-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="6f802-103">Obtient une valeur qui indique si le manifeste de l’assembly au chemin d’accès fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6f802-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f802-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f802-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f802-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="6f802-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6f802-106">dans Chemin d’accès au fichier exécutable portable (. dll ou. exe) de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="6f802-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="6f802-107">dans Indicateurs permettant de modifier le comportement de vérification.</span><span class="sxs-lookup"><span data-stu-id="6f802-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="6f802-108">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="6f802-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="6f802-109">`SN_INFLAG_FORCE_VER` (0x00000001) : force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="6f802-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="6f802-110">`SN_INFLAG_INSTALL` (0x00000002) : spécifie qu’il s’agit de la première fois que le manifeste est vérifié.</span><span class="sxs-lookup"><span data-stu-id="6f802-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="6f802-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) : spécifie que le cache autorise l’accès uniquement aux utilisateurs disposant de privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="6f802-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="6f802-112">`SN_INFLAG_USER_ACCESS` (0x00000008) : spécifie que l’assembly sera uniquement accessible à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="6f802-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="6f802-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) : spécifie que le cache ne fournit aucune garantie de restriction d’accès.</span><span class="sxs-lookup"><span data-stu-id="6f802-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="6f802-114">`SN_INFLAG_RUNTIME` (0x80000000)-réservé au débogage interne.</span><span class="sxs-lookup"><span data-stu-id="6f802-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="6f802-115">à Indicateurs indiquant si la signature de nom fort a été vérifiée.</span><span class="sxs-lookup"><span data-stu-id="6f802-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="6f802-116">La valeur suivante est prise en charge :</span><span class="sxs-lookup"><span data-stu-id="6f802-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="6f802-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="6f802-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f802-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6f802-118">Return Value</span></span>  
 <span data-ttu-id="6f802-119">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="6f802-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f802-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6f802-120">Requirements</span></span>  
 <span data-ttu-id="6f802-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f802-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f802-122">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="6f802-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6f802-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6f802-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f802-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f802-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f802-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f802-125">See also</span></span>

- [<span data-ttu-id="6f802-126">StrongNameSignatureVerificationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="6f802-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="6f802-127">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="6f802-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
