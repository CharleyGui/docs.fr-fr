---
title: ICorDebugVariableHome, interface
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: c347346c9157fea843527c662e26ffcfba22ace4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790955"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="e93ea-102">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="e93ea-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="e93ea-103">Représente une variable locale ou un argument d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="e93ea-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e93ea-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e93ea-104">Methods</span></span>  
  
|<span data-ttu-id="e93ea-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e93ea-105">Method</span></span>|<span data-ttu-id="e93ea-106">Description</span><span class="sxs-lookup"><span data-stu-id="e93ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e93ea-107">GetArgumentIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="e93ea-107">GetArgumentIndex Method</span></span>](icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="e93ea-108">Obtient l’index d’un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="e93ea-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="e93ea-109">GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="e93ea-109">GetCode Method</span></span>](icordebugvariablehome-getcode-method.md)|<span data-ttu-id="e93ea-110">Obtient l’instance « ICorDebugCode » qui contient cet objet `ICorDebugVariableHome`.</span><span class="sxs-lookup"><span data-stu-id="e93ea-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="e93ea-111">GetLiveRange, méthode</span><span class="sxs-lookup"><span data-stu-id="e93ea-111">GetLiveRange Method</span></span>](icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="e93ea-112">Obtient la plage native sur laquelle cette variable est active.</span><span class="sxs-lookup"><span data-stu-id="e93ea-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="e93ea-113">GetLocationType, méthode</span><span class="sxs-lookup"><span data-stu-id="e93ea-113">GetLocationType Method</span></span>](icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="e93ea-114">Obtient le type de l’emplacement natif de la variable.</span><span class="sxs-lookup"><span data-stu-id="e93ea-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="e93ea-115">GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="e93ea-115">GetOffset Method</span></span>](icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="e93ea-116">Obtient le décalage à partir du registre de base pour une variable.</span><span class="sxs-lookup"><span data-stu-id="e93ea-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="e93ea-117">GetRegister, méthode</span><span class="sxs-lookup"><span data-stu-id="e93ea-117">GetRegister Method</span></span>](icordebugvariablehome-getregister-method.md)|<span data-ttu-id="e93ea-118">Obtient le Registre qui contient une variable avec un type d’emplacement `VLT_REGISTER`et le registre de base pour une variable avec un type d’emplacement de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="e93ea-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="e93ea-119">GetSlotIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="e93ea-119">GetSlotIndex Method</span></span>](icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="e93ea-120">Obtient l’index d’emplacement managé d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="e93ea-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e93ea-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="e93ea-121">Example</span></span>  
 <span data-ttu-id="e93ea-122">Le fragment de code suivant utilise l’objet [ICorDebugCode4](icordebugcode4-interface.md) nommé `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="e93ea-122">The following code fragment uses the [ICorDebugCode4](icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="e93ea-123">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e93ea-123">Requirements</span></span>  
 <span data-ttu-id="e93ea-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e93ea-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e93ea-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e93ea-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e93ea-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e93ea-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e93ea-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e93ea-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93ea-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e93ea-128">See also</span></span>

- [<span data-ttu-id="e93ea-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e93ea-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e93ea-130">ICorDebugVariableHomeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e93ea-130">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
