---
title: ICorDebugAppDomain::GetName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179087"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName, méthode
Obtient le nom du domaine de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cchName`  
 [in] Taille du tableau `szName`. Définissez cette valeur à zéro pour mettre cette méthode en mode requête.  
  
 `pcchName`  
 [out] Un pointeur sur la taille du nom ou `szName`le nombre de caractères effectivement retournés dans . En mode requête, cette valeur permet à l’appelant de savoir dans quelle mesure un tampon à allouer pour le nom.  
  
 `szName`  
 [out] Un tableau qui stocke le nom du domaine de l’application.  
  
## <a name="remarks"></a>Notes   
 Un débbuggeur `GetName` appelle la méthode une fois pour obtenir la taille d’un tampon nécessaire pour le nom. Le débbuggeur alloue le tampon, puis appelle la méthode une deuxième fois pour remplir le tampon. Le premier appel, pour obtenir la taille du nom, est appelé *mode requête*.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
