---
title: Méthode ICLRStrongName::StrongNameKeyGenEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: 1a5bcfb7a272af694126025f28ca3efe5a881c15
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135023"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="9d3a9-102">Méthode ICLRStrongName::StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="9d3a9-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="9d3a9-103">Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée, pour une utilisation avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d3a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d3a9-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d3a9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d3a9-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="9d3a9-106">dans Nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-106">[in] The requested key container name.</span></span> <span data-ttu-id="9d3a9-107">`wszKeyContainer` doit être une chaîne non vide ou null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9d3a9-108">dans Valeur qui spécifie s’il faut conserver la clé inscrite.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="9d3a9-109">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="9d3a9-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="9d3a9-110">0x00000000-utilisé lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="9d3a9-111">0x00000001 (`SN_LEAVE_KEY`) : spécifie que la clé doit rester inscrite.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="9d3a9-112">dans Taille demandée de la clé, en bits.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="9d3a9-113">à Paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="9d3a9-114">à Taille, en octets, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d3a9-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9d3a9-115">Return Value</span></span>  
 <span data-ttu-id="9d3a9-116">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="9d3a9-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d3a9-117">Notes</span><span class="sxs-lookup"><span data-stu-id="9d3a9-117">Remarks</span></span>  
 <span data-ttu-id="9d3a9-118">Les versions 1,0 et 1,1 de .NET Framework requièrent un `dwKeySize` de 1024 bits pour signer un assembly avec un nom fort ; la version 2,0 ajoute prend en charge les clés 2048 bits.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="9d3a9-119">Une fois la clé Récupérée, vous devez appeler la méthode [ICLRStrongName :: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d3a9-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="9d3a9-120">Requirements</span></span>  
 <span data-ttu-id="9d3a9-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d3a9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d3a9-122">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="9d3a9-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d3a9-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d3a9-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d3a9-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d3a9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3a9-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d3a9-125">See also</span></span>

- [<span data-ttu-id="9d3a9-126">StrongNameKeyGen, méthode</span><span class="sxs-lookup"><span data-stu-id="9d3a9-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="9d3a9-127">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="9d3a9-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
