---
title: ICorDebugSymbolProvider::GetObjectSize, méthode
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 64324df49ad0b5dfa3c25455950bddc3d687b178
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379556"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a>ICorDebugSymbolProvider::GetObjectSize, méthode
Retourne la taille d'un objet en fonction de sa signature typespec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cbSignature`  
 [in] Nombre d'octets dans la signature typespec.  
  
 typeSig  
 [in] Signature typespec.  
  
 `pObjectSize`  
 [out] Pointeur vers la taille de l'objet.  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugSymbolProvider, interface](icordebugsymbolprovider-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
