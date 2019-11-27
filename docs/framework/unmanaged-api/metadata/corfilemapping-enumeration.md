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
ms.openlocfilehash: f85a36c810df52f871ecc75b92a3b4440455c66b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450295"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping, énumération
Contient des valeurs qui décrivent le type de mappage de fichier retourné à partir d’un appel à la méthode [IMetaDataInfo :: GetFileMapping,](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) .  
  
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
|`fmFlat`|Le fichier est mappé en tant que fichier de données. Autrement dit, l’indicateur `SEC_IMAGE` n’a pas été passé à la fonction de `CreateFileMapping` Microsoft Win32.|  
|`fmExecutableImage`|Le fichier est mappé pour exécution, à l’aide de la fonction `LoadLibrary` ou de la fonction `CreateFileMapping` avec l’indicateur `SEC_IMAGE`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [GetFileMapping, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
