---
title: CorAssemblyFlags, énumération
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: 615c4ac95ab777e8081e630cafb6671e64dea78a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718980"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags, énumération

Contient des valeurs qui décrivent les métadonnées appliquées à une compilation d'assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`afPublicKey`|Indique que la référence d’assembly contient la clé publique déhachée complète.|  
|`afPA_None`|Indique que l’architecture du processeur n’est pas spécifiée.|  
|`afPA_MSIL`|Indique que l’architecture du processeur est neutre (PE32).|  
|`afPA_x86`|Indique que l’architecture du processeur est x86 (PE32).|  
|`afPA_IA64`|Indique que l’architecture du processeur est Itanium (PE32 +).|  
|`afPA_AMD64`|Indique que l’architecture du processeur est AMD x64 (PE32 +).|  
|`afPA_ARM`|Indique que l’architecture du processeur est ARM (PE32).|  
|`afPA_NoPlatform`|Indique que l’assembly est un assembly de référence ; autrement dit, elle s’applique à n’importe quelle architecture, mais ne peut pas être exécutée sur n’importe quelle architecture. Ainsi, l’indicateur est le même que `afPA_Mask` .|  
|`afPA_Specified`|Indique que les indicateurs de l’architecture du processeur doivent être propagés à l' `AssemblyRef` enregistrement.|  
|`afPA_Mask`|Masque qui décrit l’architecture du processeur.|  
|`afPA_FullMask`|Spécifie que la description de l’architecture du processeur est incluse.|  
|`afPA_Shift`|Indique un nombre de décalages dans les indicateurs d’architecture de processeur vers et à partir de l’index.|  
|`afEnableJITcompileTracking`|Indique la valeur correspondante à partir du <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> de <xref:System.Diagnostics.DebuggableAttribute> .|  
|`afDisableJITcompileOptimizer`|Indique la valeur correspondante à partir du <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> de <xref:System.Diagnostics.DebuggableAttribute> .|  
|`afRetargetable`|Indique que l’assembly peut être reciblé au moment de l’exécution vers un assembly d’un autre serveur de publication.|  
|`afContentType_Mask`|Masque qui décrit le type de contenu.|  
|`afContentType_Default`|Indique le type de contenu par défaut.|  
|`afContentType_WindowsRuntime`|Indique le type de contenu Windows Runtime.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
