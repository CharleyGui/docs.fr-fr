---
title: ICorDebugStaticFieldSymbol::GetAddress, méthode
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 7b8072234df172eeafd77db90287ea3319c08ec7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378766"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a>ICorDebugStaticFieldSymbol::GetAddress, méthode
Obtient l’adresse d’un champ static.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 pRVA  
 [out] Pointeur vers l'adresse virtuelle relative (RVA) du champ statique.  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugStaticFieldSymbol, interface](icordebugstaticfieldsymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
