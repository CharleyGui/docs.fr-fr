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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5039117c649943a1f05a91ecccf22eb4230e5e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776380"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA, structure
Contient des informations sur l’assembly référencé, y compris sa version et son niveau de prise en charge des paramètres régionaux, des processeurs et systèmes d’exploitation.  
  
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
|`usMajorVersion`|Numéro de version principale de l’assembly référencé. Cette valeur ne peut pas être égal à zéro. Si tous les bits de `usMajorVersion` sont définis, la version principale n’est pas spécifiée.|  
|`usMinorVersion`|Numéro de version secondaire de l’assembly référencé. Cette valeur ne peut pas être égal à zéro. Si tous les bits de `usMinorVersion` sont définis, la version secondaire n’est pas spécifiée.|  
|`usBuildNumber`|Le numéro de build de l’assembly référencé. Cette valeur ne peut pas être égal à zéro. Si tous les bits de `usBuildNumber` sont définis, le numéro de build n’est pas spécifié.|  
|`usRevisionNumber`|Le numéro de révision de l’assembly référencé. Cette valeur ne peut pas être égal à zéro. Si tous les bits de `usRevisionNumber` sont définis, le numéro de révision n’est pas spécifié.|  
|`szLocale`|Une liste de noms de paramètres régionaux conformément à la spécification RFC1766, séparée par des points-virgules, spécifiant les paramètres régionaux pris en charge par l’assembly référencé. Une valeur null indique l’indépendance des paramètres régionaux. **Remarque :**  Dans le .NET Framework version 1.0, vous ne pouvez pas spécifier plusieurs paramètres régionaux.|  
|`cbLocale`|La taille en caractères larges de `szLocale`.|  
|`rdwProcessor`|Un tableau d’identificateurs, tel que défini dans Winnt.h, pour les types de processeurs qui sont pris en charge par l’assembly référencé. Une valeur NULL indique l’indépendance des processeurs.|  
|`ulProcessor`|La longueur de la `rdwProcessor` tableau.|  
|`rOS`|Un tableau de [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances spécifiant les systèmes d’exploitation pris en charge par l’assembly référencé. Une valeur NULL indique l’indépendance du système d’exploitation.|  
|`ulOS`|La longueur de la `rOS` tableau.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO, structure](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
