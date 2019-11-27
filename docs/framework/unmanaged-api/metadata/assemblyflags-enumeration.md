---
title: Énumération AssemblyFlags
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: ffb5953c843a338b4548253457a0c3b1ca0c20f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444301"
---
# <a name="assemblyflags-enumeration"></a>Énumération AssemblyFlags
Contient des valeurs qui décrivent les fonctionnalités d’exécution d’un assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`afImplicitExportedTypes`|Spécifie que les définitions de type exporté sont implicites dans les fichiers qui composent l’assembly. Dans les versions 1,0 et 1,1 de .NET Framework, cette valeur est toujours supposée être définie.|  
|`afImplicitResources`|Spécifie que les définitions de ressource sont implicites dans les fichiers qui composent l’assembly. Dans les .NET Framework 1,0 et 1,1, cette valeur est toujours supposée être définie.|  
|`afNonSideBySideAppDomain`|Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même domaine d’application.|  
|`afNonSideBySideProcess`|Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même processus.|  
|`afNonSideBySideMachine`|Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent sur le même ordinateur.|  
  
## <a name="remarks"></a>Notes  
 Les valeurs comprises entre 0x0010 et 0x0070, incluses, sont utilisées pour décrire les fonctionnalités de compatibilité côte à côte de l’assembly référencé. Si aucune de ces valeurs n’est définie, l’assembly est supposé être compatible côte à côte.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MsCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
