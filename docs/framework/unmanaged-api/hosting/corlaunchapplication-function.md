---
title: CorLaunchApplication, fonction
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
ms.openlocfilehash: e01698d2d8491b2496bb664c13dca97964cd1481
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136945"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication, fonction
Démarre l’application au chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et d’autres données d’application.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwClickOnceHost`  
 dans Valeur de l’énumération [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) qui spécifie le type d’hôte qui lance l’application.  
  
 `pwzAppFullName`  
 dans Nom complet de l’application en cours de lancement.  
  
 `dwManifestPaths`  
 dans Nombre de chemins d’accès de manifeste pour l’application.  
  
 `ppwzManifestPaths`  
 dans Tableau de chaînes, chacune spécifiant un chemin d’accès à un manifeste pour l’application en cours de lancement.  
  
 `dwActivationData`  
 dans Nombre d’éléments de données d’activation pour l’application en cours de lancement.  
  
 `ppwzActivationData`  
 dans Tableau de chaînes, chacune d’entre elles étant un élément de données d’activation pour l’application en cours de lancement.  
  
 `lpProcessInformation`  
 à Pointeur vers des informations sur le processus dans lequel l’application a été chargée.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
