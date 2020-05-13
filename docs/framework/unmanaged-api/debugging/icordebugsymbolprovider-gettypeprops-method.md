---
title: ICorDebugSymbolProvider::GetTypeProps, méthode
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: e116716284bb2081edb669e7fc9083cde10f6457
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379363"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider::GetTypeProps, méthode
Retourne des informations sur les propriétés d'un type, comme le nombre de signature de ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans une vtable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tableRva`  
 [in] Adresse virtuelle relative (RVA) dans une vtable.  
  
 `cbSignature`  
 [in] Taille du tableau `signature`. Consultez la section Notes.  
  
 `pcbSignature`  
 [out] Pointeur vers la taille du tableau `signature` retourné.  
  
 `signature`  
 [out] Mémoire tampon qui conserve les signatures typespec de tous les paramètres génériques.  
  
## <a name="remarks"></a>Remarks  
 Pour récupérer la taille requise du tableau du type `signature` , affectez à l’argument la valeur `cbSignature` 0 et `signature` à la **valeur null**. Suite au retour de la méthode, `pcbSignature` contient le nombre d'octets requis pour le tableau `signature`.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetMethodProps, méthode](icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider, interface](icordebugsymbolprovider-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
