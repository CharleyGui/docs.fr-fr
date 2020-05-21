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
ms.openlocfilehash: e2003ce78f04b101fe093867e0820f9c3840151a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762706"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="80958-102">Méthode ICLRStrongName::StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="80958-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="80958-103">Obtient une valeur qui indique si le manifeste de l’assembly au chemin d’accès fourni contient une signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="80958-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80958-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80958-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80958-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="80958-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="80958-106">dans Chemin d’accès au fichier exécutable portable (. exe ou. dll) de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="80958-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="80958-107">[in] `true` pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres du Registre ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="80958-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="80958-108">[out] `true` Si la signature de nom fort a été vérifiée ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="80958-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="80958-109">`pfWasVerified`est également défini sur `false` si la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="80958-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80958-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="80958-110">Return Value</span></span>  
 <span data-ttu-id="80958-111">`S_OK`Si la vérification a réussi ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="80958-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80958-112">Notes</span><span class="sxs-lookup"><span data-stu-id="80958-112">Remarks</span></span>  
 <span data-ttu-id="80958-113">La méthode [ICLRStrongName :: StrongNameSignatureVerificationEx (](iclrstrongname-strongnamesignatureverificationex-method.md) fournit une fonctionnalité semblable à la méthode [ICLRStrongName :: StrongNameSignatureVerification (](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="80958-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="80958-114">Toutefois, le deuxième paramètre d’entrée et le paramètre de sortie pour [ICLRStrongName :: StrongNameSignatureVerificationEx (](iclrstrongname-strongnamesignatureverificationex-method.md) sont de type `BOOLEAN` au lieu de `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="80958-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80958-115">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="80958-115">Requirements</span></span>  
 <span data-ttu-id="80958-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80958-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80958-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="80958-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="80958-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80958-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80958-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80958-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80958-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80958-120">See also</span></span>

- [<span data-ttu-id="80958-121">StrongNameSignatureVerification, méthode</span><span class="sxs-lookup"><span data-stu-id="80958-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="80958-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="80958-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
