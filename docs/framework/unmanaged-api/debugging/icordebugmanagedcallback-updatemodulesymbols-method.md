---
title: ICorDebugManagedCallback::UpdateModuleSymbols, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
ms.openlocfilehash: 1615d00a9a25cd2f4aa7d9b84de54b5e7670a3fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730567"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols, méthode

Notifie le débogueur que les symboles d’un module common language runtime ont changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le module dans lequel les symboles ont été modifiés.  
  
 `pModule`  
 dans Pointeur vers un objet ICorDebugModule qui représente le module dans lequel les symboles ont été modifiés.  
  
 `pSymbolStream`  
 dans Pointeur vers un objet COM Win32 `IStream` qui contient les symboles modifiés.  
  
## <a name="remarks"></a>Remarques  

 Cette méthode offre la possibilité de mettre à jour la vue du débogueur des symboles d’un module en appelant [ISymUnmanagedReader :: UpdateSymbolStore](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) ou [ISymUnmanagedReader :: ReplaceSymbolStore,](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).  
  
 Ce rappel peut se produire plusieurs fois pour le même module.  
  
 Un débogueur doit tenter de lier des points d’arrêt de niveau source non liés.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
