---
title: Méthode ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: ba1cc8c91c53547c6ed4025ee67a69e253f3596d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783580"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a>Méthode ICorDebugDataTarget2::GetImageLocation
Retourne le chemin d’accès d’un module à partir de l’adresse de base du module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `baseAddress`  
 dans Valeur [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui représente l’adresse de base du module.  
  
 `cchName`  
 [in] Nombre de caractères dans la mémoire tampon qui reçoit le chemin d’accès du module.  
  
 `pcchName`  
 [out] Pointeur vers le nombre de caractères écrits dans la mémoire tampon `szName`.  
  
 `szName`  
 [out] Chemin d'accès du module.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget2, interface](icordebugdatatarget2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
