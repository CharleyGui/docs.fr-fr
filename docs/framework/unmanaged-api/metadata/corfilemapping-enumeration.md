---
title: CorFileMapping, énumération
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007388"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping, énumération
Contient des valeurs qui décrivent le type de mappage de fichier retourné à partir d’un appel à la méthode [IMetaDataInfo :: GetFileMapping,](imetadatainfo-getfilemapping-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`fmFlat`|Le fichier est mappé en tant que fichier de données. Autrement dit, l' `SEC_IMAGE` indicateur n’a pas été passé à la `CreateFileMapping` fonction Microsoft Win32.|  
|`fmExecutableImage`|Le fichier est mappé pour exécution, à l’aide de la `LoadLibrary` fonction ou de la `CreateFileMapping` fonction avec l' `SEC_IMAGE` indicateur.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
- [GetFileMapping, méthode](imetadatainfo-getfilemapping-method.md)
