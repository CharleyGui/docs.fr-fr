---
title: IAssemblyEnum::GetNextAssembly, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
ms.openlocfilehash: af43d9cf4d5aa790036a13d060fc6ccf113f335d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719890"
---
# <a name="iassemblyenumgetnextassembly-method"></a>IAssemblyEnum::GetNextAssembly, méthode

Obtient un pointeur vers l' [IAssemblyName](iassemblyname-interface.md) suivant contenu dans cet objet [IAssemblyEnum](iassemblyenum-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pvReserved`  
 dans Réservé pour une future extensibilité. `pvReserved` doit être une référence null.  
  
 `ppName`  
 à Pointeur retourné `IAssemblyName` .  
  
 `dwFlags`  
 dans Réservé pour une future extensibilité. `dwFlags` doit avoir la valeur 0 (zéro).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyName, interface](iassemblyname-interface.md)
- [IAssemblyEnum, interface](iassemblyenum-interface.md)
