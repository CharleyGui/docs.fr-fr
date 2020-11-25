---
title: StrongNameSignatureVerificationEx, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: 27417c379411e242c48d6d9b0c99de833f7ede8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719266"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="bdc59-102">StrongNameSignatureVerificationEx, fonction</span><span class="sxs-lookup"><span data-stu-id="bdc59-102">StrongNameSignatureVerificationEx Function</span></span>

<span data-ttu-id="bdc59-103">Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="bdc59-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="bdc59-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="bdc59-104">This function has been deprecated.</span></span> <span data-ttu-id="bdc59-105">Utilisez la méthode [ICLRStrongName :: StrongNameSignatureVerificationEx (](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="bdc59-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc59-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdc59-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdc59-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdc59-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="bdc59-108">dans Chemin d’accès au fichier exécutable portable (. exe ou. dll) de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="bdc59-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="bdc59-109">[in] `true` pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres du Registre ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="bdc59-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="bdc59-110">[out] `true` Si la signature de nom fort a été vérifiée ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="bdc59-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="bdc59-111">`pfWasVerified` est également défini sur `false` si la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="bdc59-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdc59-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bdc59-112">Return Value</span></span>  

 <span data-ttu-id="bdc59-113">`true` Si la vérification a réussi ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="bdc59-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdc59-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="bdc59-114">Remarks</span></span>  

 <span data-ttu-id="bdc59-115">`StrongNameSignatureVerificationEx` fournit une fonctionnalité similaire à la fonction [StrongNameSignatureVerification (](strongnamesignatureverification-function.md) .</span><span class="sxs-lookup"><span data-stu-id="bdc59-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="bdc59-116">Toutefois, le deuxième paramètre d’entrée et le paramètre de sortie de `StrongNameSignatureVerificationEx` sont de type `BOOLEAN` au lieu de `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="bdc59-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdc59-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bdc59-117">Requirements</span></span>  

 <span data-ttu-id="bdc59-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdc59-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdc59-119">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="bdc59-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bdc59-120">**Bibliothèque :** Inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bdc59-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="bdc59-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdc59-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc59-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdc59-122">See also</span></span>

- [<span data-ttu-id="bdc59-123">StrongNameSignatureVerificationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="bdc59-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="bdc59-124">StrongNameSignatureVerification, méthode</span><span class="sxs-lookup"><span data-stu-id="bdc59-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="bdc59-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="bdc59-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
