---
title: ICorProfilerInfo3::GetRuntimeInformation, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: 20556d85655a0a1bbe069a94b99c19c774a13ce6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449678"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation, méthode
Fournit des informations de version sur le common language runtime (CLR) en cours de profilage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pClrInstanceId`  
 à ID représentatif d’une instance CLR en cours d’exécution dans un processus. Il s’agit du même que le `ClrInstanceID` que l’événement de démarrage suivi d’événements pour Windows (ETW) signale.  
  
 `pRuntimeType`  
 à Type au moment de l’exécution. Ce paramètre retourne `COR_PRF_DESKTOP_CLR` pour la version de bureau du CLR, ou `COR_PRF_CORE_CLR` pour la version principale du CLR utilisée dans Silverlight.  
  
 `pMajorVersion`  
 à Numéro de version principale du CLR.  
  
 `pMinorVersion`  
 à Numéro de version mineure du CLR.  
  
 `pBuildVersion`  
 à Numéro de la version de build du CLR.  
  
 `pQFEVersion`  
 à Numéro de version du CLR qui est associé à une mise à jour logicielle.  
  
 `cchVersionString`  
 dans Longueur, en caractères, de la mémoire tampon vers laquelle `szVersionString` pointe.  
  
 `pcchVersionString`  
 à Longueur, en caractères, de `szVersionString`.  
  
 `szVersionString`  
 à Chaîne de version CLR.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez passer NULL pour n’importe quel paramètre. Toutefois, `pcchVersionString` ne peut pas avoir la valeur null, sauf si `szVersionString` est également null.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
