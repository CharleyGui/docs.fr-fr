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
ms.openlocfilehash: ffbc9a10ff48b3dfd59b95c0f6b9ecab80b6a49c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007882"
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
|`dclAssert`|Le code appelant peut accéder à la ressource identifiée par l’objet d’autorisation actuel, même si les appelants situés plus haut dans la pile n’ont pas reçu l’autorisation d’accéder à la ressource|  
|`dclDeny`|La possibilité d’accéder à la ressource spécifiée par l’objet d’autorisation actuel est refusée aux appelants, même s’ils ont reçu l’autorisation d’y accéder.|  
|`dclPermitOnly`|Seules les ressources spécifiées par l’objet d’autorisation sont accessibles, même si le code a reçu l’autorisation d’accéder à d’autres ressources.|  
|`dclLinktimeCheck`|L’appelant immédiat doit avoir reçu l’autorisation spécifiée pour une période donnée.|  
|`dclInheritanceCheck`|La classe dérivée qui hérite d’une autre classe ou qui substitue une méthode doit avoir reçu l’autorisation spécifiée.|  
|`dclRequestMinimum`|L’appelant peut demander les autorisations minimales requises pour l’exécution du code. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclRequestOptional`|L’appelant peut demander des autorisations supplémentaires qui sont facultatives (non requises pour s’exécuter). Cette requête refuse implicitement toutes les autres autorisations qui ne sont pas spécifiquement demandées. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclRequestRefuse`|La demande d’autorisation de l’appelant qui peut être utilisée à l’utilisation incorrecte ne sera pas accordée. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclPrejitGrant`|Réservé.|  
|`dclPrejitDenied`|Réservé.|  
|`dclNonCasDemand`|Réservé.|  
|`dclNonCasLinkDemand`|L’appelant immédiat doit avoir reçu l’autorisation spécifiée.|  
|`dclNonCasInheritance`|Réservé.|  
|`dclLinkDemandChoice`|Réservé.|  
|`dclInheritanceDemandChoice`|Réservé.|  
|`dclDemandChoice`|Réservé.|  
|`dclMaximumValue`|Réservé.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
