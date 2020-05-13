---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 6de75e1e27660ac91bd6320a501db47f3b055fb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212254"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Configure la façon dont le débogueur gère les mises à jour en mémoire des métadonnées dans le processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `flags`  
 Valeur d’énumération [writeablemetadataupdatemode,](writeablemetadataupdatemode-enumeration.md) qui spécifie si les mises à jour en mémoire des métadonnées dans le processus cible sont visibles ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) ou non visibles ( `WriteableMetadataUpdateMode::LegacyCompatPolicy` ) vers le débogueur.  
  
## <a name="remarks"></a>Remarks  
 Les mises à jour apportées aux métadonnées du processus cible peuvent provenir de Modifier et continuer, d'un profileur ou de <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess7, interface](icordebugprocess7-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
