---
title: ICorDebugModule::GetMetaDataInterface, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: 8f3cc16054d4b5340c9460e9c3fbcba6e563567a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212553"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface, méthode
Obtient un objet d’interface de métadonnées qui peut être utilisé pour examiner les métadonnées du module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `riid`  
 dans ID de référence qui spécifie l’interface de métadonnées.  
  
 `ppObj`  
 à Pointeur vers l’adresse d’un `T:IUnknown` objet qui est l’une des [interfaces de métadonnées](../metadata/metadata-interfaces.md).  
  
## <a name="remarks"></a>Remarks  
 Le débogueur peut utiliser la `GetMetaDataInterface` méthode pour effectuer une copie des métadonnées d’origine d’un module, ce qu’il doit faire pour modifier ce module. Le débogueur appelle `GetMetaDataInterface` pour obtenir un objet d’interface [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) pour le module, puis appelle [IMetaDataEmit :: SaveToMemory,](../metadata/imetadataemit-savetomemory-method.md) pour enregistrer une copie des métadonnées du module dans la mémoire.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Métadonnées](../metadata/index.md)
