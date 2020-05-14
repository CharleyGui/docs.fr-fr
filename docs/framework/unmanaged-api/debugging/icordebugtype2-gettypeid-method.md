---
title: 'Méthode icordebugtype2 :: GetTypeID, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 1c11946bc5ea69a090091c014aba859935b48b36
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396676"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="f683b-102">Méthode icordebugtype2 :: GetTypeID, méthode</span><span class="sxs-lookup"><span data-stu-id="f683b-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="f683b-103">Obtient une [COR_TYPEID](cor-typeid-structure.md) pour ce type.</span><span class="sxs-lookup"><span data-stu-id="f683b-103">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f683b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f683b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f683b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f683b-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="f683b-106">à Pointeur vers le [COR_TYPEID](cor-typeid-structure.md) pour ce ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="f683b-106">[out] A pointer to the [COR_TYPEID](cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f683b-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f683b-107">Return Value</span></span>  
 <span data-ttu-id="f683b-108">La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="f683b-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="f683b-109">Les `HRESULT` codes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f683b-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="f683b-110">Code de retour</span><span class="sxs-lookup"><span data-stu-id="f683b-110">Return code</span></span>|<span data-ttu-id="f683b-111">Description</span><span class="sxs-lookup"><span data-stu-id="f683b-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="f683b-112">La méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="f683b-112">Method succeeded.</span></span> <span data-ttu-id="f683b-113">La méthode a récupéré une [COR_TYPEID](cor-typeid-structure.md)valide.</span><span class="sxs-lookup"><span data-stu-id="f683b-113">The method has retrieved a valid [COR_TYPEID](cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="f683b-114">Le type n’a pas été chargé.</span><span class="sxs-lookup"><span data-stu-id="f683b-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="f683b-115">Le type n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f683b-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f683b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="f683b-116">Remarks</span></span>  
 <span data-ttu-id="f683b-117">Cette méthode fournit un mappage à partir de ICorDebugType, qui représente un type qui peut ou non avoir été chargé dans le runtime, à un [COR_TYPEID](cor-typeid-structure.md), qui sert de handle opaque qui identifie un type chargé dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="f683b-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="f683b-118">Lorsque le type représenté par l’ICorDebugType n’a pas encore été chargé, cette méthode retourne `CORDBG_E_CLASS_NOT_LOADED` .</span><span class="sxs-lookup"><span data-stu-id="f683b-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="f683b-119">Si le type n’est pas pris en charge, il retourne `CORDBG_E_UNSUPPORTED` .</span><span class="sxs-lookup"><span data-stu-id="f683b-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f683b-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f683b-120">Requirements</span></span>  
 <span data-ttu-id="f683b-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f683b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f683b-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f683b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f683b-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f683b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f683b-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f683b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f683b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f683b-125">See also</span></span>

- [<span data-ttu-id="f683b-126">ICorDebugType2, interface</span><span class="sxs-lookup"><span data-stu-id="f683b-126">ICorDebugType2 Interface</span></span>](icordebugtype2-interface.md)
