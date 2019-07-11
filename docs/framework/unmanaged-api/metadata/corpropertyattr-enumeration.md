---
title: CorPropertyAttr, énumération
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5fb70d530af24798636972de0a4d6280dbcb8f1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781626"
---
# <a name="corpropertyattr-enumeration"></a>CorPropertyAttr, énumération
Contient des valeurs qui décrivent les métadonnées d'une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`prSpecialName`|Spécifie que la propriété est spéciale et que son nom décrit comment.|  
|`prReservedMask`|Réservé à un usage interne par le common language runtime.|  
|`prRTSpecialName`|Spécifie que les métadonnées du common language runtime API internes doivent vérifier l’encodage du nom de la propriété.|  
|`prHasDefault`|Spécifie que la propriété a une valeur par défaut.|  
|`prUnused`|Non utilisé.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
