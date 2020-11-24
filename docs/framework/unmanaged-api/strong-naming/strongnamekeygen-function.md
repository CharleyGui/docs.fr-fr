---
title: StrongNameKeyGen, fonction
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: 4844701784a3e6a1008a5deb2bdff3b3ba47aa7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691407"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="2ac6e-102">StrongNameKeyGen, fonction</span><span class="sxs-lookup"><span data-stu-id="2ac6e-102">StrongNameKeyGen Function</span></span>

<span data-ttu-id="2ac6e-103">Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="2ac6e-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-104">This function has been deprecated.</span></span> <span data-ttu-id="2ac6e-105">Utilisez la méthode [ICLRStrongName :: StrongNameKeyGen (](../hosting/iclrstrongname-strongnamekeygen-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ac6e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ac6e-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ac6e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ac6e-107">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="2ac6e-108">dans Nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-108">[in] The requested key container name.</span></span> <span data-ttu-id="2ac6e-109">`wszKeyContainer` doit être une chaîne non vide, ou null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2ac6e-110">dans Spécifie s’il faut conserver la clé inscrite.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="2ac6e-111">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="2ac6e-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="2ac6e-112">0x00000000-utilisé lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="2ac6e-113">0x00000001 ( `SN_LEAVE_KEY` ) : spécifie que la clé doit rester inscrite.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="2ac6e-114">à Paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="2ac6e-115">à Taille, en octets, de `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="2ac6e-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ac6e-116">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2ac6e-116">Return Value</span></span>  

 <span data-ttu-id="2ac6e-117">`true` en cas de réussite de l’opération ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="2ac6e-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ac6e-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="2ac6e-118">Remarks</span></span>  

 <span data-ttu-id="2ac6e-119">La `StrongNameKeyGen` fonction crée une clé de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="2ac6e-120">Une fois la clé Récupérée, vous devez appeler la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="2ac6e-121">Si la `StrongNameKeyGen` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="2ac6e-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ac6e-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ac6e-122">Requirements</span></span>  

 <span data-ttu-id="2ac6e-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ac6e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ac6e-124">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="2ac6e-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2ac6e-125">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ac6e-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ac6e-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ac6e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac6e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ac6e-127">See also</span></span>

- [<span data-ttu-id="2ac6e-128">StrongNameKeyGen, méthode</span><span class="sxs-lookup"><span data-stu-id="2ac6e-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="2ac6e-129">StrongNameKeyGenEx, méthode</span><span class="sxs-lookup"><span data-stu-id="2ac6e-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="2ac6e-130">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="2ac6e-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
