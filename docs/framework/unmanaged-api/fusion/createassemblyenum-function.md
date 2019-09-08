---
title: CreateAssemblyEnum, fonction
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795387"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum, fonction
Obtient un pointeur vers une instance de [IAssemblyEnum](iassemblyenum-interface.md) qui peut énumérer les objets de l’assembly avec l' [IAssemblyName](iassemblyname-interface.md)spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>Paramètres  
 `pEnum`  
 à Pointeur vers un emplacement de mémoire qui contient le `IAssemblyEnum` pointeur demandé.  
  
 `pUnkReserved`  
 dans Réservé pour une future extensibilité. `pUnkReserved`doit être une référence null.  
  
 `pName`  
 dans `IAssemblyName` De l’assembly demandé. Ce nom est utilisé pour filtrer l’énumération. Elle peut avoir la valeur null pour énumérer tous les assemblys du Global Assembly Cache.  
  
 `dwFlags`  
 dans Indicateurs permettant de modifier le comportement de l’énumérateur. Ce paramètre contient exactement un bit de l’énumération [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .  
  
 `pvReserved`  
 dans Réservé pour une future extensibilité. `pvReserved`doit être une référence null.  
  
## <a name="remarks"></a>Notes  
 Le `dwFlags` paramètre contient exactement un bit de l' `ASM_CACHE_FLAGS` énumération.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyEnum, interface](iassemblyenum-interface.md)
- [IAssemblyName, interface](iassemblyname-interface.md)
- [Fonctions statiques globales de fusion](fusion-global-static-functions.md)
