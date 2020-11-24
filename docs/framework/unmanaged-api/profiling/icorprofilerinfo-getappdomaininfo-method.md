---
title: ICorProfilerInfo::GetAppDomainInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 62055a98197f5f8bd4cfc02e99891b83ef6341e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680290"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>ICorProfilerInfo::GetAppDomainInfo, méthode

Accepte un ID de domaine d'application Retourne un nom de domaine d'application et l'ID du processus qui le contient.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a>Paramètres  

 `appDomainId`  
 [in] ID du domaine d'application.  
  
 `cchName`  
 [in] Longueur, en caractères, de la mémoire tampon de retour `szName`.  
  
 `pcchName`  
 [out] Pointeur vers la longueur totale en caractères du nom de domaine d'application.  
  
 `szName`  
 [out] Mémoire tampon de caractères larges fournie par l'appelant. Suite au retour de la méthode, `szName` contient le nom de domaine d'application complet ou partiel.  
  
 `pProcessId`  
 [out] Pointeur vers l'ID du processus qui contient le domaine d'application.  
  
## <a name="remarks"></a>Remarques  

 Suite au retour de cette méthode, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom complet du domaine d'application. Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`. Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetAppDomainInfo`.  
  
 Vous pouvez également commencer par appeler `GetAppDomainInfo` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetAppDomainInfo`.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
