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
ms.openlocfilehash: 11821acbeeb04ae09464eb0e032b9bf387914168
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095047"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="35f78-102">StrongNameFreeBuffer, fonction</span><span class="sxs-lookup"><span data-stu-id="35f78-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="35f78-103">Libère la mémoire qui a été alloué avec un appel précédent à une fonction de nom fort comme [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) ou [StrongNameSignatureGeneration ](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="35f78-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="35f78-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="35f78-104">This function has been deprecated.</span></span> <span data-ttu-id="35f78-105">Utilisez la méthode [ICLRStrongName :: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="35f78-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35f78-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35f78-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35f78-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35f78-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="35f78-108">dans Pointeur vers la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="35f78-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35f78-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="35f78-109">Requirements</span></span>  
 <span data-ttu-id="35f78-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35f78-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35f78-111">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="35f78-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="35f78-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="35f78-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="35f78-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35f78-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f78-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35f78-114">See also</span></span>

- [<span data-ttu-id="35f78-115">StrongNameFreeBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="35f78-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="35f78-116">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="35f78-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
