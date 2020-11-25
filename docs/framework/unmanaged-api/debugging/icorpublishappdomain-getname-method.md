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
ms.openlocfilehash: d6b05333b9e02c4202c0fd9bdee9b5c055aa4da3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694358"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName, méthode

Obtient le nom du domaine d’application représenté par ce [ICorPublishAppDomain](icorpublishappdomain-interface.md).  
  
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
 à Pointeur vers le nombre de caractères larges, y compris le caractère null, retourné dans le `szName` tableau.  
  
 `szName`  
 à Tableau dans lequel stocker le nom.  
  
## <a name="remarks"></a>Remarques  

 Si `szName` n’a pas la valeur null, la `GetName` méthode copie jusqu’à `cchName` caractères (y compris la marque de fin null) dans `szName` . Si une valeur non null est retournée dans `pcchName` , le nombre réel de caractères dans le nom (y compris la marque de fin null) est stocké dans le `szName` tableau.  
  
 La `GetName` méthode retourne un S_OK HRESULT quel que soit le nombre de caractères copiés.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublishAppDomain, interface](icorpublishappdomain-interface.md)
