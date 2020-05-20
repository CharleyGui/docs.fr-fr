---
title: WriteableMetadataUpdateMode, énumération
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: 0793dcbe4d080da83cf507e04303d66fbbb56b85
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420641"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>WriteableMetadataUpdateMode, énumération
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit des valeurs qui spécifient si les mises à jour en mémoire apportées aux métadonnées sont visibles par un débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a>Membres  
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|Maintient la compatibilité avec les versions antérieures de .NET Framework lors de la mise à jour en mémoire de métadonnées visibles. Pour plus d'informations, consultez la section Remarques.|  
|`AlwaysShowUpdates`|Rend les mises à jour en mémoire apportées aux métadonnées visibles par le débogueur.|  
  
## <a name="remarks"></a>Notes  
 Un membre de l' `WriteableMetadataUpdateMode` énumération peut être passé à la méthode [setwriteablemetadataupdatemode,](icordebugprocess7-setwriteablemetadataupdatemode-method.md) pour contrôler si les mises à jour en mémoire des métadonnées dans le processus cible sont visibles par le débogueur.  
  
 L'option `LegacyCompatPolicy` force le même comportement que dans les versions de .NET Framework antérieures à 4.5.2. Cela signifie souvent que les métadonnées provenant des mises à jour ne sont pas visibles. Cependant, les appels à certaines méthodes de débogage forcent implicitement le débogueur à rendre visibles les mises à jour. Par exemple, si le débogueur passe [ICorDebugILFrame :: GetLocalVariable](icordebugilframe-getlocalvariable-method.md) l’index d’une variable qui est introuvable dans les métadonnées d’origine de la méthode, toutes les métadonnées du module sont mises à jour vers un instantané correspondant à l’état actuel du processus. En d'autres termes, avec l'option `LegacyCompatPolicy`, le débogueur peut voir aucune, certaines ou toutes les mises à jour des métadonnées disponibles, selon la façon dont il utilise les autres parties de l'API de débogage non managée.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode, méthode](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
