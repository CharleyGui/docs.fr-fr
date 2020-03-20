---
title: GetCORSystemDirectory, fonction
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178206"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory, fonction
Retourne le répertoire d’installation de l’heure de course de langue commune (CLR) qui est chargé dans le processus. L’annuaire d’installation est entièrement qualifié, par exemple, "c:'windows’microsoft.net’framework’v1.0.3705".  
  
 Cette fonction est déconseillée. Il est remplacé par [l’ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) méthode fournie dans le cadre .NET 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>Paramètres  
 `pbuffer`  
 [out] Un tampon dans lequel le temps d’exécution renvoie une chaîne qui contient le nom entièrement qualifié de l’annuaire d’installation pour le temps d’exécution qui est chargé dans le processus. Si le temps d’exécution n’a pas encore été chargé dans le processus, la fonction renvoie les informations d’annuaire appropriées pour la dernière version du temps d’exécution installé sur l’ordinateur.  
  
 `cchBuffer`  
 [dans] La taille, dans les `pbuffer`octets, de .  
  
 `dwLength`  
 [out] Le nombre de `pbuffer`caractères retournés dans .  
  
## <a name="remarks"></a>Notes   
  
> [!CAUTION]
> N’utilisez pas cette fonction dans les processus qui exécutent la version 4 du CLR. Si une version antérieure du CLR est installée sur l’ordinateur, cette fonction renvoie le répertoire d’installation pour cette version.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
