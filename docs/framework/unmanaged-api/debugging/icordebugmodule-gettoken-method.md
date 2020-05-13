---
title: ICorDebugModule::GetToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: a6aff37a480460bfed7064d59b4c5276daf3207c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212501"
---
# <a name="icordebugmodulegettoken-method"></a>ICorDebugModule::GetToken, méthode
Obtient le jeton pour l’entrée de table pour ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pToken`  
 à Pointeur vers le `mdModule` jeton qui référence les métadonnées du module.  
  
## <a name="remarks"></a>Remarks  
 Le jeton peut être passé aux interfaces d’importation de métadonnées [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)et [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Métadonnées](../metadata/index.md)
