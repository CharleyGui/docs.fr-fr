---
title: Méthode ICLRStrongName::StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: adb3b4e33edafe6d25c8259e316a9b62e339f896
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092667"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="faeb5-102">Méthode ICLRStrongName::StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="faeb5-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="faeb5-103">Vérifie qu’un assembly qui a déjà été mappé en mémoire est valide pour la clé publique associée.</span><span class="sxs-lookup"><span data-stu-id="faeb5-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faeb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faeb5-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faeb5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="faeb5-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="faeb5-106">dans Adresse virtuelle relative du manifeste de l’assembly mappé.</span><span class="sxs-lookup"><span data-stu-id="faeb5-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="faeb5-107">dans Taille, en octets, de l’image mappée.</span><span class="sxs-lookup"><span data-stu-id="faeb5-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="faeb5-108">dans Indicateurs qui influencent le comportement de la vérification.</span><span class="sxs-lookup"><span data-stu-id="faeb5-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="faeb5-109">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="faeb5-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="faeb5-110">`SN_INFLAG_FORCE_VER` (0x00000001) : force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="faeb5-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="faeb5-111">`SN_INFLAG_INSTALL` (0x00000002) : spécifie qu’il s’agit de la première vérification effectuée sur cette image.</span><span class="sxs-lookup"><span data-stu-id="faeb5-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="faeb5-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) : spécifie que le cache autorise l’accès uniquement aux utilisateurs disposant de privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="faeb5-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="faeb5-113">`SN_INFLAG_USER_ACCESS` (0x00000008) : spécifie que l’assembly sera uniquement accessible à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="faeb5-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="faeb5-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) : spécifie que le cache ne fournit aucune garantie de restriction d’accès.</span><span class="sxs-lookup"><span data-stu-id="faeb5-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="faeb5-115">`SN_INFLAG_RUNTIME` (0x80000000)-réservé au débogage interne.</span><span class="sxs-lookup"><span data-stu-id="faeb5-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="faeb5-116">à Indicateur pour les informations de sortie supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="faeb5-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="faeb5-117">La valeur suivante est prise en charge :</span><span class="sxs-lookup"><span data-stu-id="faeb5-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="faeb5-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="faeb5-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faeb5-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="faeb5-119">Return Value</span></span>  
 <span data-ttu-id="faeb5-120">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="faeb5-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faeb5-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="faeb5-121">Requirements</span></span>  
 <span data-ttu-id="faeb5-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faeb5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faeb5-123">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="faeb5-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="faeb5-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="faeb5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faeb5-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faeb5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faeb5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faeb5-126">See also</span></span>

- [<span data-ttu-id="faeb5-127">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="faeb5-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
