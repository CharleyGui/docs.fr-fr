---
title: ICorDebugDataTarget2::GetSymbolProviderForImage, méthode
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 7800630be0ed9afb321d607046be308088781388
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976445"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a>ICorDebugDataTarget2::GetSymbolProviderForImage, méthode
Retourne le fournisseur de symboles d'un module à partir de l'adresse de base de ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `imageBaseAddress`  
 dans Valeur [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) qui représente l’adresse de base d’un module.  
  
 `ppSymProvider`  
 à Pointeur vers l’adresse d’un objet [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) .  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget2, interface](icordebugdatatarget2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
