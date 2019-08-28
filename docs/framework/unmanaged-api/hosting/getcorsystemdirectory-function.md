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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d30384ea8b9ff4eee41abd43ae39486f770039e7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041421"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory, fonction
Retourne le répertoire d’installation du common language runtime (CLR) qui est chargé dans le processus. Le répertoire d’installation est complet, par exemple, «c:\Windows\Microsoft.NET\Framework\v1.0.3705».  
  
 Cette fonction est déconseillée. Elle est remplacée par la méthode [ICLRRuntimeInfo:: GetRuntimeDirectory,](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) fournie dans le .NET Framework 4.  
  
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
 à Mémoire tampon dans laquelle le runtime retourne une chaîne qui contient le nom qualifié complet du répertoire d’installation du runtime chargé dans le processus. Si le runtime n’a pas encore été chargé dans le processus, la fonction retourne les informations de répertoire appropriées pour la version la plus récente du runtime installée sur l’ordinateur.  
  
 `cchBuffer`  
 dans Taille, en octets, de `pbuffer`.  
  
 `dwLength`  
 à Nombre de caractères retournés `pbuffer`dans.  
  
## <a name="remarks"></a>Notes  
  
> [!CAUTION]
> N’utilisez pas cette fonction dans les processus qui exécutent la version 4 du CLR. Si une version antérieure du CLR est installée sur l’ordinateur, cette fonction retourne le répertoire d’installation de cette version.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
