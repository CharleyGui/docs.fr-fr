---
title: _EFN_GetManagedObjectFieldInfo, fonction
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: 42f7020212dd2db793b7c7d20a15c129157e7261
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860764"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a>\_EFN\_fonction GetManagedObjectFieldInfo
Obtient l'offset du début d'un objet jusqu'à un champ, ainsi que la valeur du champ, à l'aide du pointeur d'objet et du nom de champ fournis.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `Client`  
 dans Pointeur vers le client de débogage.  
  
 `objAddr`  
 dans Pointeur d’objet managé.  
  
 szFieldName  
 dans Pointeur d’objet managé vers le nom de champ.  
  
 `pValue`  
 à Valeur de champ. Ce paramètre peut avoir la valeur Null.  
  
 `pOffset`  
 à Offset de `objAddr` à du champ. Ce paramètre peut avoir la valeur Null.  
  
## <a name="remarks"></a>Notes   
 Si le décalage est égal à 0, aucun décalage n’est écrit.  
  
 S’il n’existe aucun code managé sur le thread actuellement en contexte, la fonction retourne HRESULT SOS_E_NOMANAGEDCODE avec une valeur d’installation de 0xa0 et un code d’erreur 0x1000.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** SOS_Stacktrace. h  
  
 **Version de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales du débogage](debugging-global-static-functions.md)
