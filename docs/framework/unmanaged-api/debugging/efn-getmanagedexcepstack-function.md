---
title: _EFN_GetManagedExcepStack, fonction
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61f4e057a487462feb385ca0e3ca977fdd165f56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739094"
---
# <a name="efngetmanagedexcepstack-function"></a>\_EFN\_GetManagedExcepStack (fonction)
Retourne une version de chaîne de la trace de pile contenue dans une adresse d'objet exception managée donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `Client`  
 [in] Le client en cours de débogage.  
  
 `StackObjAddr`  
 [in] Un pointeur d’objet managé, dérivé <xref:System.Exception>.  
  
 szStackString  
 [out] La chaîne retournée.  
  
 `cbString`  
 [out] Le nombre de caractères disponibles dans la mémoire tampon de chaîne.  
  
## <a name="remarks"></a>Notes  
 S’il n’existe aucun code managé sur le thread actuellement dans le contexte, la fonction retourne les HRESULT SOS_E_NOMANAGEDCODE avec une valeur de 0xa0 et un code d’erreur de 0 x 1000.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** SOS_Stacktrace.h  
  
 **Version du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
