---
title: Méthode ICLRStrongName::GetHashFromFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176368"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="a704f-102">Méthode ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="a704f-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="a704f-103">Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="a704f-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a704f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a704f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="a704f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a704f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a704f-106">[dans] Le nom Unicode du fichier au hachage.</span><span class="sxs-lookup"><span data-stu-id="a704f-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a704f-107">[dans, dehors] L’algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="a704f-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="a704f-108">Les algorithmes valides sont ceux définis par le CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="a704f-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="a704f-109">Si `piHashAlg` l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a704f-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a704f-110">[out] Un tableau d’en-lieu contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="a704f-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a704f-111">[dans] La taille maximale de la `pbHash`mémoire tampon indiquée par .</span><span class="sxs-lookup"><span data-stu-id="a704f-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a704f-112">[out] La taille, dans les `pbHash`octets, de .</span><span class="sxs-lookup"><span data-stu-id="a704f-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a704f-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a704f-113">Return Value</span></span>  
 <span data-ttu-id="a704f-114">`S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="a704f-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a704f-115">Notes </span><span class="sxs-lookup"><span data-stu-id="a704f-115">Remarks</span></span>  
 <span data-ttu-id="a704f-116">Cette méthode est la même que la méthode [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) méthode, sauf que la spécification nom de fichier est Unicode au lieu de ANSI.</span><span class="sxs-lookup"><span data-stu-id="a704f-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a704f-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a704f-117">Requirements</span></span>  
 <span data-ttu-id="a704f-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a704f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a704f-119">**En-tête:** MetaHost.h MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a704f-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a704f-120">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a704f-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a704f-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a704f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a704f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a704f-122">See also</span></span>

- [<span data-ttu-id="a704f-123">GetHashFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="a704f-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="a704f-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a704f-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
