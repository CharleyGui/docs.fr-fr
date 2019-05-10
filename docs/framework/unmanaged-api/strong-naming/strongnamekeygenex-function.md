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
ms.openlocfilehash: 736e537a3f773acbd61dbad013b8dfb7cc429076
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666018"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="8c8d2-102">StrongNameKeyGenEx, fonction</span><span class="sxs-lookup"><span data-stu-id="8c8d2-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="8c8d2-103">Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée, pour une utilisation de nom fort.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="8c8d2-104">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-104">This function has been deprecated.</span></span> <span data-ttu-id="8c8d2-105">Utilisez le [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8d2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c8d2-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c8d2-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c8d2-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="8c8d2-108">[in] Le nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-108">[in] The requested key container name.</span></span> <span data-ttu-id="8c8d2-109">`wszKeyContainer` doit être une chaîne non vide, ou null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8c8d2-110">[in] Spécifie s’il faut laisser la clé enregistrée.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="8c8d2-111">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="8c8d2-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="8c8d2-112">0 x 00000000 - utilisée lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="8c8d2-113">0 x 00000001 (`SN_LEAVE_KEY`)-Spécifie que la clé doit être inscrit à gauche.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="8c8d2-114">[in] La taille demandée de la clé, en bits.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="8c8d2-115">[out] La paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="8c8d2-116">[out] La taille, en octets, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c8d2-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8c8d2-117">Return Value</span></span>  
 <span data-ttu-id="8c8d2-118">`true` de réussite ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c8d2-119">Notes</span><span class="sxs-lookup"><span data-stu-id="8c8d2-119">Remarks</span></span>  
 <span data-ttu-id="8c8d2-120">Les versions 1.0 et 1.1 du .NET Framework nécessitent une `dwKeySize` de 1024 bits pour signer un assembly avec un nom fort ; version 2.0 ajoute prend en charge des clés 2048 bits.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="8c8d2-121">Une fois que la clé est récupérée, vous devez appeler la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) (fonction) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="8c8d2-122">Si le `StrongNameKeyGenEx` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c8d2-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8c8d2-123">Requirements</span></span>  
 <span data-ttu-id="8c8d2-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c8d2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c8d2-125">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="8c8d2-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8c8d2-126">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c8d2-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c8d2-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c8d2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8d2-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c8d2-128">See also</span></span>

- [<span data-ttu-id="8c8d2-129">StrongNameKeyGenEx, méthode</span><span class="sxs-lookup"><span data-stu-id="8c8d2-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="8c8d2-130">StrongNameKeyGen, méthode</span><span class="sxs-lookup"><span data-stu-id="8c8d2-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="8c8d2-131">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="8c8d2-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
