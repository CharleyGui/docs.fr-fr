---
title: ICorPublishAppDomain::GetName, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 2f91891164f1f80617cab10347eb4a7a08762c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140352"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName, méthode
Obtient le nom du domaine d’application représenté par ce [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cchName`  
 [in] Taille du tableau `szName`.  
  
 `pcchName`  
 à Pointeur vers le nombre de caractères larges, y compris le caractère null, retourné dans le tableau de `szName`.  
  
 `szName`  
 à Tableau dans lequel stocker le nom.  
  
## <a name="remarks"></a>Notes  
 Si `szName` n’est pas null, la méthode `GetName` copie jusqu’à `cchName` caractères (y compris la marque de fin null) dans `szName`. Si une valeur non null est retournée dans `pcchName`, le nombre réel de caractères dans le nom (y compris la marque de fin null) est stocké dans le tableau `szName`.  
  
 La méthode `GetName` retourne un HRESULT S_OK quel que soit le nombre de caractères copiés.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublishAppDomain, interface](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
