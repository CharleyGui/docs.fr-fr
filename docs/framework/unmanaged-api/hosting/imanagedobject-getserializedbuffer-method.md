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
ms.openlocfilehash: 4a55ae265230c4da3cc0a19b06a7597be8661beb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103248"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="d7891-102">IManagedObject::GetSerializedBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="d7891-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="d7891-103">Obtient la représentation sous forme de chaîne de cet objet managé.</span><span class="sxs-lookup"><span data-stu-id="d7891-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7891-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7891-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7891-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7891-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="d7891-106">à Pointeur vers une chaîne qui est l’objet sérialisé.</span><span class="sxs-lookup"><span data-stu-id="d7891-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7891-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d7891-107">Remarks</span></span>  
 <span data-ttu-id="d7891-108">La méthode `GetSerializedBuffer` sérialise l’objet afin qu’il puisse être marshalé vers le client.</span><span class="sxs-lookup"><span data-stu-id="d7891-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7891-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="d7891-109">Requirements</span></span>  
 <span data-ttu-id="d7891-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7891-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7891-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d7891-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7891-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d7891-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7891-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7891-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7891-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7891-114">See also</span></span>

- [<span data-ttu-id="d7891-115">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="d7891-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
