---
title: CorOpenFlags, énumération
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
ms.openlocfilehash: ad582fc2fd1bd1d2fc9d5a0d483fdb3a51309a10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436505"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags, énumération
Contient des valeurs d'indicateurs qui contrôlent le comportement des métadonnées après ouverture des fichiers manifeste.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`ofRead`|Indique que le fichier doit être ouvert en lecture seule.|  
|`ofWrite`|Indique que le fichier doit être ouvert en écriture.<br /><br /> Si vous utilisez l'indicateur `ofWrite` lors de l'ouverture d'un fichier .winmd, vous devez aussi passer l'indicateur `ofNoTransform`.|  
|`ofReadWriteMask`|Un masque pour la lecture et l'écriture.|  
|`ofCopyMemory`|Indique que le fichier doit être lu en mémoire. Les métadonnées doivent gérer leur propre copie.|  
|`ofCacheImage`|Obsolète. Cet indicateur est ignoré.|  
|`ofManifestMetadata`|Obsolète. Cet indicateur est ignoré.|  
|`ofReadOnly`|Indique que le fichier doit être ouvert pour la lecture et qu’un appel à `QueryInterface` pour une [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) ne peut pas être effectué.|  
|`ofTakeOwnership`|Indique que la mémoire a été allouée à l’aide d’un appel à [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) et sera libérée par les métadonnées.|  
|`ofNoTypeLib`|Obsolète. Cet indicateur est ignoré.|  
|`ofNoTransform`|Indique que les transformations automatiques de fichiers .winmd doivent être désactivées. En d'autres termes, la projection d'un type Windows Runtime vers un type .NET Framework doit être désactivée. Pour plus d’informations, consultez [Windows Runtime et le CLR-sous le capot avec .net et le Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).|  
|`ofReserved1`|Réservé à un usage interne.|  
|`ofReserved2`|Réservé à un usage interne.|  
|`ofReserved`|Réservé à un usage interne.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
