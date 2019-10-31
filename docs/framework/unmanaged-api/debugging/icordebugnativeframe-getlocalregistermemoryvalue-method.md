---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: d44d7c23f88f5ea93f608d06b69f69b2c3637b5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096848"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="1438d-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1438d-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="1438d-103">Obtient la valeur d’un argument ou d’une variable locale dont le mot de poids faible et le mot de poids fort sont stockés respectivement dans l’emplacement de mémoire et dans le registre spécifié pour ce frame natif.</span><span class="sxs-lookup"><span data-stu-id="1438d-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1438d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1438d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1438d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1438d-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="1438d-106">dans Valeur de l’énumération « CorDebugRegister » qui spécifie le registre contenant le mot de poids fort de la valeur.</span><span class="sxs-lookup"><span data-stu-id="1438d-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="1438d-107">dans Valeur `CORDB_ADDRESS` qui spécifie l’emplacement mémoire contenant le mot de poids faible de la valeur.</span><span class="sxs-lookup"><span data-stu-id="1438d-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="1438d-108">dans Entier qui spécifie la taille de la signature de métadonnées binaires référencée par le paramètre `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="1438d-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1438d-109">dans Valeur `PCCOR_SIGNATURE` qui pointe vers la signature de métadonnées binaires du type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="1438d-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1438d-110">à Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans le registre et l’emplacement de mémoire spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1438d-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1438d-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="1438d-111">Requirements</span></span>  
 <span data-ttu-id="1438d-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1438d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1438d-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1438d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1438d-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1438d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1438d-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1438d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1438d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1438d-116">See also</span></span>
