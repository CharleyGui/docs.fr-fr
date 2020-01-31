---
title: Méthode ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 9fc4facda6253d0c68dcf89b2a1b06e639734efe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788850"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>Méthode ICorDebugDataTarget2::CreateVirtualUnwinder
Crée un dérouleur de pile qui commence le déroulement à partir d'un contexte initial (qui n'est pas forcément la feuille d'un thread).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a>Parameters  
 nativeThreadID  
 [in] L'ID de thread natif du thread à partir duquel dérouler la pile.  
  
 contextFlags  
 [in] Indicateurs qui spécifient les parties du contexte définies dans `initialContext`.  
  
 cbContext  
 [in] Taille de `initialContext`.  
  
 initialContext  
 [in] Données dans le contexte.  
  
 ppUnwinder  
 [out] Pointeur vers l'adresse d'un objet d'interface ICorDebugVirtualUnwinder.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si l'opération a réussi. Toute autre valeur `HRESULT` indique l'échec de l'opération. Toute défaillance `HRESULT` reçue par mscordbi est considérée comme irrécupérable et provoque le retour `CORDBG_E_DATA_TARGET_ERROR` des méthodes [ICorDebug](icordebug-interface.md).  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget2, interface](icordebugdatatarget2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
