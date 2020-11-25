---
title: StrongNameSignatureVerificationFromImage, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: b90cc6fe99cf592f1b3fd117888462a957e4ce35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708424"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="59540-102">StrongNameSignatureVerificationFromImage, fonction</span><span class="sxs-lookup"><span data-stu-id="59540-102">StrongNameSignatureVerificationFromImage Function</span></span>

<span data-ttu-id="59540-103">Vérifie qu’un assembly qui a déjà été mappé en mémoire est valide pour la clé publique associée.</span><span class="sxs-lookup"><span data-stu-id="59540-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="59540-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="59540-104">This function has been deprecated.</span></span> <span data-ttu-id="59540-105">Utilisez la méthode [ICLRStrongName :: StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="59540-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59540-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59540-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59540-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59540-107">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="59540-108">dans Adresse virtuelle relative du manifeste de l’assembly mappé.</span><span class="sxs-lookup"><span data-stu-id="59540-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="59540-109">dans Taille, en octets, de l’image mappée.</span><span class="sxs-lookup"><span data-stu-id="59540-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="59540-110">dans Indicateurs qui influencent le comportement de la vérification.</span><span class="sxs-lookup"><span data-stu-id="59540-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="59540-111">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="59540-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="59540-112">`SN_INFLAG_FORCE_VER` (0x00000001) : force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="59540-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="59540-113">`SN_INFLAG_INSTALL` (0x00000002) : spécifie qu’il s’agit de la première vérification effectuée sur cette image.</span><span class="sxs-lookup"><span data-stu-id="59540-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="59540-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) : spécifie que le cache autorise uniquement l’accès aux utilisateurs disposant de privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="59540-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="59540-115">`SN_INFLAG_USER_ACCESS` (0x00000008) : spécifie que l’assembly sera uniquement accessible à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="59540-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="59540-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) : spécifie que le cache ne fournit aucune garantie de restriction d’accès.</span><span class="sxs-lookup"><span data-stu-id="59540-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="59540-117">`SN_INFLAG_RUNTIME` (0x80000000)-réservé au débogage interne.</span><span class="sxs-lookup"><span data-stu-id="59540-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="59540-118">à Indicateur pour les informations de sortie supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="59540-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="59540-119">La valeur suivante est prise en charge :</span><span class="sxs-lookup"><span data-stu-id="59540-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="59540-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="59540-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59540-121">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="59540-121">Return Value</span></span>  

 <span data-ttu-id="59540-122">`true` en cas de réussite de l’opération ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="59540-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59540-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="59540-123">Remarks</span></span>  

 <span data-ttu-id="59540-124">Si la `StrongNameSignatureVerificationFromImage` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="59540-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59540-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="59540-125">Requirements</span></span>  

 <span data-ttu-id="59540-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59540-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59540-127">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="59540-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="59540-128">**Bibliothèque :** Inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="59540-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="59540-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59540-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59540-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59540-130">See also</span></span>

- [<span data-ttu-id="59540-131">StrongNameSignatureVerificationFromImage, méthode</span><span class="sxs-lookup"><span data-stu-id="59540-131">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="59540-132">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="59540-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
