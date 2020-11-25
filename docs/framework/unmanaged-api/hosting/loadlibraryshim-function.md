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
ms.openlocfilehash: d5e9ba0023b6516eb6190f32bc65b2b8b6af79f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727560"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim, fonction

Charge une version spécifiée d’une DLL qui est incluse dans le package redistribuable .NET Framework.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4. Utilisez la méthode [ICLRRuntimeInfo :: LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) à la place.  
  
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
 dans Chaîne se terminant par zéro qui représente la version de la DLL à charger. Si `szVersion` a la valeur null, la version sélectionnée pour le chargement est la version la plus récente de la DLL spécifiée inférieure à la version 4. Autrement dit, toutes les versions égales ou supérieures à la version 4 sont ignorées si `szVersion` a la valeur null, et si aucune version antérieure à la version 4 n’est installée, le chargement de la DLL échoue. Cela permet de s’assurer que l’installation du .NET Framework 4 n’affecte pas les applications ou les composants préexistants. Consultez l’entrée [in-proc SxS and Migration démarrage rapide](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) dans le blog de l’équipe CLR.  
  
 `pvReserved`  
 Réservé à un usage ultérieur.  
  
 `phModDll`  
 à Pointeur vers le handle du module.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|CLR_E_SHIM_RUNTIMELOAD|Le chargement `szDllName` requiert le chargement du Common Language Runtime (CLR) et la version nécessaire du CLR ne peut pas être chargée.|  
  
## <a name="remarks"></a>Remarques  

 Cette fonction est utilisée pour charger les dll incluses dans le package redistribuable .NET Framework. Il ne charge pas les dll générées par l’utilisateur.  
  
> [!NOTE]
> À partir de la version .NET Framework 2,0, le chargement de Fusion.dll entraîne le chargement du CLR. Cela est dû au fait que les fonctions de Fusion.dll sont désormais des wrappers dont les implémentations sont fournies par le Runtime.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
