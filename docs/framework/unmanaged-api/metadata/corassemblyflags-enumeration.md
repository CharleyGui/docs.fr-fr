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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43bfec471fbcfc481e178f6610e0318e9538ee34
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025771"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags, énumération
Contient des valeurs qui décrivent les métadonnées appliquées à une compilation d'assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`afPublicKey`|Indique que la référence d’assembly conserve la clé publique complète et non hachée.|  
|`afPA_None`|Indique que l’architecture de processeur n’est pas spécifiée.|  
|`afPA_MSIL`|Indique que l’architecture de processeur est neutre (PE32 +).|  
|`afPA_x86`|Indique que l’architecture de processeur est x86 (PE32 +).|  
|`afPA_IA64`|Indique que l’architecture de processeur est Itanium (PE32 +).|  
|`afPA_AMD64`|Indique que l’architecture de processeur est AMD X64 (PE32 +).|  
|`afPA_ARM`|Indique que l’architecture de processeur ARM (PE32 +).|  
|`afPA_NoPlatform`|Indique que l’assembly est un assembly de référence ; Autrement dit, elle s’applique à n’importe quelle architecture mais ne peut pas s’exécuter sur n’importe quelle architecture. Par conséquent, l’indicateur est identique à `afPA_Mask`.|  
|`afPA_Specified`|Indique que les indicateurs de l’architecture processeur doivent être propagés à la `AssemblyRef` enregistrement.|  
|`afPA_Mask`|Masque qui décrit l’architecture de processeur.|  
|`afPA_FullMask`|Spécifie que la description d’architecture de processeur est incluse.|  
|`afPA_Shift`|Indique une valeur du décalage dans les indicateurs de l’architecture processeur vers et à partir de l’index.|  
|`afEnableJITcompileTracking`|Indique la valeur correspondante à partir de la <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> de la <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Indique la valeur correspondante à partir de la <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> de la <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Indique que l’assembly peut être reciblé au moment de l’exécution à un assembly à partir d’un éditeur différent.|  
|`afContentType_Mask`|Masque qui décrit le type de contenu.|  
|`afContentType_Default`|Indique le type de contenu par défaut.|  
|`afContentType_WindowsRuntime`|Indique le type de contenu de Windows Runtime.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
