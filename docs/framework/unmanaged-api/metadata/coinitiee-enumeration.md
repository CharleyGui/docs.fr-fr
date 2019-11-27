---
title: COINITIEE, énumération
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: 2ccc038b4420040779dae70f15e3a8827ba94180
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444101"
---
# <a name="coinitiee-enumeration"></a>COINITIEE, énumération
Spécifie les constantes utilisées par [CoInitializeEE,](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) lors de l’initialisation du Common Language Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Mode d’initialisation par défaut. Cela initialise le runtime et crée le <xref:System.AppDomain>par défaut.|  
|`COINITEE_DLL`|Initialise pour exécuter une DLL managée.|  
|`COINITEE_MAIN`|Initialise pour exécuter un EXE managé. Cela initialise le runtime, mais ne crée pas le <xref:System.AppDomain>par défaut, qui est créé après l’entrée de la routine principale de l’EXE.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
