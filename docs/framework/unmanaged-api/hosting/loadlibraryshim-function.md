---
title: LoadLibraryShim, fonction
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
ms.openlocfilehash: 1759ee2ecf08322b745a4f80a62b24596c4504cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123249"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim, fonction
Charge une version spécifiée d’une DLL qui est incluse dans le package redistribuable .NET Framework.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4. Utilisez la méthode [ICLRRuntimeInfo :: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szDllName`  
 dans Chaîne se terminant par zéro qui représente le nom de la DLL à charger à partir de la bibliothèque de .NET Framework.  
  
 `szVersion`  
 dans Chaîne se terminant par zéro qui représente la version de la DLL à charger. Si `szVersion` a la valeur null, la version sélectionnée pour le chargement est la version la plus récente de la DLL spécifiée inférieure à la version 4. Autrement dit, toutes les versions égales ou supérieures à la version 4 sont ignorées si `szVersion` a la valeur null, et si aucune version antérieure à la version 4 n’est installée, le chargement de la DLL échoue. Cela permet de s’assurer que l’installation du .NET Framework 4 n’affecte pas les applications ou les composants préexistants. Consultez l’entrée [in-proc SxS and Migration démarrage rapide](https://go.microsoft.com/fwlink/?LinkId=200329) dans le blog de l’équipe CLR.  
  
 `pvReserved`  
 Réservé à un usage ultérieur.  
  
 `phModDll`  
 à Pointeur vers le handle du module.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|CLR_E_SHIM_RUNTIMELOAD|Le chargement de `szDllName` nécessite le chargement du common language runtime (CLR) et la version nécessaire du CLR ne peut pas être chargée.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est utilisée pour charger les dll incluses dans le package redistribuable .NET Framework. Il ne charge pas les dll générées par l’utilisateur.  
  
> [!NOTE]
> À partir de la version 2,0 de .NET Framework, le chargement de fusion. dll entraîne le chargement du CLR. Cela est dû au fait que les fonctions de fusion. dll sont désormais des wrappers dont les implémentations sont fournies par le Runtime.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
