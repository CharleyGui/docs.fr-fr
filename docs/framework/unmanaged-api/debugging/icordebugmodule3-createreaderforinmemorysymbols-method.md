---
title: ICorDebugModule3::CreateReaderForInMemorySymbols, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 44f4c59f95c28f9982d67875584e2f9803c0ed3b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709568"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols, méthode

Crée un lecteur de symboles de débogage pour un module dynamique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>Paramètres  

 riid  
 dans IID de l’interface COM à retourner. En règle générale, il s’agit d’une [interface ISymUnmanagedReader](../diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 à Pointeur vers un pointeur vers l’interface retournée.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK  
 Le lecteur a été créé avec succès.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Le module n’est pas un module en mémoire ou dynamique.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Les symboles n’ont pas été fournis par l’application ou ne sont pas encore disponibles.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible de créer le lecteur.  
  
## <a name="remarks"></a>Remarques  

 Cette méthode peut également être utilisée pour créer un objet lecteur de symboles pour les modules en mémoire (non dynamiques), mais uniquement une fois que les symboles sont disponibles pour la première fois (indiqué par le rappel de la [méthode UpdateModuleSymbols,](icordebugmanagedcallback-updatemodulesymbols-method.md) ).  
  
 Cette méthode retourne une nouvelle instance de lecteur à chaque fois qu’elle est appelée (comme [CComPtrBase :: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)). Par conséquent, le débogueur doit mettre en cache le résultat et demander une nouvelle instance uniquement lorsque les données sous-jacentes ont été modifiées (autrement dit, lors de la réception d’un rappel de [méthode loadClass](icordebugmanagedcallback-loadclass-method.md) ).  
  
 Les modules dynamiques n’ont aucun symbole disponible tant que le premier type n’a pas été chargé (comme indiqué par le rappel de la [méthode loadClass](icordebugmanagedcallback-loadclass-method.md) ).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRemoteTarget, interface](icordebugremotetarget-interface.md)
- [ICorDebug, interface](icordebug-interface.md)

- [Interfaces de débogage](debugging-interfaces.md)
