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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03bc5584d24efa790989f93426251f9f38e65904
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768525"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim, fonction
Charge une version spécifiée d’une DLL qui est incluse dans le package redistribuable .NET Framework.  
  
 Cette fonction a été déconseillée dans le .NET Framework 4. Utilisez le [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) méthode à la place.  
  
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
 [in] Chaîne se terminant par zéro qui représente le nom de la DLL à charger à partir de la bibliothèque .NET Framework.  
  
 `szVersion`  
 [in] Chaîne se terminant par zéro qui représente la version de la DLL à charger. Si `szVersion` est null, la version sélectionnée pour le chargement est la dernière version de la DLL spécifiée est inférieure à la version 4. Autrement dit, toutes les versions égales ou supérieures à la version 4 sont ignorées si `szVersion` a la valeur null, et si aucune version inférieure à la version 4 n’est installé, la DLL ne parvient pas à charger. Il s’agit pour vous assurer que l’installation du .NET Framework 4 n’affecte pas des applications existantes ou des composants. Consultez l’entrée [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) dans le blog de l’équipe CLR.  
  
 `pvReserved`  
 Réservé à un usage ultérieur.  
  
 `phModDll`  
 [out] Un pointeur vers le handle du module.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur de composant COM (Object Model) standard, tel que défini dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|CLR_E_SHIM_RUNTIMELOAD|Le chargement `szDllName` requiert le chargement, le common language runtime (CLR) et la version nécessaire du CLR ne peut pas être chargé.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est utilisée pour charger les DLL qui sont inclus dans le package redistribuable .NET Framework. Il ne charge pas les DLL générées par l’utilisateur.  
  
> [!NOTE]
>  À compter de .NET Framework version 2.0, en chargeant Fusion.dll provoque le CLR à charger. Il s’agit, car les fonctions dans le fichier Fusion.dll sont maintenant des wrappers dont les implémentations sont fournies par le runtime.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
