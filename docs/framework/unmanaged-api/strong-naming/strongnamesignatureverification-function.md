---
title: StrongNameSignatureVerification, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
ms.openlocfilehash: c47d693f450b9cafcb4c8a388c8c38afcd2094e6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725714"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="dd544-102">StrongNameSignatureVerification, fonction</span><span class="sxs-lookup"><span data-stu-id="dd544-102">StrongNameSignatureVerification Function</span></span>

<span data-ttu-id="dd544-103">Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="dd544-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="dd544-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="dd544-104">This function has been deprecated.</span></span> <span data-ttu-id="dd544-105">Utilisez la méthode [ICLRStrongName :: StrongNameSignatureVerification (](../hosting/iclrstrongname-strongnamesignatureverification-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="dd544-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd544-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd544-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd544-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dd544-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="dd544-108">dans Chemin d’accès au fichier exécutable portable (. dll ou. exe) de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="dd544-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="dd544-109">dans Indicateurs permettant de modifier le comportement de vérification.</span><span class="sxs-lookup"><span data-stu-id="dd544-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="dd544-110">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="dd544-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="dd544-111">`SN_INFLAG_FORCE_VER` (0x00000001) : force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="dd544-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="dd544-112">`SN_INFLAG_INSTALL` (0x00000002) : spécifie qu’il s’agit de la première fois que le manifeste est vérifié.</span><span class="sxs-lookup"><span data-stu-id="dd544-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="dd544-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) : spécifie que le cache autorise uniquement l’accès aux utilisateurs disposant de privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="dd544-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="dd544-114">`SN_INFLAG_USER_ACCESS` (0x00000008) : spécifie que l’assembly sera uniquement accessible à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="dd544-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="dd544-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) : spécifie que le cache ne fournit aucune garantie de restriction d’accès.</span><span class="sxs-lookup"><span data-stu-id="dd544-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="dd544-116">`SN_INFLAG_RUNTIME` (0x80000000)-réservé au débogage interne.</span><span class="sxs-lookup"><span data-stu-id="dd544-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="dd544-117">à Indicateurs indiquant si la signature de nom fort a été vérifiée.</span><span class="sxs-lookup"><span data-stu-id="dd544-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="dd544-118">La valeur suivante est prise en charge :</span><span class="sxs-lookup"><span data-stu-id="dd544-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="dd544-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="dd544-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd544-120">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="dd544-120">Return Value</span></span>  

 <span data-ttu-id="dd544-121">`true` Si la vérification a réussi ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="dd544-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd544-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dd544-122">Requirements</span></span>  

 <span data-ttu-id="dd544-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd544-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd544-124">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="dd544-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dd544-125">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd544-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd544-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd544-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd544-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd544-127">See also</span></span>

- [<span data-ttu-id="dd544-128">StrongNameSignatureVerification, méthode</span><span class="sxs-lookup"><span data-stu-id="dd544-128">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="dd544-129">StrongNameSignatureVerificationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="dd544-129">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="dd544-130">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="dd544-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
