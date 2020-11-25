---
title: COR_TYPEID, structure
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
ms.openlocfilehash: 5eeb5aef7edaa23385190a309144e1477da741e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697439"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="3eaed-102">COR_TYPEID, structure</span><span class="sxs-lookup"><span data-stu-id="3eaed-102">COR_TYPEID Structure</span></span>

<span data-ttu-id="3eaed-103">Contient un identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="3eaed-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eaed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eaed-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="3eaed-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3eaed-105">Members</span></span>  
  
|<span data-ttu-id="3eaed-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3eaed-106">Member</span></span>|<span data-ttu-id="3eaed-107">Description</span><span class="sxs-lookup"><span data-stu-id="3eaed-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="3eaed-108">Premier jeton.</span><span class="sxs-lookup"><span data-stu-id="3eaed-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="3eaed-109">Deuxième jeton.</span><span class="sxs-lookup"><span data-stu-id="3eaed-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eaed-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="3eaed-110">Remarks</span></span>  

 <span data-ttu-id="3eaed-111">La `COR_TYPEID` structure est retournée par un certain nombre de méthodes de débogage qui fournissent des informations sur les objets qui doivent être récupérés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="3eaed-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="3eaed-112">Il peut ensuite être passé comme argument à d’autres méthodes de débogage qui fournissent des informations supplémentaires sur cet élément.</span><span class="sxs-lookup"><span data-stu-id="3eaed-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="3eaed-113">Par exemple, en énumérant un objet [icordebugheapenum,](icordebugheapenum-interface.md) , vous pouvez récupérer des objets [COR_HEAPOBJECT](cor-heapobject-structure.md) individuels qui représentent des objets individuels sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="3eaed-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="3eaed-114">Vous pouvez ensuite passer la `COR_TYPEID` valeur du `COR_HEAPOBJECT.type` champ à la méthode [ICorDebugProcess5 :: gettypefortypeid,](icordebugprocess5-gettypefortypeid-method.md) pour récupérer un objet ICorDebugType qui fournit des informations de type sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="3eaed-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="3eaed-115">Un `COR_TYPEID` objet est destiné à être opaque.</span><span class="sxs-lookup"><span data-stu-id="3eaed-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="3eaed-116">Ses champs individuels ne doivent pas être accessibles ou manipulés.</span><span class="sxs-lookup"><span data-stu-id="3eaed-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="3eaed-117">Son unique utilisation est l’identificateur qui est fourni en tant que `out` paramètre dans un appel de méthode et qui peut, à son tour, être passé à d’autres méthodes pour fournir des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3eaed-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eaed-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3eaed-118">Requirements</span></span>  

 <span data-ttu-id="3eaed-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eaed-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eaed-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3eaed-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3eaed-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3eaed-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3eaed-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eaed-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eaed-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eaed-123">See also</span></span>

- [<span data-ttu-id="3eaed-124">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="3eaed-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3eaed-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="3eaed-125">Debugging</span></span>](index.md)
