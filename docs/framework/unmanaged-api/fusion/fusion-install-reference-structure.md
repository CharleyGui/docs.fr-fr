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
ms.openlocfilehash: 3859752fd92a76f3fef1ceced0e792109b65106a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108279"
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
|`guidScheme`|Entité qui ajoute la référence. Ce champ peut prendre l’une des valeurs suivantes :<br /><br /> -FUSION_REFCOUNT_MSI_GUID : l’assembly est référencé par une application qui a été installée à l’aide de l’Microsoft Windows Installer. Le champ `szIdentifier` est défini sur `MSI`et le champ `szNonCanonicalData` est défini sur `Windows Installer`. Ce schéma est utilisé pour les assemblys côte à côte Windows.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID : l’assembly est référencé par une application qui s’affiche dans l’interface **Ajout/suppression de programmes** . Le champ `szIdentifier` fournit le jeton qui inscrit l’application auprès de l’interface **Ajout/suppression de programmes** .<br />-FUSION_REFCOUNT_FILEPATH_GUID : l’assembly est référencé par une application qui est représentée par un fichier dans le système de fichiers. Le champ `szIdentifier` fournit le chemin d’accès à ce fichier.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID : l’assembly est référencé par une application qui est représentée uniquement par une chaîne opaque. Le champ `szIdentifier` fournit cette chaîne opaque. La Global Assembly Cache ne vérifie pas l’existence de références opaques lorsque vous supprimez cette valeur.<br />-FUSION_REFCOUNT_OSINSTALL_GUID : cette valeur est réservée.|  
|`szIdentifier`|Chaîne unique qui identifie l’application qui a installé l’assembly dans le Global Assembly Cache. Sa valeur dépend de la valeur du champ `guidScheme`.|  
|`szNonCanonicalData`|Chaîne qui est comprise uniquement par l’entité qui ajoute la référence. Le Global Assembly Cache stocke cette chaîne, mais ne l’utilise pas.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de fusion](fusion-structures.md)
- [Global Assembly Cache](../../app-domains/gac.md)
