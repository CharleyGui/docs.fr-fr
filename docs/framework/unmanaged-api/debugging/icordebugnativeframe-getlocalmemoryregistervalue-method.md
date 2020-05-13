---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: 91f0a75f127afcff89c2b92bf3ed67466b205081
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213047"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="1bffb-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1bffb-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="1bffb-103">Obtient la valeur d’un argument ou d’une variable locale dont le mot de poids faible et le mot de poids fort sont stockés dans le registre et l’emplacement de mémoire spécifiés, respectivement, pour ce frame natif.</span><span class="sxs-lookup"><span data-stu-id="1bffb-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bffb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bffb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bffb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bffb-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="1bffb-106">dans `CORDB_ADDRESS`Valeur qui spécifie l’emplacement mémoire contenant le mot de poids fort de la valeur.</span><span class="sxs-lookup"><span data-stu-id="1bffb-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="1bffb-107">dans Valeur de l’énumération « CorDebugRegister » qui spécifie le registre contenant le mot de poids faible de la valeur.</span><span class="sxs-lookup"><span data-stu-id="1bffb-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="1bffb-108">dans Entier qui spécifie la taille de la signature de métadonnées binaires référencée par le `pvSigBlob` paramètre.</span><span class="sxs-lookup"><span data-stu-id="1bffb-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1bffb-109">dans `PCCOR_SIGNATURE`Valeur qui pointe vers la signature de métadonnées binaires du type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="1bffb-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1bffb-110">à Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans le registre et l’emplacement de mémoire spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1bffb-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bffb-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1bffb-111">Requirements</span></span>  
 <span data-ttu-id="1bffb-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bffb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bffb-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bffb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bffb-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bffb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bffb-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bffb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bffb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bffb-116">See also</span></span>
