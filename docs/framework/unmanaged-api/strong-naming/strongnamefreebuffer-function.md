---
title: StrongNameFreeBuffer, fonction
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: d93bda046a79dbdec2195eee48fefc1e5538b2e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732253"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="951d8-102">StrongNameFreeBuffer, fonction</span><span class="sxs-lookup"><span data-stu-id="951d8-102">StrongNameFreeBuffer Function</span></span>

<span data-ttu-id="951d8-103">Libère la mémoire qui a été alloué avec un appel précédent à une fonction de nom fort comme [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) ou [StrongNameSignatureGeneration ](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="951d8-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="951d8-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="951d8-104">This function has been deprecated.</span></span> <span data-ttu-id="951d8-105">Utilisez la méthode [ICLRStrongName :: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="951d8-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="951d8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="951d8-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="951d8-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="951d8-107">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="951d8-108">dans Pointeur vers la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="951d8-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="951d8-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="951d8-109">Requirements</span></span>  

 <span data-ttu-id="951d8-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="951d8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="951d8-111">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="951d8-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="951d8-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="951d8-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="951d8-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="951d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951d8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="951d8-114">See also</span></span>

- [<span data-ttu-id="951d8-115">StrongNameFreeBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="951d8-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="951d8-116">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="951d8-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
