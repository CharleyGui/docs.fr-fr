---
title: COR_ACTIVE_FUNCTION, structure
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: c50ba530d78296ebb956329b2f34b4f1e5cae94c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727417"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="98505-102">COR_ACTIVE_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="98505-102">COR_ACTIVE_FUNCTION Structure</span></span>

<span data-ttu-id="98505-103">Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread.</span><span class="sxs-lookup"><span data-stu-id="98505-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="98505-104">Cette structure est utilisée par la méthode [ICorDebugThread2 :: GetActiveFunctions,](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="98505-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98505-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98505-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="98505-106">Membres</span><span class="sxs-lookup"><span data-stu-id="98505-106">Members</span></span>  
  
|<span data-ttu-id="98505-107">Membre</span><span class="sxs-lookup"><span data-stu-id="98505-107">Member</span></span>|<span data-ttu-id="98505-108">Description</span><span class="sxs-lookup"><span data-stu-id="98505-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="98505-109">Pointeur vers le propriétaire du domaine d’application du `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="98505-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="98505-110">Pointeur désignant le propriétaire du module du `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="98505-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="98505-111">Pointeur désignant le propriétaire de la fonction du `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="98505-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="98505-112">Décalage MSIL (Microsoft Intermediate Language) du frame.</span><span class="sxs-lookup"><span data-stu-id="98505-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="98505-113">Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="98505-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98505-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="98505-114">Requirements</span></span>  

 <span data-ttu-id="98505-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98505-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98505-116">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="98505-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="98505-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98505-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98505-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98505-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98505-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98505-119">See also</span></span>

- [<span data-ttu-id="98505-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="98505-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="98505-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="98505-121">Debugging</span></span>](index.md)
