---
title: Méthode ICLRStrongName::StrongNameFreeBuffer
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 7aed3e6877bfcd83754d462cdba81ccc229d002f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504002"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="39733-102">Méthode ICLRStrongName::StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="39733-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="39733-103">Libère de la mémoire qui a été allouée avec un appel précédent à une méthode de nom fort telle que [ICLRStrongName :: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName :: StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)ou [ICLRStrongName :: StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="39733-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39733-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39733-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39733-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="39733-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="39733-106">dans Pointeur vers la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="39733-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39733-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="39733-107">Return Value</span></span>  
 <span data-ttu-id="39733-108">`S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="39733-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39733-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="39733-109">Requirements</span></span>  
 <span data-ttu-id="39733-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39733-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39733-111">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="39733-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="39733-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="39733-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39733-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39733-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39733-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39733-114">See also</span></span>

- [<span data-ttu-id="39733-115">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="39733-115">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
