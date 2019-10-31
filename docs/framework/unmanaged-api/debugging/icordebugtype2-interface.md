---
title: ICorDebugType2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 7b56f0f3ba62efb48ac8d79aad4480b5f22771ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110212"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="04a03-102">ICorDebugType2, interface</span><span class="sxs-lookup"><span data-stu-id="04a03-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="04a03-103">Étend l’interface ICorDebugType pour récupérer l’identificateur de type d’un type de base ou un type complexe (défini par l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="04a03-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04a03-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="04a03-104">Methods</span></span>  
  
|<span data-ttu-id="04a03-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="04a03-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="04a03-106">GetTypeID, méthode</span><span class="sxs-lookup"><span data-stu-id="04a03-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="04a03-107">Obtient un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pour ce type.</span><span class="sxs-lookup"><span data-stu-id="04a03-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04a03-108">Notes</span><span class="sxs-lookup"><span data-stu-id="04a03-108">Remarks</span></span>  
 <span data-ttu-id="04a03-109">Cette interface est une extension logique de l’interface ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="04a03-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04a03-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="04a03-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04a03-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="04a03-111">Example</span></span>  
 <span data-ttu-id="04a03-112">Le fragment de code suivant illustre l’utilisation de la méthode [méthode icordebugtype2 :: GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="04a03-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="04a03-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="04a03-113">Requirements</span></span>  
 <span data-ttu-id="04a03-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a03-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a03-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04a03-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04a03-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04a03-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04a03-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a03-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a03-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04a03-118">See also</span></span>

- [<span data-ttu-id="04a03-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="04a03-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
