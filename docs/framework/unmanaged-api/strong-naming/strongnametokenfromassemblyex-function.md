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
ms.openlocfilehash: 566bba09f6bfac2f7616dc5caf32ef431f2e1e67
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719799"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="40057-102">StrongNameTokenFromAssemblyEx, fonction</span><span class="sxs-lookup"><span data-stu-id="40057-102">StrongNameTokenFromAssemblyEx Function</span></span>

<span data-ttu-id="40057-103">Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique que le jeton représente.</span><span class="sxs-lookup"><span data-stu-id="40057-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="40057-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="40057-104">This function has been deprecated.</span></span> <span data-ttu-id="40057-105">Utilisez la méthode [ICLRStrongName :: StrongNameTokenFromAssemblyEx (](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="40057-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40057-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40057-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40057-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="40057-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="40057-108">dans Chemin d’accès au fichier exécutable portable (PE) pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="40057-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="40057-109">à Jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="40057-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="40057-110">à Taille, en octets, du jeton de nom fort.</span><span class="sxs-lookup"><span data-stu-id="40057-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="40057-111">à Clé publique retournée.</span><span class="sxs-lookup"><span data-stu-id="40057-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="40057-112">à Taille, en octets, de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="40057-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40057-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="40057-113">Return Value</span></span>  

 <span data-ttu-id="40057-114">`true` en cas de réussite de l’opération ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="40057-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40057-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="40057-115">Remarks</span></span>  

 <span data-ttu-id="40057-116">Un jeton de nom fort est la forme raccourcie d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="40057-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="40057-117">Le jeton est un hachage 64 bits qui est créé à partir de la clé publique utilisée pour signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="40057-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="40057-118">Le jeton fait partie du nom fort de l’assembly et peut être lu à partir des métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="40057-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="40057-119">Une fois la clé récupérée et le jeton créé, vous devez appeler la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="40057-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="40057-120">Si la `StrongNameTokenFromAssemblyEx` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="40057-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40057-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="40057-121">Requirements</span></span>  

 <span data-ttu-id="40057-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40057-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40057-123">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="40057-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="40057-124">**Bibliothèque :** Inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="40057-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="40057-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40057-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40057-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40057-126">See also</span></span>

- [<span data-ttu-id="40057-127">StrongNameTokenFromAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="40057-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="40057-128">StrongNameTokenFromAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="40057-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="40057-129">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="40057-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
