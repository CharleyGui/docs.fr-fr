---
title: CorRefToDefCheck, énumération
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e6c3c9b842bd823e8975661964480fd801779b2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450124"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck, énumération
Spécifie des indicateurs pour contrôler les éléments référencés qui sont convertis en définitions afin d'optimiser le code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDRefToDefDefault`|Spécifie que les références de type et les références de membre doivent être converties en définitions. Il s’agit de la valeur par &#124; défaut (`MDTypeRefToDef` `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Spécifie que tous les éléments référencés doivent être convertis en définitions.|  
|`MDRefToDefNone`|Spécifie qu’aucun élément référencé ne doit être converti en définitions.|  
|`MDTypeRefToDef`|Spécifie que seules les références de type doivent être converties en définitions de type.|  
|`MDMemberRefToDef`|Spécifie que seules les références de membre doivent être converties en définitions. Autrement dit, les références de membre doivent être converties en définitions de méthode ou définitions de champ.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
