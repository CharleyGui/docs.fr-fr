---
title: CreateAssemblyCache, fonction
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
ms.openlocfilehash: 3197c650b4f167e7a5043270797d2c4a62413d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683197"
---
# <a name="createassemblycache-function"></a>CreateAssemblyCache, fonction

Obtient un pointeur vers une nouvelle instance [IAssemblyCache](iassemblycache-interface.md) qui représente le global assembly cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppAsmCache`  
 à Pointeur retourné `IAssemblyCache` .  
  
 `dwReserved`  
 dans Réservé pour une future extensibilité. `dwReserved` doit avoir la valeur 0 (zéro).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyCache, interface](iassemblycache-interface.md)
- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
- [Global Assembly Cache](../../app-domains/gac.md)
