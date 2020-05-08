---
title: ICorDebugClass::GetStaticFieldValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: d4a254853256e1a1440f5588418b94e39eabcc9a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894112"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="811c2-102">ICorDebugClass::GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="811c2-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="811c2-103">Obtient la valeur du champ statique spécifié.</span><span class="sxs-lookup"><span data-stu-id="811c2-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="811c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="811c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="811c2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="811c2-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="811c2-106">dans Jeton de `Def` champ qui référence le champ à récupérer.</span><span class="sxs-lookup"><span data-stu-id="811c2-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="811c2-107">dans Pointeur vers un objet ICorDebugFrame qui représente le frame à utiliser pour lever l’ambiguïté entre les threads, le contexte ou les statiques de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="811c2-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="811c2-108">Si le champ statique est relatif à un thread, à un contexte ou à un domaine d’application, le frame détermine la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="811c2-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="811c2-109">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur du champ statique.</span><span class="sxs-lookup"><span data-stu-id="811c2-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="811c2-110">Notes </span><span class="sxs-lookup"><span data-stu-id="811c2-110">Remarks</span></span>  
 <span data-ttu-id="811c2-111">Pour les types paramétrables, la valeur d’un champ statique est relative à l’instanciation particulière.</span><span class="sxs-lookup"><span data-stu-id="811c2-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="811c2-112">Par conséquent, si le constructeur de classe accepte des <xref:System.Type>paramètres de type, appelez [ICorDebugType :: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) au lieu de `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="811c2-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="811c2-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="811c2-113">Requirements</span></span>  
 <span data-ttu-id="811c2-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="811c2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="811c2-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="811c2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="811c2-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="811c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="811c2-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="811c2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
