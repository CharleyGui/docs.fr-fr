---
title: Fonction PreBindAssemblyEx
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: a729249f7b0681941a0b1a478dbe2c0d9d6cd01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723959"
---
# <a name="prebindassemblyex-function"></a>Fonction PreBindAssemblyEx

Obtient le nom complet de la stratégie d’un assembly.  
  
 Cette fonction prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>Paramètres  

 `pAppCtx`  
 dans Identifie le contexte de l’application.  
  
 `pName`  
 dans Identifie le nom de l’assembly.  
  
 `pAsmParent`  
 dans Identifie l’assembly parent. Ce paramètre est ignoré.  
  
 `pwzRuntimeVersion`  
 dans Identifie la version du Runtime.  
  
 `ppNamePostPolicy`  
 à Contient le nom complet de la stratégie.  
  
 `pvReserved`  
 dans Réservé pour une future extensibilité. `pvReserved` doit être une référence null.  
  
## <a name="remarks"></a>Remarques  

 Le `ppNamePostPolicy` paramètre de sortie est défini uniquement si la fonction retourne HRESULT FUSION_E_REF_DEF_MISMATCH. Sinon, sa valeur est null.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
