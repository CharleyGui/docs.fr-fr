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
ms.openlocfilehash: 159ece09ae0b6a67780639da8aae8c0e4b412bb8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730689"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="bfd17-102">IManagedObject::GetSerializedBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="bfd17-102">IManagedObject::GetSerializedBuffer Method</span></span>

<span data-ttu-id="bfd17-103">Obtient la représentation sous forme de chaîne de cet objet managé.</span><span class="sxs-lookup"><span data-stu-id="bfd17-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfd17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfd17-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bfd17-105">Parameters</span></span>  

 `pBSTR`  
 <span data-ttu-id="bfd17-106">à Pointeur vers une chaîne qui est l’objet sérialisé.</span><span class="sxs-lookup"><span data-stu-id="bfd17-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfd17-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="bfd17-107">Remarks</span></span>  

 <span data-ttu-id="bfd17-108">La `GetSerializedBuffer` méthode sérialise l’objet afin qu’il puisse être marshalé vers le client.</span><span class="sxs-lookup"><span data-stu-id="bfd17-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfd17-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bfd17-109">Requirements</span></span>  

 <span data-ttu-id="bfd17-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfd17-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfd17-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bfd17-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfd17-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bfd17-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfd17-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfd17-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd17-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfd17-114">See also</span></span>

- [<span data-ttu-id="bfd17-115">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="bfd17-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
