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
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175055"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="821ba-102">StrongNameTokenFromPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="821ba-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="821ba-103">Obtient un jeton représentant une clé publique.</span><span class="sxs-lookup"><span data-stu-id="821ba-103">Gets a token representing a public key.</span></span> <span data-ttu-id="821ba-104">Un jeton de nom fort est la forme raccourcie d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="821ba-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="821ba-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="821ba-105">This function has been deprecated.</span></span> <span data-ttu-id="821ba-106">Utilisez la méthode [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="821ba-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="821ba-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="821ba-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="821ba-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="821ba-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="821ba-109">[dans] Une structure de type [PublicKeyBlob](publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="821ba-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="821ba-110">[dans] La taille, dans les `pbPublicKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="821ba-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="821ba-111">[out] Le jeton de nom fort `pbPublicKeyBlob`correspondant à la clé passée dedans .</span><span class="sxs-lookup"><span data-stu-id="821ba-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="821ba-112">Le runtime de langue commune alloue la mémoire dans laquelle retourner le jeton.</span><span class="sxs-lookup"><span data-stu-id="821ba-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="821ba-113">L’appelant doit libérer cette mémoire en utilisant la fonction [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="821ba-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="821ba-114">[out] La taille, dans les octets, du jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="821ba-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="821ba-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="821ba-115">Return Value</span></span>  
 <span data-ttu-id="821ba-116">`true`à la réussite; autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="821ba-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="821ba-117">Notes </span><span class="sxs-lookup"><span data-stu-id="821ba-117">Remarks</span></span>  
 <span data-ttu-id="821ba-118">Un jeton de nom fort est la forme raccourcie d’une clé publique utilisée pour économiser de l’espace lors du stockage des informations clés dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="821ba-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="821ba-119">Plus précisément, des jetons de nom forts sont utilisés dans les références d’assemblage pour désigner l’assemblage dépendant.</span><span class="sxs-lookup"><span data-stu-id="821ba-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="821ba-120">Si `StrongNameTokenFromPublicKey` la fonction ne se termine pas avec succès, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="821ba-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="821ba-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="821ba-121">Requirements</span></span>  
 <span data-ttu-id="821ba-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="821ba-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="821ba-123">**En-tête:** StrongName.h (en)</span><span class="sxs-lookup"><span data-stu-id="821ba-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="821ba-124">**Bibliothèque:** Inclus comme une ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="821ba-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="821ba-125">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="821ba-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821ba-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="821ba-126">See also</span></span>

- [<span data-ttu-id="821ba-127">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="821ba-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="821ba-128">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="821ba-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="821ba-129">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="821ba-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
