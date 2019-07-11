---
title: CorMethodAttr, énumération
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff298f73f02f148fc389f389ba86fd9a550998c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781776"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr, énumération
Contient des valeurs qui décrivent les fonctionnalités d’une méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`mdMemberAccessMask`|Spécifie l’accès au membre.|  
|`mdPrivateScope`|Spécifie que le membre ne peut pas être référencé.|  
|`mdPrivate`|Spécifie que le membre est accessible uniquement par le type de parent.|  
|`mdFamANDAssem`|Spécifie que le membre est accessible aux sous-types uniquement dans cet assembly.|  
|`mdAssem`|Spécifie que le membre est accessible par tous les membres de l’assembly.|  
|`mdFamily`|Spécifie que le membre est accessible uniquement par les types et aux sous-types.|  
|`mdFamORAssem`|Spécifie que le membre est accessible par les classes dérivées et par d’autres types dans son assembly.|  
|`mdPublic`|Spécifie que le membre est accessible par tous les types ayant accès à l’étendue.|  
|`mdStatic`|Spécifie que le membre est défini en tant que partie du type plutôt qu’en tant que membre d’une instance.|  
|`mdFinal`|Spécifie que la méthode ne peut pas être substituée.|  
|`mdVirtual`|Spécifie que la méthode peut être substituée.|  
|`mdHideBySig`|Spécifie que la méthode masque par nom et signature, plutôt que simplement par nom.|  
|`mdVtableLayoutMask`|Spécifie la disposition du tableau virtuel.|  
|`mdReuseSlot`|Indique que l’emplacement utilisé pour cette méthode dans la table virtuelle être réutilisé. Il s'agit de la valeur par défaut.|  
|`mdNewSlot`|Spécifie que la méthode obtient toujours un nouvel emplacement dans la table virtuelle.|  
|`mdCheckAccessOnOverride`|Spécifie que la méthode peut être substituée par les mêmes types auxquels elle est visible.|  
|`mdAbstract`|Spécifie que la méthode n’est pas implémentée.|  
|`mdSpecialName`|Spécifie que la méthode est spéciale et que son nom décrit comment.|  
|`mdPinvokeImpl`|Spécifie que l’implémentation de méthode est transférée à l’aide de PInvoke.|  
|`mdUnmanagedExport`|Spécifie que la méthode est une méthode managée exportée vers du code non managé.|  
|`mdReservedMask`|Réservé à un usage interne par le common language runtime.|  
|`mdRTSpecialName`|Spécifie que le common language runtime doit vérifier l’encodage du nom de la méthode.|  
|`mdHasSecurity`|Spécifie que la méthode a une sécurité associée.|  
|`mdRequireSecObject`|Spécifie que la méthode appelle une autre méthode contenant du code de sécurité.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
