---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO, structure
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 4fdc8e1074bf45de3a8ab85500a85b124ce34fa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867332"
---
# <a name="cor_prf_assembly_reference_info-structure"></a>COR_PRF_ASSEMBLY_REFERENCE_INFO, structure
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit au CLR (Common Language Runtime) des informations sur une référence d'assembly qui doit être prise en compte lors d'un parcours de fermeture des références d'assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|Un pointeur vers la clé publique ou le jeton de l'assembly.|  
|`cbPublicKeyOrToken`|Le nombre d'octets dans la clé publique ou le jeton.|  
|`szName`|Le nom de l'assembly qui est référencé.|  
|`pMetaData`|Un pointeur vers les métadonnées de l'assembly.|  
|`pbHashValue`|Un pointeur vers un objet blob de hachage.|  
|`cbHashValue`|Le nombre d'octets de l'objet blob de hachage.|  
|`dwAssemblyRefFlags`|Les indicateurs de l'assembly.|  
  
## <a name="remarks"></a>Notes  
 La structure `COR_PRF_EX_CLAUSE_INFO` est remplie par le profileur quand il déclare des références d'assembly supplémentaires que le CLR (Common Language Runtime) doit prendre en compte lors de la réalisation d'un parcours de fermeture des références d'assembly.  
  
 Si le profileur s’inscrit à la méthode de rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , le runtime passe le chemin d’accès et le nom de l’assembly à charger, ainsi qu’un pointeur vers un objet d’interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) à cette méthode. Le profileur peut ensuite appeler la méthode [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) avec un objet `COR_PRF_ASSEMBLY_REFERENCE_INFO` pour chaque assembly cible qu’il prévoit de référencer à partir de l’assembly spécifié dans le rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de profilage](profiling-structures.md)
- [GetAssemblyReferences, méthode](icorprofilercallback6-getassemblyreferences-method.md)
- [AddAssemblyReference, méthode](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
