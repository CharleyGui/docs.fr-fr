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
ms.openlocfilehash: 501a4543940437bfe2a6cb0952aed8184107150c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672160"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName, méthode

Obtient le nom du domaine d’application.  
  
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
 [in] Taille du tableau `szName`. Définissez cette valeur sur zéro pour mettre cette méthode en mode requête.  
  
 `pcchName`  
 à Pointeur vers la taille du nom ou le nombre de caractères réellement retournés dans `szName` . En mode requête, cette valeur permet à l’appelant de connaître la taille d’une mémoire tampon à allouer au nom.  
  
 `szName`  
 à Tableau qui stocke le nom du domaine d’application.  
  
## <a name="remarks"></a>Remarques  

 Un débogueur appelle la `GetName` méthode une fois pour obtenir la taille d’une mémoire tampon nécessaire pour le nom. Le débogueur alloue la mémoire tampon, puis appelle la méthode une deuxième fois pour remplir la mémoire tampon. Le premier appel, pour obtenir la taille du nom, est appelé *mode de requête*.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
