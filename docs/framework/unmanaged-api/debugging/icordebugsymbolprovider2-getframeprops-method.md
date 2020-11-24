---
title: Méthode ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: ba1fd104c35b6e6dfdfd771f71eb19f8d532a1d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672009"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>Méthode ICorDebugSymbolProvider2::GetFrameProps

Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `codeRva`  
 [in] Adresse virtuelle relative du code.  
  
 `pCodeStartRva`  
 [out] Pointeur vers l'adresse virtuelle relative de départ de la méthode.  
  
 `pParentFrameStartRva`  
 [out] Pointeur vers l'adresse virtuelle relative de départ du frame.  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugSymbolProvider2, interface](icordebugsymbolprovider2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
