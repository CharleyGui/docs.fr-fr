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
ms.openlocfilehash: 081df31d1e3b1ca3345fe44b60cff6af27386953
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762121"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="62e2f-102">Méthode ICLRStrongName::GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="62e2f-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="62e2f-103">Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="62e2f-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62e2f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="62e2f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62e2f-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="62e2f-106">dans Pointeur vers l’adresse du bloc de mémoire à hacher.</span><span class="sxs-lookup"><span data-stu-id="62e2f-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="62e2f-107">dans Longueur, en octets, du bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="62e2f-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="62e2f-108">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="62e2f-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="62e2f-109">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="62e2f-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="62e2f-110">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="62e2f-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="62e2f-111">dans Taille maximale demandée de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="62e2f-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="62e2f-112">à Taille, en octets, du retourné `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="62e2f-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62e2f-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="62e2f-113">Return Value</span></span>  
 <span data-ttu-id="62e2f-114">`S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="62e2f-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e2f-115">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="62e2f-115">Requirements</span></span>  
 <span data-ttu-id="62e2f-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62e2f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62e2f-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="62e2f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="62e2f-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="62e2f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62e2f-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62e2f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e2f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62e2f-120">See also</span></span>

- [<span data-ttu-id="62e2f-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="62e2f-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
