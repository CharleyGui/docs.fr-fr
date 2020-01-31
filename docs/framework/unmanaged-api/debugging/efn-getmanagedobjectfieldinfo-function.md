---
title: _EFN_GetManagedObjectFieldInfo, fonction
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: 182424632e4f81dfdf86e87dc6bb2c75c2780fce
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793770"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="8a91c-102">\_EFN\_GetManagedObjectFieldInfo Function</span><span class="sxs-lookup"><span data-stu-id="8a91c-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="8a91c-103">Obtient l'offset du début d'un objet jusqu'à un champ, ainsi que la valeur du champ, à l'aide du pointeur d'objet et du nom de champ fournis.</span><span class="sxs-lookup"><span data-stu-id="8a91c-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a91c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a91c-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a91c-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="8a91c-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="8a91c-106">dans Pointeur vers le client de débogage.</span><span class="sxs-lookup"><span data-stu-id="8a91c-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="8a91c-107">dans Pointeur d’objet managé.</span><span class="sxs-lookup"><span data-stu-id="8a91c-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="8a91c-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="8a91c-108">szFieldName</span></span>  
 <span data-ttu-id="8a91c-109">dans Pointeur d’objet managé vers le nom de champ.</span><span class="sxs-lookup"><span data-stu-id="8a91c-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8a91c-110">à Valeur de champ.</span><span class="sxs-lookup"><span data-stu-id="8a91c-110">[out] The field value.</span></span> <span data-ttu-id="8a91c-111">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="8a91c-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="8a91c-112">à Offset de `objAddr` au champ.</span><span class="sxs-lookup"><span data-stu-id="8a91c-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="8a91c-113">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="8a91c-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a91c-114">Notes</span><span class="sxs-lookup"><span data-stu-id="8a91c-114">Remarks</span></span>  
 <span data-ttu-id="8a91c-115">Si le décalage est égal à 0, aucun décalage n’est écrit.</span><span class="sxs-lookup"><span data-stu-id="8a91c-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="8a91c-116">S’il n’existe aucun code managé sur le thread actuellement en contexte, la fonction retourne HRESULT SOS_E_NOMANAGEDCODE avec une valeur d’installation de 0xa0 et un code d’erreur 0x1000.</span><span class="sxs-lookup"><span data-stu-id="8a91c-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a91c-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="8a91c-117">Requirements</span></span>  
 <span data-ttu-id="8a91c-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a91c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a91c-119">**En-tête :** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="8a91c-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="8a91c-120">**Version de .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a91c-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a91c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a91c-121">See also</span></span>

- [<span data-ttu-id="8a91c-122">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="8a91c-122">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
