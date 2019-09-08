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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798915"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="8f487-102">StrongNameSignatureVerificationEx, fonction</span><span class="sxs-lookup"><span data-stu-id="8f487-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="8f487-103">Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="8f487-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="8f487-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="8f487-104">This function has been deprecated.</span></span> <span data-ttu-id="8f487-105">Utilisez la méthode [ICLRStrongName :: StrongNameSignatureVerificationEx (](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="8f487-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f487-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f487-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f487-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8f487-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="8f487-108">dans Chemin d’accès au fichier exécutable portable (. exe ou. dll) de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="8f487-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="8f487-109">dans pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres du Registre ; `false`sinon,. `true`</span><span class="sxs-lookup"><span data-stu-id="8f487-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="8f487-110">à Si la signature de nom fort a été vérifiée ; sinon, `false`. `true`</span><span class="sxs-lookup"><span data-stu-id="8f487-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="8f487-111">`pfWasVerified`est également défini sur `false` si la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="8f487-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f487-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8f487-112">Return Value</span></span>  
 <span data-ttu-id="8f487-113">`true`Si la vérification a réussi ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="8f487-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f487-114">Notes</span><span class="sxs-lookup"><span data-stu-id="8f487-114">Remarks</span></span>  
 <span data-ttu-id="8f487-115">`StrongNameSignatureVerificationEx`fournit une fonctionnalité similaire à la fonction [StrongNameSignatureVerification (](strongnamesignatureverification-function.md) .</span><span class="sxs-lookup"><span data-stu-id="8f487-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="8f487-116">Toutefois, le deuxième paramètre d’entrée et le paramètre de `StrongNameSignatureVerificationEx` sortie de sont `BOOLEAN` de type `DWORD`au lieu de.</span><span class="sxs-lookup"><span data-stu-id="8f487-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f487-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8f487-117">Requirements</span></span>  
 <span data-ttu-id="8f487-118">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f487-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f487-119">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="8f487-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8f487-120">**Bibliothèque** Inclus en tant que ressource dans Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8f487-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="8f487-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f487-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f487-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f487-122">See also</span></span>

- [<span data-ttu-id="8f487-123">StrongNameSignatureVerificationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="8f487-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="8f487-124">StrongNameSignatureVerification, méthode</span><span class="sxs-lookup"><span data-stu-id="8f487-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="8f487-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="8f487-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
