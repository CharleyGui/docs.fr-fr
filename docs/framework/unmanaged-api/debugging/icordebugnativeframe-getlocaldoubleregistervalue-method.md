---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
ms.openlocfilehash: 10f06fb04099ef947711bc7c5641e5a7f1fa36b7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695697"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="0a385-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue, méthode</span><span class="sxs-lookup"><span data-stu-id="0a385-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>

<span data-ttu-id="0a385-103">Obtient la valeur d’un argument ou d’une variable locale stockée dans les deux registres spécifiés pour ce frame natif.</span><span class="sxs-lookup"><span data-stu-id="0a385-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a385-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a385-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a385-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a385-105">Parameters</span></span>  

 `highWordReg`  
 <span data-ttu-id="0a385-106">dans Valeur de l’énumération « CorDebugRegister » qui spécifie le registre contenant le mot de poids fort de la valeur.</span><span class="sxs-lookup"><span data-stu-id="0a385-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="0a385-107">dans Valeur de l' `CorDebugRegister` énumération qui spécifie le registre contenant le mot de poids faible de la valeur.</span><span class="sxs-lookup"><span data-stu-id="0a385-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="0a385-108">dans Entier qui spécifie la taille de la signature de métadonnées binaires référencée par le `pvSigBlob` paramètre.</span><span class="sxs-lookup"><span data-stu-id="0a385-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0a385-109">dans `PCCOR_SIGNATURE` Valeur qui pointe vers la signature de métadonnées binaires du type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="0a385-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0a385-110">à Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans les registres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0a385-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a385-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="0a385-111">Remarks</span></span>  

 <span data-ttu-id="0a385-112">La `GetLocalDoubleRegisterValue` méthode peut être utilisée dans un frame natif ou dans un frame compilé juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="0a385-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a385-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0a385-113">Requirements</span></span>  

 <span data-ttu-id="0a385-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a385-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a385-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a385-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a385-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a385-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a385-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a385-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a385-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a385-118">See also</span></span>
