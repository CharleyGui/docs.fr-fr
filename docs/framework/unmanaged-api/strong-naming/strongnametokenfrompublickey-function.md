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
ms.openlocfilehash: 89556cf0e1ef65c35278a526e10fc791063ea2c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708346"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="00bac-102">StrongNameTokenFromPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="00bac-102">StrongNameTokenFromPublicKey Function</span></span>

<span data-ttu-id="00bac-103">Obtient un jeton représentant une clé publique.</span><span class="sxs-lookup"><span data-stu-id="00bac-103">Gets a token representing a public key.</span></span> <span data-ttu-id="00bac-104">Un jeton de nom fort est la forme raccourcie d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="00bac-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="00bac-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="00bac-105">This function has been deprecated.</span></span> <span data-ttu-id="00bac-106">Utilisez la méthode [ICLRStrongName :: StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="00bac-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00bac-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00bac-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00bac-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00bac-108">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="00bac-109">dans Structure de type [publicKeyBlob](publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="00bac-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="00bac-110">dans Taille, en octets, de `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="00bac-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="00bac-111">à Jeton de nom fort correspondant à la clé passée `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="00bac-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="00bac-112">Le common language runtime alloue la mémoire dans laquelle le jeton doit être retourné.</span><span class="sxs-lookup"><span data-stu-id="00bac-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="00bac-113">L’appelant doit libérer cette mémoire à l’aide de la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="00bac-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="00bac-114">à Taille, en octets, du jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="00bac-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00bac-115">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="00bac-115">Return Value</span></span>  

 <span data-ttu-id="00bac-116">`true` en cas de réussite de l’opération ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="00bac-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00bac-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="00bac-117">Remarks</span></span>  

 <span data-ttu-id="00bac-118">Un jeton de nom fort est la forme raccourcie d’une clé publique utilisée pour économiser de l’espace lors du stockage des informations de clé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="00bac-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="00bac-119">Plus précisément, les jetons de nom fort sont utilisés dans les références d’assembly pour faire référence à l’assembly dépendant.</span><span class="sxs-lookup"><span data-stu-id="00bac-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="00bac-120">Si la `StrongNameTokenFromPublicKey` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="00bac-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00bac-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00bac-121">Requirements</span></span>  

 <span data-ttu-id="00bac-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00bac-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00bac-123">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="00bac-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="00bac-124">**Bibliothèque :** Inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="00bac-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="00bac-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00bac-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00bac-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00bac-126">See also</span></span>

- [<span data-ttu-id="00bac-127">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="00bac-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="00bac-128">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="00bac-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="00bac-129">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="00bac-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
