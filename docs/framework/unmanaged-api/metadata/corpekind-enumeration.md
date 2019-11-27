---
title: CorPEKind, énumération
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 74670a1477546066145bd4bbf2f123a252e10b55
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436471"
---
# <a name="corpekind-enumeration"></a>CorPEKind, énumération
Contient des valeurs qui décrivent un fichier exécutable portable (PE, Portable Executable), tel qu’il est retourné à partir d’un appel à [IMetaDataImport2 :: GetPEKind,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`peNot`|Indique qu’il ne s’agit pas d’un fichier PE.|  
|`peILOnly`|Indique que ce fichier PE contient uniquement du code managé.|  
|`pe32BitRequired`|Indique que ce fichier PE effectue des appels Win32.|  
|`pe32Plus`|Indique que ce fichier PE s’exécute sur une plateforme 64 bits.|  
|`pe32Unmanaged`|Indique que ce fichier PE est du code natif.|  
|pe32BitPreferred|Indique que ce fichier PE est indépendant de la plateforme et qu’il préfère être chargé dans un environnement 32 bits.|  
  
## <a name="remarks"></a>Notes  
 Ces valeurs peuvent être utilisées dans des combinaisons au niveau du bit.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
