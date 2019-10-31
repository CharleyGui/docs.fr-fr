---
title: StrongNameSignatureVerificationEx2, méthode
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
ms.openlocfilehash: cf8d6b7e45c0012d223173c85a92fac4fb044c6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141415"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="45332-102">StrongNameSignatureVerificationEx2, méthode</span><span class="sxs-lookup"><span data-stu-id="45332-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="45332-103">Vérifie la signature d’un assembly avec un nom fort et fournit un mappage de la clé ECMA à une clé réelle.</span><span class="sxs-lookup"><span data-stu-id="45332-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45332-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45332-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45332-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="45332-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="45332-106">dans Chemin d’accès au fichier exécutable portable (. exe ou. dll) de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="45332-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="45332-107">[in] `true` pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres du Registre ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="45332-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="45332-108">dans Pointeur vers le mappage de la clé publique ECMA à la clé réelle utilisée pour la vérification.</span><span class="sxs-lookup"><span data-stu-id="45332-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="45332-109">dans Longueur de la clé publique de l’ECMA réelle.</span><span class="sxs-lookup"><span data-stu-id="45332-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="45332-110">[out] `true` si la signature de nom fort a été vérifiée ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="45332-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="45332-111">Ce paramètre est également défini sur `false` si la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="45332-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45332-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="45332-112">Return Value</span></span>  
 <span data-ttu-id="45332-113">`S_OK` si la vérification a réussi ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="45332-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45332-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="45332-114">Requirements</span></span>  
 <span data-ttu-id="45332-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45332-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45332-116">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="45332-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="45332-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="45332-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45332-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45332-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45332-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45332-119">See also</span></span>

- [<span data-ttu-id="45332-120">StrongNameSignatureVerification, méthode</span><span class="sxs-lookup"><span data-stu-id="45332-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="45332-121">StrongNameSignatureVerificationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="45332-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="45332-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="45332-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
