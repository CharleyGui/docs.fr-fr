---
title: GetCORVersion, fonction
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178188"
---
# <a name="getcorversion-function"></a>GetCORVersion, fonction
Retourne le numéro de version de l’heure d’exécution de langue commune (CLR) qui est en cours d’exécution dans le processus actuel.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>Paramètres  
 `pbuffer`  
 Un pointeur vers un tampon dans lequel le CLR renvoie une chaîne spécifiant la version du temps d’exécution qui est actuellement chargé dans le processus. La corde retournée prend la même forme que les cordes passées à [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), par exemple, "v1.0.1216". Si le temps d’exécution n’a pas encore été chargé dans le processus, la fonction renvoie les informations d’annuaire appropriées pour la dernière version du temps d’exécution installé sur l’ordinateur.  
  
 `cchBuffer`  
 Le nombre de`WCHAR`caractères (s) `pbuffer`qui peuvent être conservés dans .  
  
 `dwLength`  
 Un pointeur sur le nombre `pbuffer`de caractères effectivement retourné dans . S’il `pbuffer` s’agit d’un pointeur nul, le temps de course revient E_POINTER. Si le nombre de caractères `pbuffer` est plus élevé, puis la longueur de , le temps d’exécution retourne ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
