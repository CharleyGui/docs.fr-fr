---
title: ICorDebugILFrame2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 2e0f284625e99215900c6aaab94e4eae611787ed
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212098"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="53982-102">ICorDebugILFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="53982-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="53982-103">Extension logique de l’interface ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="53982-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53982-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="53982-104">Methods</span></span>  
  
|<span data-ttu-id="53982-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="53982-105">Method</span></span>|<span data-ttu-id="53982-106">Description</span><span class="sxs-lookup"><span data-stu-id="53982-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53982-107">EnumerateTypeParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="53982-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="53982-108">Obtient un objet ICorDebugTypeEnum qui contient les <xref:System.Type> paramètres de ce frame.</span><span class="sxs-lookup"><span data-stu-id="53982-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="53982-109">RemapFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="53982-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="53982-110">Remappe une fonction modifiée en spécifiant le nouvel offset MSIL.</span><span class="sxs-lookup"><span data-stu-id="53982-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53982-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="53982-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53982-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="53982-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53982-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="53982-113">Requirements</span></span>  
 <span data-ttu-id="53982-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53982-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53982-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53982-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53982-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53982-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53982-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53982-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53982-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53982-118">See also</span></span>

- [<span data-ttu-id="53982-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="53982-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
