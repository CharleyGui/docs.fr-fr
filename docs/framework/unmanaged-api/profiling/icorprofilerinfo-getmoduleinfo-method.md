---
title: ICorProfilerInfo::GetModuleInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ceca2133068d3ed011b9499024d127a3dd9279ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782772"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo, méthode
Pour un ID de module donné, retourne le nom de fichier du module et l'ID de l'assembly parent du module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
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
  
## <a name="remarks"></a>Notes  
 Pour les modules dynamiques, le paramètre `szName` est une chaîne vide et l'adresse de base est 0 (zéro).  
  
 Bien que le `GetModuleInfo` méthode peut être appelée dès que l’ID du module existe, l’ID de l’assembly parent ne sera pas disponible jusqu'à ce que le profileur reçoit le [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) rappel.  
  
 Suite au retour de `GetModuleInfo`, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom de fichier complet du module. Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`. Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetModuleInfo`.  
  
 Vous pouvez également commencer par appeler `GetModuleInfo` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetModuleInfo`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [GetModuleInfo2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
