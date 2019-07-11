---
title: ICorDebugNativeFrame::GetLocalRegisterValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d287305934c7884d5474935e50de3d26e225975
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746162"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="b9fab-102">ICorDebugNativeFrame::GetLocalRegisterValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b9fab-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="b9fab-103">Obtient la valeur d’un argument ou une variable locale qui est stockée dans le Registre spécifié pour ce frame natif.</span><span class="sxs-lookup"><span data-stu-id="b9fab-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9fab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9fab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9fab-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9fab-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="b9fab-106">[in] Une valeur de l’énumération « CorDebugRegister » qui spécifie le Registre contenant la valeur.</span><span class="sxs-lookup"><span data-stu-id="b9fab-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b9fab-107">[in] Entier qui spécifie la taille de la signature de métadonnées binaires qui est référencée par le `pvSigBlob` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b9fab-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b9fab-108">[in] Un `PCCOR_SIGNATURE` valeur pointe vers la signature de métadonnées binaires du type de valeur.</span><span class="sxs-lookup"><span data-stu-id="b9fab-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b9fab-109">[out] Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans le Registre spécifié.</span><span class="sxs-lookup"><span data-stu-id="b9fab-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9fab-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b9fab-110">Remarks</span></span>  
 <span data-ttu-id="b9fab-111">Le `GetLocalRegisterValue` méthode peut être utilisée dans un frame natif ou un juste-à-temps (JIT)-frame compilé.</span><span class="sxs-lookup"><span data-stu-id="b9fab-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9fab-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9fab-112">Requirements</span></span>  
 <span data-ttu-id="b9fab-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9fab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9fab-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9fab-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9fab-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9fab-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9fab-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9fab-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9fab-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9fab-117">See also</span></span>
