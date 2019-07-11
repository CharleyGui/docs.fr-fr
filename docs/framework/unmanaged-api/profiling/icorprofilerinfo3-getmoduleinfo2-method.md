---
title: ICorProfilerInfo3::GetModuleInfo2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ead38d54d470c3f443ae5e27e4a2d045bc27c79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783037"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2, méthode
Étant donné un ID de module, retourne le nom de fichier du module, l'ID de l'assembly parent du module et un masque de bits qui décrit les propriétés du module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleId`  
 [in] ID du module pour lequel les informations sont récupérées.  
  
 `ppBaseLoadAddress`  
 [out] Adresse de base à laquelle le module est chargé.  
  
 `cchName`  
 [in] Longueur, en caractères, de la mémoire tampon de retour `szName`.  
  
 `pcchName`  
 [out] Pointeur vers la longueur de caractère totale du nom de fichier du module qui est retourné.  
  
 `szName`  
 [out] Mémoire tampon de caractères larges fournie par l'appelant. Suite au retour de la méthode, cette mémoire tampon contient le nom de fichier du module.  
  
 `pAssemblyId`  
 [out] Pointeur vers l'ID de l'assembly parent du module.  
  
 `pdwModuleFlags`  
 [out] Un masque de bits des valeurs à partir de la [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) énumération qui spécifient les propriétés du module.  
  
## <a name="remarks"></a>Notes  
 Pour les modules dynamiques, le paramètre `szName` est le nom de métadonnées du module et l'adresse de base est 0 (zéro). Le nom de métadonnées est la valeur figurant dans la colonne Nom de la table Module dans les métadonnées. Il est également exposé en tant que le <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> propriété au code managé et comme le `szName` paramètre de la [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) méthode au code client de métadonnées non managées.  
  
 Bien que le `GetModuleInfo2` méthode peut être appelée dès que l’ID du module existe, l’ID de l’assembly parent ne sera pas disponible jusqu'à ce que le profileur reçoit le [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) rappel.  
  
 Suite au retour de `GetModuleInfo2`, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom de fichier complet du module. Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`. Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetModuleInfo2`.  
  
 Vous pouvez également commencer par appeler `GetModuleInfo2` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetModuleInfo2`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
