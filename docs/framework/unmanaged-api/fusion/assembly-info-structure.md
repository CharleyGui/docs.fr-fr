---
title: ASSEMBLY_INFO, structure
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
ms.openlocfilehash: 520a24ced6e897d926ce68ef5973ab7083731b9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717628"
---
# <a name="assembly_info-structure"></a>ASSEMBLY_INFO, structure

Contient des informations sur un assembly qui est inscrit dans le Global Assembly Cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`cbAssemblyInfo`|Taille, en octets, de la structure. Ce champ est réservé à une future extensibilité.|  
|`dwAssemblyFlags`|Indicateurs qui indiquent les détails de l’installation de l’assembly. Les valeurs suivantes sont admises :<br /><br /> -La valeur ASSEMBLYINFO_FLAG_INSTALLED, qui indique que l’assembly est installé. La version actuelle de la .NET Framework affecte toujours `dwAssemblyFlags` cette valeur à.<br />-La valeur ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, qui indique que l’assembly est un résident de charge utile. La version actuelle de la .NET Framework ne définit jamais `dwAssemblyFlags` cette valeur.|  
|`uliAssemblySizeInKB`|Taille totale, en kilo-octets, des fichiers que l’assembly contient.|  
|`pszCurrentAssemblyPathBuf`|Pointeur vers une mémoire tampon de chaîne qui contient le chemin d’accès actuel au fichier manifeste. Le chemin d’accès doit se terminer par un caractère null.|  
|`cchBuf`|Nombre de caractères larges, y compris la marque de fin null, qui `pszCurrentAssemblyPathBuf` contient.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de fusion](fusion-structures.md)
- [Global Assembly Cache](../../app-domains/gac.md)
