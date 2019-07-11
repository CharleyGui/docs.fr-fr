---
title: StrongNameTokenFromAssemblyEx, fonction
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14af44901e7c65933800e41328e95602ce715282
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783181"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="f990e-102">StrongNameTokenFromAssemblyEx, fonction</span><span class="sxs-lookup"><span data-stu-id="f990e-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="f990e-103">Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique qui représente le jeton.</span><span class="sxs-lookup"><span data-stu-id="f990e-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="f990e-104">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="f990e-104">This function has been deprecated.</span></span> <span data-ttu-id="f990e-105">Utilisez le [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="f990e-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f990e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f990e-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f990e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f990e-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f990e-108">[in] Le chemin d’accès au fichier exécutable portable (PE) pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f990e-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="f990e-109">[out] Le jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="f990e-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="f990e-110">[out] La taille, en octets, du jeton de nom fort.</span><span class="sxs-lookup"><span data-stu-id="f990e-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="f990e-111">[out] La clé publique retournée.</span><span class="sxs-lookup"><span data-stu-id="f990e-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="f990e-112">[out] La taille, en octets, de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="f990e-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f990e-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f990e-113">Return Value</span></span>  
 <span data-ttu-id="f990e-114">`true` de réussite ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="f990e-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f990e-115">Notes</span><span class="sxs-lookup"><span data-stu-id="f990e-115">Remarks</span></span>  
 <span data-ttu-id="f990e-116">Un jeton de nom fort est la forme abrégée d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="f990e-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="f990e-117">Le jeton est un hachage 64 bits qui est créé à partir de la clé publique utilisée pour signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f990e-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="f990e-118">Le jeton est une partie du nom fort pour l’assembly et peut être lues à partir des métadonnées d’assembly.</span><span class="sxs-lookup"><span data-stu-id="f990e-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="f990e-119">Une fois que la clé est récupérée et le jeton est créé, vous devez appeler la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) (fonction) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="f990e-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="f990e-120">Si le `StrongNameTokenFromAssemblyEx` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="f990e-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f990e-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f990e-121">Requirements</span></span>  
 <span data-ttu-id="f990e-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f990e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f990e-123">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f990e-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f990e-124">**Bibliothèque :** Inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f990e-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="f990e-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f990e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f990e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f990e-126">See also</span></span>

- [<span data-ttu-id="f990e-127">StrongNameTokenFromAssemblyEx, méthode</span><span class="sxs-lookup"><span data-stu-id="f990e-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="f990e-128">StrongNameTokenFromAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="f990e-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="f990e-129">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="f990e-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
