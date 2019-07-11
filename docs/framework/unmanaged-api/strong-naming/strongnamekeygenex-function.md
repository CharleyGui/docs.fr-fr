---
title: StrongNameKeyGenEx, fonction
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2ed9ba4b580b8f64fc05dbb429742442a36acf5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757463"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="ed915-102">StrongNameKeyGenEx, fonction</span><span class="sxs-lookup"><span data-stu-id="ed915-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="ed915-103">Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée, pour une utilisation de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ed915-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="ed915-104">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="ed915-104">This function has been deprecated.</span></span> <span data-ttu-id="ed915-105">Utilisez le [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="ed915-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed915-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed915-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed915-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ed915-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ed915-108">[in] Le nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="ed915-108">[in] The requested key container name.</span></span> <span data-ttu-id="ed915-109">`wszKeyContainer` doit être une chaîne non vide, ou null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="ed915-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ed915-110">[in] Spécifie s’il faut laisser la clé enregistrée.</span><span class="sxs-lookup"><span data-stu-id="ed915-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="ed915-111">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="ed915-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="ed915-112">0 x 00000000 - utilisée lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="ed915-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="ed915-113">0 x 00000001 (`SN_LEAVE_KEY`)-Spécifie que la clé doit être inscrit à gauche.</span><span class="sxs-lookup"><span data-stu-id="ed915-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="ed915-114">[in] La taille demandée de la clé, en bits.</span><span class="sxs-lookup"><span data-stu-id="ed915-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="ed915-115">[out] La paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="ed915-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="ed915-116">[out] La taille, en octets, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ed915-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed915-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ed915-117">Return Value</span></span>  
 <span data-ttu-id="ed915-118">`true` de réussite ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ed915-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed915-119">Notes</span><span class="sxs-lookup"><span data-stu-id="ed915-119">Remarks</span></span>  
 <span data-ttu-id="ed915-120">Les versions 1.0 et 1.1 du .NET Framework nécessitent une `dwKeySize` de 1024 bits pour signer un assembly avec un nom fort ; version 2.0 ajoute prend en charge des clés 2048 bits.</span><span class="sxs-lookup"><span data-stu-id="ed915-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="ed915-121">Une fois que la clé est récupérée, vous devez appeler la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) (fonction) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="ed915-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="ed915-122">Si le `StrongNameKeyGenEx` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="ed915-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed915-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ed915-123">Requirements</span></span>  
 <span data-ttu-id="ed915-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed915-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed915-125">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ed915-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ed915-126">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed915-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed915-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed915-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed915-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed915-128">See also</span></span>

- [<span data-ttu-id="ed915-129">StrongNameKeyGenEx, méthode</span><span class="sxs-lookup"><span data-stu-id="ed915-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="ed915-130">StrongNameKeyGen, méthode</span><span class="sxs-lookup"><span data-stu-id="ed915-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="ed915-131">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ed915-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
