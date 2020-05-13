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
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryRegisterValue, méthode
Obtient la valeur d’un argument ou d’une variable locale dont le mot de poids faible et le mot de poids fort sont stockés dans le registre et l’emplacement de mémoire spécifiés, respectivement, pour ce frame natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `highWordAddress`  
 dans `CORDB_ADDRESS`Valeur qui spécifie l’emplacement mémoire contenant le mot de poids fort de la valeur.  
  
 `lowWordRegister`  
 dans Valeur de l’énumération « CorDebugRegister » qui spécifie le registre contenant le mot de poids faible de la valeur.  
  
 `cbSigBlob`  
 dans Entier qui spécifie la taille de la signature de métadonnées binaires référencée par le `pvSigBlob` paramètre.  
  
 `pvSigBlob`  
 dans `PCCOR_SIGNATURE`Valeur qui pointe vers la signature de métadonnées binaires du type de la valeur.  
  
 `ppValue`  
 à Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans le registre et l’emplacement de mémoire spécifiés.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
