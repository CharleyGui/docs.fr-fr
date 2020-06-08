---
title: ICorProfilerInfo::GetILFunctionBody, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: 5984c63f0e1a1859dd5cc2550d6dc37c963affb3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503001"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody, méthode
Obtient un pointeur vers le corps d’une méthode dans le code MSIL (Microsoft Intermediate Language), en commençant à son en-tête.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleId`  
 dans ID du module dans lequel la fonction réside.  
  
 `methodId`  
 dans Jeton de métadonnées pour la méthode.  
  
 `ppMethodHeader`  
 à Pointeur vers l’en-tête de la méthode.  
  
 `pcbMethodSize`  
 à Entier qui spécifie la taille de la méthode.  
  
## <a name="remarks"></a>Remarques  
 Une méthode est délimitée par le module dans lequel elle réside. Étant donné que la `GetILFunctionBody` méthode est conçue pour permettre à un outil d’accéder au code MSIL avant son chargement par le Common Language Runtime (CLR), il utilise le jeton de métadonnées de la méthode pour Rechercher l’instance souhaitée.  
  
 `GetILFunctionBody`peut retourner une CORPROF_E_FUNCTION_NOT_IL HRESULT si le `methodId` pointe vers une méthode sans code MSIL (par exemple, une méthode abstraite ou une méthode d’appel de code non managé (PInvoke)).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
