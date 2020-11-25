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
ms.openlocfilehash: 281b9f46194e93220f47ef8aadbf29ce03084582
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711947"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="a0d40-102">ICorDebugType::GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="a0d40-102">ICorDebugType::GetStaticFieldValue Method</span></span>

<span data-ttu-id="a0d40-103">Obtient un pointeur d’interface vers un objet ICorDebugValue qui contient la valeur du champ statique référencé par le jeton de champ spécifié dans le frame de pile spécifié.</span><span class="sxs-lookup"><span data-stu-id="a0d40-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0d40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0d40-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0d40-105">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="a0d40-106">dans `mdFieldDef` Jeton qui spécifie le champ statique.</span><span class="sxs-lookup"><span data-stu-id="a0d40-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="a0d40-107">dans Pointeur vers un ICorDebugFrame qui représente le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="a0d40-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a0d40-108">à Pointeur vers l’adresse d’un `ICorDebugValue` qui contient la valeur du champ statique.</span><span class="sxs-lookup"><span data-stu-id="a0d40-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0d40-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0d40-109">Remarks</span></span>  

 <span data-ttu-id="a0d40-110">La `GetStaticFieldValue` méthode peut être utilisée uniquement si le type est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, comme indiqué par la méthode [ICorDebugType :: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a0d40-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="a0d40-111">Pour les types non génériques, l’opération effectuée par `GetStaticFieldValue` est identique à l’appel de [ICorDebugClass :: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) sur l’objet ICorDebugClass retourné par [ICorDebugType :: GetClass](icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="a0d40-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="a0d40-112">Pour les types génériques, une valeur de champ statique sera relative à une instanciation particulière.</span><span class="sxs-lookup"><span data-stu-id="a0d40-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="a0d40-113">En outre, si le champ statique peut être relatif à un thread, à un contexte ou à un domaine d’application, le frame de pile aide le débogueur à déterminer la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a0d40-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0d40-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0d40-114">Remarks</span></span>  

 <span data-ttu-id="a0d40-115">`GetStaticFieldValue` peut être utilisé uniquement quand un appel à `ICorDebugType::GetType` retourne une valeur de ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="a0d40-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d40-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a0d40-116">Requirements</span></span>  

 <span data-ttu-id="a0d40-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0d40-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d40-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0d40-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0d40-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0d40-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0d40-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d40-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
