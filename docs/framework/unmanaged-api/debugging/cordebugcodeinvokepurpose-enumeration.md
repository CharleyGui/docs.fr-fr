---
title: CorDebugCodeInvokePurpose, énumération
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: 2e59d02093b9c2e2bda72c45de25975cbbdb7a29
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796013"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="dc412-102">CorDebugCodeInvokePurpose, énumération</span><span class="sxs-lookup"><span data-stu-id="dc412-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="dc412-103">Indique pourquoi une fonction exportée appelle du code managé.</span><span class="sxs-lookup"><span data-stu-id="dc412-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc412-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc412-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="dc412-105">Membres</span><span class="sxs-lookup"><span data-stu-id="dc412-105">Members</span></span>  
  
|<span data-ttu-id="dc412-106">Membre</span><span class="sxs-lookup"><span data-stu-id="dc412-106">Member</span></span>|<span data-ttu-id="dc412-107">Description</span><span class="sxs-lookup"><span data-stu-id="dc412-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="dc412-108">Aucun ou inconnu.</span><span class="sxs-lookup"><span data-stu-id="dc412-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="dc412-109">Le code managé exécute n'importe quel point d'entrée managé, par exemple un p-invoke inverse.</span><span class="sxs-lookup"><span data-stu-id="dc412-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="dc412-110">Aucun objectif plus détaillé n'est indiqué au runtime.</span><span class="sxs-lookup"><span data-stu-id="dc412-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="dc412-111">Le code managé exécute un constructeur statique.</span><span class="sxs-lookup"><span data-stu-id="dc412-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="dc412-112">Le code managé exécute l'implémentation pour une méthode d'interface qui a été appelée.</span><span class="sxs-lookup"><span data-stu-id="dc412-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc412-113">Notes </span><span class="sxs-lookup"><span data-stu-id="dc412-113">Remarks</span></span>  
 <span data-ttu-id="dc412-114">Cette énumération est utilisée par la méthode [ICorDebugProcess6 :: getexportstepinfo,](icordebugprocess6-getexportstepinfo-method.md) pour fournir des informations sur l’exécution pas à pas du code managé.</span><span class="sxs-lookup"><span data-stu-id="dc412-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc412-115">Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.</span><span class="sxs-lookup"><span data-stu-id="dc412-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc412-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc412-116">Requirements</span></span>  
 <span data-ttu-id="dc412-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc412-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc412-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc412-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc412-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc412-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc412-120">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc412-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc412-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc412-121">See also</span></span>

- [<span data-ttu-id="dc412-122">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="dc412-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="dc412-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="dc412-123">Debugging</span></span>](index.md)
