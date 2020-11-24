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
ms.openlocfilehash: c727d4524bc40ab90eee90faf16788140a73ad9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677659"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="e74aa-102">Méthode ICLRStrongName::StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="e74aa-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>

<span data-ttu-id="e74aa-103">Obtient un jeton qui représente une clé publique.</span><span class="sxs-lookup"><span data-stu-id="e74aa-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="e74aa-104">Un jeton de nom fort est la forme raccourcie d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="e74aa-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e74aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e74aa-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e74aa-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e74aa-106">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="e74aa-107">dans Structure de type [publicKeyBlob](../strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="e74aa-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="e74aa-108">dans Taille, en octets, de `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="e74aa-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="e74aa-109">à Jeton de nom fort correspondant à la clé passée `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="e74aa-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="e74aa-110">Le common language runtime alloue la mémoire dans laquelle le jeton doit être retourné.</span><span class="sxs-lookup"><span data-stu-id="e74aa-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="e74aa-111">L’appelant doit libérer cette mémoire à l’aide de la méthode [ICLRStrongName :: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e74aa-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="e74aa-112">à Taille, en octets, du jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="e74aa-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e74aa-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e74aa-113">Return Value</span></span>  

 <span data-ttu-id="e74aa-114">`S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="e74aa-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e74aa-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="e74aa-115">Remarks</span></span>  

 <span data-ttu-id="e74aa-116">Un jeton de nom fort est la forme raccourcie d’une clé publique qui est utilisée pour économiser de l’espace lors du stockage des informations de clé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e74aa-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="e74aa-117">Plus précisément, les jetons de nom fort sont utilisés dans les références d’assembly pour faire référence à l’assembly dépendant.</span><span class="sxs-lookup"><span data-stu-id="e74aa-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e74aa-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e74aa-118">Requirements</span></span>  

 <span data-ttu-id="e74aa-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e74aa-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e74aa-120">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="e74aa-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e74aa-121">**Bibliothèque :** Inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e74aa-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="e74aa-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e74aa-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74aa-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e74aa-123">See also</span></span>

- [<span data-ttu-id="e74aa-124">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="e74aa-124">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="e74aa-125">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="e74aa-125">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="e74aa-126">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="e74aa-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
