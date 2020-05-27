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
ms.openlocfilehash: 5e6f77b9b5da061a75d23d7f3f7b673754b62afd
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006361"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="20e20-102">StrongNameSignatureVerificationEx2, méthode</span><span class="sxs-lookup"><span data-stu-id="20e20-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="20e20-103">Vérifie la signature d’un assembly avec un nom fort et fournit un mappage de la clé ECMA à une clé réelle.</span><span class="sxs-lookup"><span data-stu-id="20e20-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20e20-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20e20-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20e20-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="20e20-106">dans Chemin d’accès au fichier exécutable portable (. exe ou. dll) de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="20e20-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="20e20-107">[in] `true` pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres du Registre ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="20e20-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="20e20-108">dans Pointeur vers le mappage de la clé publique ECMA à la clé réelle utilisée pour la vérification.</span><span class="sxs-lookup"><span data-stu-id="20e20-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="20e20-109">dans Longueur de la clé publique de l’ECMA réelle.</span><span class="sxs-lookup"><span data-stu-id="20e20-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="20e20-110">[out] `true` Si la signature de nom fort a été vérifiée ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="20e20-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="20e20-111">Ce paramètre est également défini sur `false` si la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="20e20-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20e20-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="20e20-112">Return Value</span></span>  
 <span data-ttu-id="20e20-113">`S_OK`Si la vérification a réussi ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="20e20-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e20-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="20e20-114">Requirements</span></span>  
 <span data-ttu-id="20e20-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20e20-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e20-116">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="20e20-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="20e20-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20e20-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20e20-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e20-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e20-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20e20-119">See also</span></span>

- [<span data-ttu-id="20e20-120">StrongNameSignatureVerification, méthode</span><span class="sxs-lookup"><span data-stu-id="20e20-120">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="20e20-121">StrongNameSignatureVerificationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="20e20-121">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="20e20-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="20e20-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
