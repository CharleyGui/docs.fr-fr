---
title: Méthode ICLRStrongName::GetHashFromBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4839f098a41e0d2b8e87616791b69ffd83e139f0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748194"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="029f5-102">Méthode ICLRStrongName::GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="029f5-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="029f5-103">Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="029f5-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="029f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="029f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="029f5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="029f5-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="029f5-106">[in] Pointeur vers l’adresse du bloc de mémoire à hacher.</span><span class="sxs-lookup"><span data-stu-id="029f5-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="029f5-107">[in] La longueur, en octets, du bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="029f5-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="029f5-108">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="029f5-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="029f5-109">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="029f5-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="029f5-110">[out] La mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="029f5-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="029f5-111">[in] La taille maximale demandée de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="029f5-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="029f5-112">[out] La taille, en octets, de retourné `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="029f5-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="029f5-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="029f5-113">Return Value</span></span>  
 <span data-ttu-id="029f5-114">`S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="029f5-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="029f5-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="029f5-115">Requirements</span></span>  
 <span data-ttu-id="029f5-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="029f5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="029f5-117">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="029f5-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="029f5-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="029f5-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="029f5-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="029f5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029f5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="029f5-120">See also</span></span>

- [<span data-ttu-id="029f5-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="029f5-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
