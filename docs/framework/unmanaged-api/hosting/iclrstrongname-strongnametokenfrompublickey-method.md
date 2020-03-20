---
title: Méthode ICLRStrongName::StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: 919c1321f18ca163481d27fa204c78f38af1e456
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176316"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="a39ca-102">Méthode ICLRStrongName::StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="a39ca-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="a39ca-103">Obtient un jeton qui représente une clé publique.</span><span class="sxs-lookup"><span data-stu-id="a39ca-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="a39ca-104">Un jeton de nom fort est la forme raccourcie d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="a39ca-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39ca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a39ca-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a39ca-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a39ca-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="a39ca-107">[dans] Une structure de type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="a39ca-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="a39ca-108">[dans] La taille, dans les `pbPublicKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="a39ca-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="a39ca-109">[out] Le jeton de nom fort `pbPublicKeyBlob`correspondant à la clé passée dedans .</span><span class="sxs-lookup"><span data-stu-id="a39ca-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="a39ca-110">Le runtime de langue commune alloue la mémoire dans laquelle retourner le jeton.</span><span class="sxs-lookup"><span data-stu-id="a39ca-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="a39ca-111">L’appelant doit libérer cette mémoire en utilisant la méthode [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="a39ca-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="a39ca-112">[out] La taille, dans les octets, du jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="a39ca-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a39ca-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a39ca-113">Return Value</span></span>  
 <span data-ttu-id="a39ca-114">`S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="a39ca-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a39ca-115">Notes </span><span class="sxs-lookup"><span data-stu-id="a39ca-115">Remarks</span></span>  
 <span data-ttu-id="a39ca-116">Un jeton de nom fort est la forme raccourcie d’une clé publique qui est utilisée pour économiser de l’espace lors du stockage des informations clés dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a39ca-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="a39ca-117">Plus précisément, des jetons de nom forts sont utilisés dans les références d’assemblage pour désigner l’assemblage dépendant.</span><span class="sxs-lookup"><span data-stu-id="a39ca-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a39ca-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a39ca-118">Requirements</span></span>  
 <span data-ttu-id="a39ca-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a39ca-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a39ca-120">**En-tête:** MetaHost.h MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a39ca-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a39ca-121">**Bibliothèque:** Inclus comme une ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a39ca-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="a39ca-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a39ca-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39ca-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a39ca-123">See also</span></span>

- [<span data-ttu-id="a39ca-124">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="a39ca-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="a39ca-125">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="a39ca-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="a39ca-126">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a39ca-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
