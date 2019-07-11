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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65ac35e254368b53ac2751e84be7dfe052fa0b53
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749086"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="b78b7-102">IManagedObject::GetSerializedBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="b78b7-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="b78b7-103">Obtient la représentation sous forme de chaîne de cet objet managé.</span><span class="sxs-lookup"><span data-stu-id="b78b7-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b78b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b78b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b78b7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b78b7-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="b78b7-106">[out] Un pointeur vers une chaîne qui est l’objet sérialisé.</span><span class="sxs-lookup"><span data-stu-id="b78b7-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b78b7-107">Notes</span><span class="sxs-lookup"><span data-stu-id="b78b7-107">Remarks</span></span>  
 <span data-ttu-id="b78b7-108">Le `GetSerializedBuffer` méthode sérialise l’objet afin qu’elle peut être marshalée au client.</span><span class="sxs-lookup"><span data-stu-id="b78b7-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b78b7-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b78b7-109">Requirements</span></span>  
 <span data-ttu-id="b78b7-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b78b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b78b7-111">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b78b7-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b78b7-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b78b7-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b78b7-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b78b7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b78b7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b78b7-114">See also</span></span>

- [<span data-ttu-id="b78b7-115">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="b78b7-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
