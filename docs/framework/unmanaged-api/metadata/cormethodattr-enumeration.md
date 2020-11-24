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
ms.openlocfilehash: 6c3e721c24da217eaf2e8857377359e1c51b7b59
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677010"
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
|`mdPrivate`|Spécifie que le membre est accessible uniquement par le type parent.|  
|`mdFamANDAssem`|Spécifie que le membre est accessible par les sous-types uniquement dans cet assembly.|  
|`mdAssem`|Spécifie que le membre est accessibly par toute personne de l’assembly.|  
|`mdFamily`|Spécifie que le membre est accessible uniquement par type et sous-types.|  
|`mdFamORAssem`|Spécifie que le membre est accessible par les classes dérivées et par d’autres types dans son assembly.|  
|`mdPublic`|Spécifie que le membre est accessible par tous les types ayant accès à la portée.|  
|`mdStatic`|Spécifie que le membre est défini dans le cadre du type plutôt qu’en tant que membre d’une instance.|  
|`mdFinal`|Spécifie que la méthode ne peut pas être substituée.|  
|`mdVirtual`|Spécifie que la méthode peut être substituée.|  
|`mdHideBySig`|Spécifie que la méthode masque par nom et par signature, plutôt que simplement par nom.|  
|`mdVtableLayoutMask`|Spécifie la disposition de la table virtuelle.|  
|`mdReuseSlot`|Spécifie que l’emplacement utilisé pour cette méthode dans la table virtuelle doit être réutilisé. Il s’agit de la valeur par défaut.|  
|`mdNewSlot`|Spécifie que la méthode obtient toujours un nouvel emplacement dans la table virtuelle.|  
|`mdCheckAccessOnOverride`|Spécifie que la méthode peut être substituée par les mêmes types auxquels elle est visible.|  
|`mdAbstract`|Spécifie que la méthode n’est pas implémentée.|  
|`mdSpecialName`|Spécifie que la méthode est spéciale et que son nom décrit comment.|  
|`mdPinvokeImpl`|Spécifie que l’implémentation de la méthode est transférée à l’aide de PInvoke.|  
|`mdUnmanagedExport`|Spécifie que la méthode est une méthode managée exportée vers du code non managé.|  
|`mdReservedMask`|Réservé à un usage interne par la common language runtime.|  
|`mdRTSpecialName`|Spécifie que le common language runtime doit vérifier l’encodage du nom de la méthode.|  
|`mdHasSecurity`|Spécifie que la méthode est associée à la sécurité.|  
|`mdRequireSecObject`|Spécifie que la méthode appelle une autre méthode contenant du code de sécurité.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
