---
title: GetHashFromFileW, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175081"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="23b7c-102">GetHashFromFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="23b7c-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="23b7c-103">Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="23b7c-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="23b7c-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="23b7c-104">This function has been deprecated.</span></span> <span data-ttu-id="23b7c-105">Utilisez la méthode [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="23b7c-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b7c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23b7c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="23b7c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23b7c-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="23b7c-108">[dans] Le nom Unicode du fichier au hachage.</span><span class="sxs-lookup"><span data-stu-id="23b7c-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="23b7c-109">[dans, dehors] L’algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="23b7c-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="23b7c-110">Les algorithmes valides sont ceux définis par le CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="23b7c-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="23b7c-111">Si `piHashAlg` l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="23b7c-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="23b7c-112">[out] Un tableau d’en-lieu contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="23b7c-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="23b7c-113">[dans] La taille maximale de la `pbHash`mémoire tampon indiquée par .</span><span class="sxs-lookup"><span data-stu-id="23b7c-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="23b7c-114">[out] La taille, dans les `pbHash`octets, de .</span><span class="sxs-lookup"><span data-stu-id="23b7c-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23b7c-115">Notes </span><span class="sxs-lookup"><span data-stu-id="23b7c-115">Remarks</span></span>  
 <span data-ttu-id="23b7c-116">Cette fonction est la même que [GetHashFromFile](gethashfromfile-function.md), sauf que la spécification nom de fichier est Unicode au lieu de ANSI.</span><span class="sxs-lookup"><span data-stu-id="23b7c-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23b7c-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="23b7c-117">Requirements</span></span>  
 <span data-ttu-id="23b7c-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23b7c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b7c-119">**En-tête:** StrongName.h (en)</span><span class="sxs-lookup"><span data-stu-id="23b7c-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="23b7c-120">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23b7c-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23b7c-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b7c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b7c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23b7c-122">See also</span></span>

- [<span data-ttu-id="23b7c-123">GetHashFromFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="23b7c-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="23b7c-124">GetHashFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="23b7c-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="23b7c-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="23b7c-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
