---
title: CorDeclSecurity, énumération
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
ms.openlocfilehash: 98183ed02f8821b7c40852de2d040775d30f2518
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443740"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity, énumération
Spécifie les actions de sécurité qui peuvent être effectuées à l’aide de la sécurité déclarative.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`dclActionMask`|Réservé.|  
|`dclActionNil`|Réservé.|  
|`dclRequest`|Réservé.|  
|`dclDemand`|Tous les appelants figurant plus haut dans la pile des appels doivent disposer de l’autorisation spécifiée par l’objet d’autorisation actuel.|  
|`dclAssert`|The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource|  
|`dclDeny`|The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.|  
|`dclPermitOnly`|Seules les ressources spécifiées par l’objet d’autorisation sont accessibles, même si le code a reçu l’autorisation d’accéder à d’autres ressources.|  
|`dclLinktimeCheck`|The immediate caller is required to have been granted the specified permission for a given period of time.|  
|`dclInheritanceCheck`|The derived class inheriting another class or overriding a method is required to have been granted the specified permission.|  
|`dclRequestMinimum`|The caller can request for the minimum permissions required for code to run. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclRequestOptional`|The caller can request for additional permissions that are optional (not required to run). Cette requête refuse implicitement toutes les autres autorisations qui ne sont pas spécifiquement demandées. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclRequestRefuse`|The caller's request for permissions that might be misused will not be granted. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclPrejitGrant`|Réservé.|  
|`dclPrejitDenied`|Réservé.|  
|`dclNonCasDemand`|Réservé.|  
|`dclNonCasLinkDemand`|L’appelant immédiat doit avoir reçu l’autorisation spécifiée.|  
|`dclNonCasInheritance`|Réservé.|  
|`dclLinkDemandChoice`|Réservé.|  
|`dclInheritanceDemandChoice`|Réservé.|  
|`dclDemandChoice`|Réservé.|  
|`dclMaximumValue`|Réservé.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
