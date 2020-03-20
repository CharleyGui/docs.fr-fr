---
title: Méthode ICLRStrongName::GetHashFromFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ed735c3d7830551581df35793f3f6fdc4953dc8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178073"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="e4d0a-102">Méthode ICLRStrongName::GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="e4d0a-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="e4d0a-103">Génère un hachage sur le contenu du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4d0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4d0a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4d0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e4d0a-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="e4d0a-106">[dans] Le nom du fichier au hachage.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e4d0a-107">[dans, dehors] L’algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="e4d0a-108">Les algorithmes valides sont ceux définis par le CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="e4d0a-109">Si `piHashAlg` l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e4d0a-110">[out] Un tableau d’en-lieu contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e4d0a-111">[dans] La taille maximale du `pbHash` tampon qui indique.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e4d0a-112">[out] La taille, dans les octets, du retour `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4d0a-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e4d0a-113">Return Value</span></span>  
 <span data-ttu-id="e4d0a-114">`S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="e4d0a-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4d0a-115">Notes </span><span class="sxs-lookup"><span data-stu-id="e4d0a-115">Remarks</span></span>  
 <span data-ttu-id="e4d0a-116">Cette méthode est la même que la méthode [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) méthode, sauf que la spécification nom de fichier est ANSI au lieu d’Unicode.</span><span class="sxs-lookup"><span data-stu-id="e4d0a-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4d0a-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e4d0a-117">Requirements</span></span>  
 <span data-ttu-id="e4d0a-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4d0a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4d0a-119">**En-tête:** MetaHost.h MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e4d0a-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e4d0a-120">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4d0a-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4d0a-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4d0a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d0a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4d0a-122">See also</span></span>

- [<span data-ttu-id="e4d0a-123">GetHashFromFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="e4d0a-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="e4d0a-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="e4d0a-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
