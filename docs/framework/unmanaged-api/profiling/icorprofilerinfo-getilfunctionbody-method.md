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
ms.openlocfilehash: 8160bb5b9ca5e0a4e22a1a831e978eaf125e7605
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870490"
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
  
## <a name="parameters"></a>Parameters  
 `moduleId`  
 dans ID du module dans lequel la fonction réside.  
  
 `methodId`  
 dans Jeton de métadonnées pour la méthode.  
  
 `ppMethodHeader`  
 à Pointeur vers l’en-tête de la méthode.  
  
 `pcbMethodSize`  
 à Entier qui spécifie la taille de la méthode.  
  
## <a name="remarks"></a>Notes  
 Une méthode est délimitée par le module dans lequel elle réside. Étant donné que la méthode `GetILFunctionBody` est conçue pour permettre à un outil d’accéder au code MSIL avant qu’elle ait été chargée par le common language runtime (CLR), elle utilise le jeton de métadonnées de la méthode pour Rechercher l’instance souhaitée.  
  
 `GetILFunctionBody` pouvez retourner un HRESULT CORPROF_E_FUNCTION_NOT_IL si le `methodId` pointe vers une méthode sans code MSIL (par exemple, une méthode abstraite ou une méthode d’appel de code non managé (PInvoke)).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
