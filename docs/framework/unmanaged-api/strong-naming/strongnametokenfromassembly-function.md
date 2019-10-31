---
title: StrongNameTokenFromAssembly, fonction
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
ms.openlocfilehash: 6b9eca3f2f0267870866874ea27dc65812795f41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121129"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="ab349-102">StrongNameTokenFromAssembly, fonction</span><span class="sxs-lookup"><span data-stu-id="ab349-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="ab349-103">Crée un jeton de nom fort à partir du fichier d’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="ab349-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="ab349-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="ab349-104">This function has been deprecated.</span></span> <span data-ttu-id="ab349-105">Utilisez la méthode [ICLRStrongName :: StrongNameTokenFromAssembly (](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="ab349-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab349-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab349-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab349-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab349-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ab349-108">dans Chemin d’accès au fichier exécutable portable (PE) pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ab349-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="ab349-109">à Jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="ab349-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="ab349-110">à Taille, en octets, du jeton de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ab349-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab349-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ab349-111">Return Value</span></span>  
 <span data-ttu-id="ab349-112">`true` en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ab349-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab349-113">Notes</span><span class="sxs-lookup"><span data-stu-id="ab349-113">Remarks</span></span>  
 <span data-ttu-id="ab349-114">Un jeton de nom fort est la forme raccourcie d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="ab349-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="ab349-115">Le jeton est un hachage 64 bits qui est créé à partir de la clé publique utilisée pour signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ab349-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="ab349-116">Le jeton fait partie du nom fort de l’assembly et peut être lu à partir des métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ab349-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="ab349-117">Une fois le jeton créé, vous devez appeler la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="ab349-117">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="ab349-118">Si la fonction `StrongNameTokenFromAssembly` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="ab349-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab349-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="ab349-119">Requirements</span></span>  
 <span data-ttu-id="ab349-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab349-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab349-121">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ab349-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ab349-122">**Bibliothèque :** Inclus en tant que ressource dans Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ab349-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ab349-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab349-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab349-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab349-124">See also</span></span>

- [<span data-ttu-id="ab349-125">StrongNameTokenFromAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="ab349-125">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="ab349-126">StrongNameTokenFromAssemblyEx, méthode</span><span class="sxs-lookup"><span data-stu-id="ab349-126">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="ab349-127">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ab349-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
