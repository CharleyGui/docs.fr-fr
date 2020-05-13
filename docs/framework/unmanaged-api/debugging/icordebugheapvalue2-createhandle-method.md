---
title: ICorDebugHeapValue2::CreateHandle, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: cbc056e9a3cc00178b32dee4011da4403dff508a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212774"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="12145-102">ICorDebugHeapValue2::CreateHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="12145-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="12145-103">Crée un handle du type spécifié pour la valeur de tas représentée par cet objet ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="12145-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12145-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12145-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12145-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12145-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="12145-106">dans Valeur de l’énumération CorDebugHandleType, qui spécifie le type de descripteur à créer.</span><span class="sxs-lookup"><span data-stu-id="12145-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="12145-107">à Pointeur vers l’adresse d’un objet ICorDebugHandleValue qui représente le nouveau handle pour cette valeur de tas.</span><span class="sxs-lookup"><span data-stu-id="12145-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12145-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="12145-108">Remarks</span></span>  
 <span data-ttu-id="12145-109">Le handle sera créé dans le domaine d’application associé à la valeur du tas et deviendra non valide si le domaine d’application est déchargé.</span><span class="sxs-lookup"><span data-stu-id="12145-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="12145-110">Plusieurs appels à cette fonction pour la même valeur de tas créeront plusieurs handles.</span><span class="sxs-lookup"><span data-stu-id="12145-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="12145-111">Étant donné que les handles affectent les performances du garbage collector, le débogueur doit se limiter à un nombre relativement faible de handles (environ 256) qui sont actifs à la fois.</span><span class="sxs-lookup"><span data-stu-id="12145-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12145-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="12145-112">Requirements</span></span>  
 <span data-ttu-id="12145-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12145-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12145-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12145-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12145-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12145-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12145-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12145-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
