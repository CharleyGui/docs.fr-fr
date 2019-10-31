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
ms.openlocfilehash: 0c9adcc252fe16c95da8b2afca45bb2ee5dc545a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135206"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="2e61c-102">Méthode ICLRStrongName::GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="2e61c-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="2e61c-103">Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="2e61c-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e61c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e61c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2e61c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e61c-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="2e61c-106">dans Pointeur vers l’adresse du bloc de mémoire à hacher.</span><span class="sxs-lookup"><span data-stu-id="2e61c-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="2e61c-107">dans Longueur, en octets, du bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="2e61c-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2e61c-108">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="2e61c-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2e61c-109">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="2e61c-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2e61c-110">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="2e61c-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2e61c-111">dans Taille maximale de `pbHash`demandée.</span><span class="sxs-lookup"><span data-stu-id="2e61c-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2e61c-112">à Taille, en octets, de la `pbHash`retournée.</span><span class="sxs-lookup"><span data-stu-id="2e61c-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e61c-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2e61c-113">Return Value</span></span>  
 <span data-ttu-id="2e61c-114">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="2e61c-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e61c-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="2e61c-115">Requirements</span></span>  
 <span data-ttu-id="2e61c-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e61c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e61c-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="2e61c-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2e61c-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e61c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e61c-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e61c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e61c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e61c-120">See also</span></span>

- [<span data-ttu-id="2e61c-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="2e61c-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
