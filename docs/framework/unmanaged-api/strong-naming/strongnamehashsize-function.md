---
title: StrongNameHashSize, fonction
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
ms.openlocfilehash: 1116fcde754f966a783f4fdca85df8bd3ca1b0ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724427"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="8f0c3-102">StrongNameHashSize, fonction</span><span class="sxs-lookup"><span data-stu-id="8f0c3-102">StrongNameHashSize Function</span></span>

<span data-ttu-id="8f0c3-103">Obtient la taille de mémoire tampon requise pour un hachage, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="8f0c3-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="8f0c3-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="8f0c3-104">This function has been deprecated.</span></span> <span data-ttu-id="8f0c3-105">Utilisez la méthode [ICLRStrongName :: StrongNameHashSize (](../hosting/iclrstrongname-strongnamehashsize-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="8f0c3-105">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f0c3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f0c3-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f0c3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8f0c3-107">Parameters</span></span>  

 `ulHashAlg`  
 <span data-ttu-id="8f0c3-108">dans Algorithme de hachage utilisé pour calculer la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="8f0c3-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="8f0c3-109">à Taille de la mémoire tampon retournée, en octets.</span><span class="sxs-lookup"><span data-stu-id="8f0c3-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f0c3-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8f0c3-110">Return Value</span></span>  

 <span data-ttu-id="8f0c3-111">`true` en cas de réussite de l’opération ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="8f0c3-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f0c3-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="8f0c3-112">Remarks</span></span>  

 <span data-ttu-id="8f0c3-113">Si la `StrongNameHashSize` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="8f0c3-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f0c3-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8f0c3-114">Requirements</span></span>  

 <span data-ttu-id="8f0c3-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f0c3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f0c3-116">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="8f0c3-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8f0c3-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f0c3-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f0c3-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f0c3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0c3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f0c3-119">See also</span></span>

- [<span data-ttu-id="8f0c3-120">StrongNameHashSize, méthode</span><span class="sxs-lookup"><span data-stu-id="8f0c3-120">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="8f0c3-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="8f0c3-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
