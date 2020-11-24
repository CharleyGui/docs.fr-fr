---
title: ICorDebugVirtualUnwinder::GetContext, méthode
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: a5a1afa47e52eff7c930698a3354a03d8c62259f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679453"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext, méthode

Obtient le contexte actuel de ce dérouleur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `contextFlags`  
 [in] Indicateurs spécifiant les parties du contexte à retourner (définition contenue dans WinNT.h).  
  
 `cbContextBuf`  
 [in] Nombre d'octets dans `contextBuf`.  
  
 `contextSize`  
 [out] Pointeur vers le nombre d'octets réellement écrits dans `contextBuf`.  
  
 `contextBuf`  
 [out] Tableau d'octets contenant le contexte actuel de ce dérouleur.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Toute valeur HRESULT indiquant un échec reçue par mscordbi est considérée comme irrécupérable et forcent les API ICorDebug à retourner `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Remarques  

 Vous définissez la valeur initiale de l' `contextBuf` argument sur la mémoire tampon de contexte retournée en appelant la méthode [ICorDebugStackWalk :: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
 Le déroulement ne pouvant restaurer qu'un sous-ensemble des registres, par exemple les registres non volatiles, le contexte peut différer de l'état du registre au moment de l'appel de la méthode.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugMemoryBuffer, interface](icordebugmemorybuffer-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
