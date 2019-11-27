---
title: ASSEMBLYMETADATA, structure
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444264"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA, structure
Contient des informations sur l’assembly référencé, y compris sa version et son niveau de prise en charge pour les paramètres régionaux, les processeurs et les systèmes d’exploitation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`usMajorVersion`|Numéro de version principale de l’assembly référencé. Cette valeur ne peut pas être égale à zéro. Si tous les bits de `usMajorVersion` sont définis, la version principale n’est pas spécifiée.|  
|`usMinorVersion`|Numéro de version mineure de l’assembly référencé. Cette valeur ne peut pas être égale à zéro. Si tous les bits de `usMinorVersion` sont définis, la version mineure n’est pas spécifiée.|  
|`usBuildNumber`|Numéro de build de l’assembly référencé. Cette valeur ne peut pas être égale à zéro. Si tous les bits de `usBuildNumber` sont définis, le numéro de build n’est pas spécifié.|  
|`usRevisionNumber`|Numéro de révision de l’assembly référencé. Cette valeur ne peut pas être égale à zéro. Si tous les bits de `usRevisionNumber` sont définis, le numéro de révision n’est pas spécifié.|  
|`szLocale`|Liste des noms de paramètres régionaux conformes à la spécification RFC1766, séparés par des points-virgules, en spécifiant les paramètres régionaux pris en charge par l’assembly référencé. Une valeur null indique l’indépendance des paramètres régionaux. **Remarque :**  Dans le .NET Framework version 1,0, vous ne pouvez pas spécifier plusieurs paramètres régionaux.|  
|`cbLocale`|Taille en caractères larges de `szLocale`.|  
|`rdwProcessor`|Tableau d’identificateurs, tel que défini dans Winnt. h, pour les types de processeurs pris en charge par l’assembly référencé. Une valeur NULL indique l’indépendance du processeur.|  
|`ulProcessor`|Longueur du tableau de `rdwProcessor`.|  
|`rOS`|Tableau d’instances [OSInfo,](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) spécifiant les systèmes d’exploitation pris en charge par l’assembly référencé. Une valeur NULL indique l’indépendance du système d’exploitation.|  
|`ulOS`|Longueur du tableau de `rOS`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO, structure](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
