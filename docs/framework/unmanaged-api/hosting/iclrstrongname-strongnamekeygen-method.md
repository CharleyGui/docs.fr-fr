---
title: Méthode ICLRStrongName::StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: 69ba58cc8c5235a15749281b3107481be9528f84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503976"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="51fa2-102">Méthode ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="51fa2-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="51fa2-103">Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.</span><span class="sxs-lookup"><span data-stu-id="51fa2-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51fa2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51fa2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51fa2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51fa2-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="51fa2-106">dans Nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="51fa2-106">[in] The requested key container name.</span></span> <span data-ttu-id="51fa2-107">`wszKeyContainer`doit être une chaîne non vide ou null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="51fa2-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="51fa2-108">dans Valeur qui spécifie s’il faut conserver la clé inscrite.</span><span class="sxs-lookup"><span data-stu-id="51fa2-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="51fa2-109">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="51fa2-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="51fa2-110">0x00000000-utilisé lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="51fa2-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="51fa2-111">0x00000001 ( `SN_LEAVE_KEY` ) : spécifie que la clé doit rester inscrite.</span><span class="sxs-lookup"><span data-stu-id="51fa2-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="51fa2-112">à Paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="51fa2-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="51fa2-113">à Taille, en octets, de `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="51fa2-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51fa2-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="51fa2-114">Return Value</span></span>  
 <span data-ttu-id="51fa2-115">`S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="51fa2-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51fa2-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="51fa2-116">Remarks</span></span>  
 <span data-ttu-id="51fa2-117">La méthode [ICLRStrongName :: StrongNameKeyGen (](iclrstrongname-strongnamekeygen-method.md) crée une clé de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="51fa2-117">The [ICLRStrongName::StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="51fa2-118">Une fois la clé Récupérée, vous devez appeler la méthode [ICLRStrongName :: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="51fa2-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51fa2-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="51fa2-119">Requirements</span></span>  
 <span data-ttu-id="51fa2-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51fa2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51fa2-121">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="51fa2-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="51fa2-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51fa2-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51fa2-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51fa2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fa2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51fa2-124">See also</span></span>

- [<span data-ttu-id="51fa2-125">StrongNameKeyGenEx, méthode</span><span class="sxs-lookup"><span data-stu-id="51fa2-125">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="51fa2-126">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="51fa2-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
