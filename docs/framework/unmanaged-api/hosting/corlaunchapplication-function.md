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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64527221e81569bf08a3cfd34a66681725755a55
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490540"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication, fonction
Démarre l’application sur le chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et autres données d’application.  
  
 Cette fonction a été déconseillée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Une valeur de la [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) énumération qui spécifie le type d’hôte qui lance l’application.  
  
 `pwzAppFullName`  
 [in] Le nom complet de l’application qui est lancée.  
  
 `dwManifestPaths`  
 [in] Le nombre de chemins d’accès de manifestes pour l’application.  
  
 `ppwzManifestPaths`  
 [in] Tableau de chaînes, dont chacun spécifie un chemin d’accès à un manifeste d’application qui est lancée.  
  
 `dwActivationData`  
 [in] Le nombre d’éléments de données d’activation pour l’application qui est lancée.  
  
 `ppwzActivationData`  
 [in] Tableau de chaînes, chacune d’elles étant un élément de données d’activation pour l’application qui est lancée.  
  
 `lpProcessInformation`  
 [out] Pointeur vers les informations sur le processus dans lequel l’application a été chargée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
