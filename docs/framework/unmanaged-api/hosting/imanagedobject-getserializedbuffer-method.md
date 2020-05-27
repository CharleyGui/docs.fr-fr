---
title: IManagedObject::GetSerializedBuffer, méthode
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: c68ec0b41bb38afc7cefaf47df718fffcf42d250
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842427"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="ad1ac-102">IManagedObject::GetSerializedBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="ad1ac-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="ad1ac-103">Obtient la représentation sous forme de chaîne de cet objet managé.</span><span class="sxs-lookup"><span data-stu-id="ad1ac-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad1ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad1ac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad1ac-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="ad1ac-106">à Pointeur vers une chaîne qui est l’objet sérialisé.</span><span class="sxs-lookup"><span data-stu-id="ad1ac-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad1ac-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ad1ac-107">Remarks</span></span>  
 <span data-ttu-id="ad1ac-108">La `GetSerializedBuffer` méthode sérialise l’objet afin qu’il puisse être marshalé vers le client.</span><span class="sxs-lookup"><span data-stu-id="ad1ac-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad1ac-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ad1ac-109">Requirements</span></span>  
 <span data-ttu-id="ad1ac-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad1ac-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad1ac-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ad1ac-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad1ac-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ad1ac-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad1ac-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1ac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1ac-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad1ac-114">See also</span></span>

- [<span data-ttu-id="ad1ac-115">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="ad1ac-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
