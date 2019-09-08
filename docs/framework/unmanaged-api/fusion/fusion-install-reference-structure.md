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
ms.openlocfilehash: 9e81fb7c99b9fd03a69456a84f2191770f40121d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795350"
---
# <a name="fusion_install_reference-structure"></a>FUSION_INSTALL_REFERENCE, structure
Représente une référence qu’une application effectue vers un assembly que l’application a installé dans le Global Assembly Cache.  
  
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
|`cbSize`|Taille de la structure en octets.|  
|`dwFlags`|Réservé pour une future extensibilité. Cette valeur doit être 0 (zéro).|  
|`guidScheme`|Entité qui ajoute la référence. Ce champ peut prendre l’une des valeurs suivantes :<br /><br /> - FUSION_REFCOUNT_MSI_GUID: L’assembly est référencé par une application qui a été installée à l’aide de l’Microsoft Windows Installer. Le `szIdentifier` champ a la `MSI`valeur `szNonCanonicalData` et`Windows Installer`le champ a la valeur. Ce schéma est utilisé pour les assemblys côte à côte Windows.<br />- FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: L’assembly est référencé par une application qui s’affiche dans l’interface **Ajout/suppression de programmes** . Le `szIdentifier` champ fournit le jeton qui inscrit l’application auprès de l’interface **Ajout/suppression de programmes** .<br />- FUSION_REFCOUNT_FILEPATH_GUID: L’assembly est référencé par une application qui est représentée par un fichier dans le système de fichiers. Le `szIdentifier` champ fournit le chemin d’accès à ce fichier.<br />- FUSION_REFCOUNT_OPAQUE_STRING_GUID: L’assembly est référencé par une application qui est représentée uniquement par une chaîne opaque. Le `szIdentifier` champ fournit cette chaîne opaque. La Global Assembly Cache ne vérifie pas l’existence de références opaques lorsque vous supprimez cette valeur.<br />- FUSION_REFCOUNT_OSINSTALL_GUID: Cette valeur est réservée.|  
|`szIdentifier`|Chaîne unique qui identifie l’application qui a installé l’assembly dans le Global Assembly Cache. Sa valeur dépend de la valeur du `guidScheme` champ.|  
|`szNonCanonicalData`|Chaîne qui est comprise uniquement par l’entité qui ajoute la référence. Le Global Assembly Cache stocke cette chaîne, mais ne l’utilise pas.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de fusion](fusion-structures.md)
- [Global Assembly Cache](../../app-domains/gac.md)
