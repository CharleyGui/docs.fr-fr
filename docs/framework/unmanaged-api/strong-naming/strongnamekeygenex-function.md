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
ms.openlocfilehash: 63ddd90f3a8090853d10f03052915d10e1503ea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125217"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="3b81a-102">StrongNameKeyGenEx, fonction</span><span class="sxs-lookup"><span data-stu-id="3b81a-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="3b81a-103">Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée, pour une utilisation avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="3b81a-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="3b81a-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="3b81a-104">This function has been deprecated.</span></span> <span data-ttu-id="3b81a-105">Utilisez la méthode [ICLRStrongName :: StrongNameKeyGenEx (](../hosting/iclrstrongname-strongnamekeygenex-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="3b81a-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b81a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b81a-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b81a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b81a-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="3b81a-108">dans Nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="3b81a-108">[in] The requested key container name.</span></span> <span data-ttu-id="3b81a-109">`wszKeyContainer` doit être une chaîne non vide, ou null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="3b81a-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3b81a-110">dans Spécifie s’il faut conserver la clé inscrite.</span><span class="sxs-lookup"><span data-stu-id="3b81a-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="3b81a-111">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="3b81a-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="3b81a-112">0x00000000-utilisé lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="3b81a-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="3b81a-113">0x00000001 (`SN_LEAVE_KEY`) : spécifie que la clé doit rester inscrite.</span><span class="sxs-lookup"><span data-stu-id="3b81a-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="3b81a-114">dans Taille demandée de la clé, en bits.</span><span class="sxs-lookup"><span data-stu-id="3b81a-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="3b81a-115">à Paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="3b81a-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="3b81a-116">à Taille, en octets, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3b81a-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b81a-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3b81a-117">Return Value</span></span>  
 <span data-ttu-id="3b81a-118">`true` en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="3b81a-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b81a-119">Notes</span><span class="sxs-lookup"><span data-stu-id="3b81a-119">Remarks</span></span>  
 <span data-ttu-id="3b81a-120">Les versions 1,0 et 1,1 de .NET Framework requièrent un `dwKeySize` de 1024 bits pour signer un assembly avec un nom fort ; la version 2,0 ajoute prend en charge les clés 2048 bits.</span><span class="sxs-lookup"><span data-stu-id="3b81a-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="3b81a-121">Une fois la clé Récupérée, vous devez appeler la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="3b81a-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="3b81a-122">Si la fonction `StrongNameKeyGenEx` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="3b81a-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b81a-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="3b81a-123">Requirements</span></span>  
 <span data-ttu-id="3b81a-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b81a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b81a-125">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="3b81a-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3b81a-126">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3b81a-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b81a-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b81a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b81a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b81a-128">See also</span></span>

- [<span data-ttu-id="3b81a-129">StrongNameKeyGenEx, méthode</span><span class="sxs-lookup"><span data-stu-id="3b81a-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="3b81a-130">StrongNameKeyGen, méthode</span><span class="sxs-lookup"><span data-stu-id="3b81a-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="3b81a-131">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="3b81a-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
