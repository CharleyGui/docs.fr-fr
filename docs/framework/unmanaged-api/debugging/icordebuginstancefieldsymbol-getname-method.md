---
title: ICorDebugInstanceFieldSymbol::GetName, méthode
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: e466a62761cc6dd1f1fc0a54f05d54f85c190d07
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724934"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a>ICorDebugInstanceFieldSymbol::GetName, méthode

Obtient le nom du champ d'instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cchName`  
 [in] Nombre de caractères dans la mémoire tampon `szName`.  
  
 `pcchName`  
 [out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.  
  
 `szName`  
 [out] Tableau de caractères qui stocke le nom retourné.  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugInstanceFieldSymbol, interface](icordebuginstancefieldsymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
