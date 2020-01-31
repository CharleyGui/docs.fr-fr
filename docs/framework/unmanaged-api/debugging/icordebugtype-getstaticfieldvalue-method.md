---
title: ICorDebugType::GetStaticFieldValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 37bf5abf66b613d8432af84c7d73aff60e9127cb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791275"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="7743b-102">ICorDebugType::GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="7743b-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="7743b-103">Obtient un pointeur d’interface vers un objet ICorDebugValue qui contient la valeur du champ statique référencé par le jeton de champ spécifié dans le frame de pile spécifié.</span><span class="sxs-lookup"><span data-stu-id="7743b-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7743b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7743b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7743b-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="7743b-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="7743b-106">dans Jeton `mdFieldDef` qui spécifie le champ statique.</span><span class="sxs-lookup"><span data-stu-id="7743b-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="7743b-107">dans Pointeur vers un ICorDebugFrame qui représente le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="7743b-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="7743b-108">à Pointeur vers l’adresse d’un `ICorDebugValue` qui contient la valeur du champ statique.</span><span class="sxs-lookup"><span data-stu-id="7743b-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7743b-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7743b-109">Remarks</span></span>  
 <span data-ttu-id="7743b-110">La méthode `GetStaticFieldValue` peut être utilisée uniquement si le type est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, comme indiqué par la méthode [ICorDebugType :: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7743b-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="7743b-111">Pour les types non génériques, l’opération effectuée par `GetStaticFieldValue` est identique à l’appel de [ICorDebugClass :: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) sur l’objet ICorDebugClass retourné par [ICorDebugType :: GetClass](icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="7743b-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="7743b-112">Pour les types génériques, une valeur de champ statique sera relative à une instanciation particulière.</span><span class="sxs-lookup"><span data-stu-id="7743b-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="7743b-113">En outre, si le champ statique peut être relatif à un thread, à un contexte ou à un domaine d’application, le frame de pile aide le débogueur à déterminer la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="7743b-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7743b-114">Notes</span><span class="sxs-lookup"><span data-stu-id="7743b-114">Remarks</span></span>  
 <span data-ttu-id="7743b-115">`GetStaticFieldValue` peut être utilisé uniquement quand un appel à `ICorDebugType::GetType` retourne la valeur ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="7743b-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7743b-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7743b-116">Requirements</span></span>  
 <span data-ttu-id="7743b-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7743b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7743b-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7743b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7743b-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7743b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7743b-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7743b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
