---
title: ICorDebugProcess6::GetCode, méthode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: cee1556fd7d803765b09a7cbd86ce2ff7be91cc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732630"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="7cead-102">ICorDebugProcess6::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="7cead-102">ICorDebugProcess6::GetCode Method</span></span>

<span data-ttu-id="7cead-103">Obtient des informations sur le code managé à une adresse de code particulière.</span><span class="sxs-lookup"><span data-stu-id="7cead-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cead-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cead-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cead-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7cead-105">Parameters</span></span>  

 `codeAddress`  
 <span data-ttu-id="7cead-106">dans Valeur [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) qui spécifie l’adresse de départ du segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="7cead-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="7cead-107">à Pointeur vers l’adresse d’un objet « ICorDebugCode » qui représente un segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="7cead-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cead-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="7cead-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cead-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7cead-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cead-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7cead-110">Requirements</span></span>  

 <span data-ttu-id="7cead-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cead-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cead-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cead-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cead-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cead-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cead-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cead-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cead-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cead-115">See also</span></span>

- [<span data-ttu-id="7cead-116">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="7cead-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="7cead-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7cead-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
