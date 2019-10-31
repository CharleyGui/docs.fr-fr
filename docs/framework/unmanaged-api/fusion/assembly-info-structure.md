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
ms.openlocfilehash: a43d5e15c02a97ff10a6a5afd439cadebb6b33d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109212"
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
|`dwAssemblyFlags`|Indicateurs qui indiquent les détails de l’installation de l’assembly. Les valeurs suivantes sont prises en charge :<br /><br /> -La valeur ASSEMBLYINFO_FLAG_INSTALLED, qui indique que l’assembly est installé. La version actuelle du .NET Framework affecte toujours la valeur à `dwAssemblyFlags`.<br />-La valeur ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, qui indique que l’assembly est un résident de charge utile. La version actuelle de la .NET Framework ne définit jamais `dwAssemblyFlags` à cette valeur.|  
|`uliAssemblySizeInKB`|Taille totale, en kilo-octets, des fichiers que l’assembly contient.|  
|`pszCurrentAssemblyPathBuf`|Pointeur vers une mémoire tampon de chaîne qui contient le chemin d’accès actuel au fichier manifeste. Le chemin d’accès doit se terminer par un caractère null.|  
|`cchBuf`|Nombre de caractères larges, y compris la marque de fin null, que `pszCurrentAssemblyPathBuf` contient.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de fusion](fusion-structures.md)
- [Global Assembly Cache](../../app-domains/gac.md)
