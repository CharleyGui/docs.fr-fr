---
title: Méthode ICLRStrongName::StrongNameSignatureVerificationEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: 9caeb72c57260012ae2b459950bf19d907da1d98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671549"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="58045-102">Méthode ICLRStrongName::StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="58045-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>

<span data-ttu-id="58045-103">Obtient une valeur qui indique si le manifeste de l’assembly au chemin d’accès fourni contient une signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="58045-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58045-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58045-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58045-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58045-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="58045-106">dans Chemin d’accès au fichier exécutable portable (. exe ou. dll) de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="58045-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="58045-107">[in] `true` pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres du Registre ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="58045-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="58045-108">[out] `true` Si la signature de nom fort a été vérifiée ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="58045-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="58045-109">`pfWasVerified` est également défini sur `false` si la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="58045-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58045-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="58045-110">Return Value</span></span>  

 <span data-ttu-id="58045-111">`S_OK` Si la vérification a réussi ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="58045-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58045-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="58045-112">Remarks</span></span>  

 <span data-ttu-id="58045-113">La méthode [ICLRStrongName :: StrongNameSignatureVerificationEx (](iclrstrongname-strongnamesignatureverificationex-method.md) fournit une fonctionnalité semblable à la méthode [ICLRStrongName :: StrongNameSignatureVerification (](iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="58045-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="58045-114">Toutefois, le deuxième paramètre d’entrée et le paramètre de sortie pour [ICLRStrongName :: StrongNameSignatureVerificationEx (](iclrstrongname-strongnamesignatureverificationex-method.md) sont de type `BOOLEAN` au lieu de `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="58045-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58045-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="58045-115">Requirements</span></span>  

 <span data-ttu-id="58045-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58045-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58045-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="58045-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="58045-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58045-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58045-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58045-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58045-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58045-120">See also</span></span>

- [<span data-ttu-id="58045-121">StrongNameSignatureVerification, méthode</span><span class="sxs-lookup"><span data-stu-id="58045-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="58045-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="58045-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
