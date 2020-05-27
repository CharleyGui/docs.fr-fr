---
title: ValidatorFlags, énumération
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
ms.openlocfilehash: d5eb225241f597baf7a0a5584f4aaf8bf8411ea2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009468"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags, énumération
Contient des valeurs qui indiquent le type de validation qui doit être effectuée dans un appel à la méthode [ICLRValidator :: Validate](iclrvalidator-validate-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|Spécifie que seul le langage MSIL (Microsoft Intermediate Language) dans le fichier exécutable doit être validé.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Spécifie que seul le format du fichier exécutable doit être validé.|  
|`VALIDATOR_EXTRA_VERBOSE`|Spécifie que tous les types de validation doivent être effectués et signalés sur.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Spécifie que le format du fichier exécutable ne doit pas être validé.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Spécifie que les messages d’erreur de validation doivent inclure les lignes de code source qui génèrent des erreurs de validation. La valeur de ce champ n’est pas valide dans la version 2,0 de .NET Framework.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** IValidator. idl, IValidator. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRErrorReportingManager, interface](iclrerrorreportingmanager-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
