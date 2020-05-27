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
ms.openlocfilehash: b6651f30e0df3a5ffc29d310b9067e76761dcf01
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007531"
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
|`prReservedMask`|Réservé à un usage interne par la common language runtime.|  
|`prRTSpecialName`|Spécifie que l’common language runtime les API internes de métadonnées doivent vérifier l’encodage du nom de la propriété.|  
|`prHasDefault`|Spécifie que la propriété a une valeur par défaut.|  
|`prUnused`|Inutilisé.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
