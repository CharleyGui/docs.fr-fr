---
title: StrongNameTokenFromPublicKey, fonction
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68be16c559431de871dc9ddb1963897b0927d49a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783164"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="a1f81-102">StrongNameTokenFromPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="a1f81-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="a1f81-103">Obtient un jeton représentant une clé publique.</span><span class="sxs-lookup"><span data-stu-id="a1f81-103">Gets a token representing a public key.</span></span> <span data-ttu-id="a1f81-104">Un jeton de nom fort est la forme abrégée d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="a1f81-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="a1f81-105">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="a1f81-105">This function has been deprecated.</span></span> <span data-ttu-id="a1f81-106">Utilisez le [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="a1f81-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f81-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1f81-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1f81-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1f81-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="a1f81-109">[in] Une structure de type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="a1f81-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="a1f81-110">[in] La taille, en octets, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a1f81-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="a1f81-111">[out] Le jeton de nom fort correspondant à la clé passée dans `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a1f81-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="a1f81-112">Le common language runtime alloue la mémoire dans lequel retourner le jeton.</span><span class="sxs-lookup"><span data-stu-id="a1f81-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="a1f81-113">L’appelant doit libérer cette mémoire en utilisant la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="a1f81-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="a1f81-114">[out] La taille, en octets, du jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="a1f81-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1f81-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a1f81-115">Return Value</span></span>  
 <span data-ttu-id="a1f81-116">`true` de réussite ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="a1f81-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1f81-117">Notes</span><span class="sxs-lookup"><span data-stu-id="a1f81-117">Remarks</span></span>  
 <span data-ttu-id="a1f81-118">Un jeton de nom fort est la forme abrégée d’une clé publique utilisée pour économiser de l’espace lorsque vous stockez des informations de clé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a1f81-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="a1f81-119">Plus précisément, les jetons de nom fort sont utilisés dans les références d’assembly pour faire référence à l’assembly dépendant.</span><span class="sxs-lookup"><span data-stu-id="a1f81-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="a1f81-120">Si le `StrongNameTokenFromPublicKey` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="a1f81-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f81-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1f81-121">Requirements</span></span>  
 <span data-ttu-id="a1f81-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f81-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f81-123">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a1f81-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a1f81-124">**Bibliothèque :** Inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a1f81-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="a1f81-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f81-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f81-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1f81-126">See also</span></span>

- [<span data-ttu-id="a1f81-127">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="a1f81-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="a1f81-128">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="a1f81-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="a1f81-129">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="a1f81-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
