---
title: ICorDebugDataTarget2::CreateVirtualUnwinder, méthode
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 7a479fba9bbcf28c60474fffc6219af23e62c251
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976497"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder, méthode
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
  
## <a name="parameters"></a>Paramètres  
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
 `S_OK` si l'opération a réussi. Toute autre valeur `HRESULT` indique l'échec de l'opération. Toute défaillance `HRESULT` reçue par mscordbi est considérée comme irrécupérable et [ICorDebug](icordebug-interface.md) provoque le retour `CORDBG_E_DATA_TARGET_ERROR`des méthodes ICorDebug.  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget2, interface](icordebugdatatarget2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
