---
title: FUSION_INSTALL_REFERENCE, structure
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec18d5d5a6574cb0e08a6c4d6eaedcbcbf6886cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759368"
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE, structure
Représente une référence par une application à un assembly de l’application a installé dans le global assembly cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`cbSize`|La taille de la structure en octets.|  
|`dwFlags`|Réservé pour une extensibilité future. Cette valeur doit être 0 (zéro).|  
|`guidScheme`|L’entité qui ajoute la référence. Ce champ peut avoir une des valeurs suivantes :<br /><br /> -   FUSION_REFCOUNT_MSI_GUID: L’assembly est référencé par une application qui a été installée à l’aide de Microsoft Windows Installer. Le `szIdentifier` champ est défini sur `MSI`et le `szNonCanonicalData` champ est défini sur `Windows Installer`. Ce schéma est utilisé pour les assemblys côte à côte de Windows.<br />-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: L’assembly est référencé par une application qui s’affiche dans le **Ajout/Suppression de programmes** interface. Le `szIdentifier` champ fournit le jeton qui enregistre l’application avec le **Ajout/Suppression de programmes** interface.<br />-   FUSION_REFCOUNT_FILEPATH_GUID: L’assembly est référencé par une application qui est représentée par un fichier dans le système de fichiers. Le `szIdentifier` champ fournit le chemin d’accès à ce fichier.<br />-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: L’assembly est référencé par une application qui est représentée uniquement par une chaîne opaque. Le `szIdentifier` champ fournit cette chaîne opaque. Le global assembly cache ne vérifie pas l’existence de références opaques lorsque vous supprimez cette valeur.<br />-   FUSION_REFCOUNT_OSINSTALL_GUID: Cette valeur est réservée.|  
|`szIdentifier`|Une chaîne unique qui identifie l’application qui a installé l’assembly dans le global assembly cache. Sa valeur dépend de la valeur de la `guidScheme` champ.|  
|`szNonCanonicalData`|Chaîne qui est interprétée uniquement par l’entité qui ajoute la référence. Le global assembly cache stocke cette chaîne, mais ne l’utilise pas.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
