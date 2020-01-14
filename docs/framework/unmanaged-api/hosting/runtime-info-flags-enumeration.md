---
title: RUNTIME_INFO_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
ms.openlocfilehash: 9d505b917c343c40c7fa2a7aecf3466578ae0a8d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936638"
---
# <a name="runtime_info_flags-enumeration"></a>RUNTIME_INFO_FLAGS, énumération
Contient des valeurs qui indiquent les informations relatives au common language runtime (CLR) qui doivent être retournées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Indique que les informations de répertoire ne doivent pas être incluses.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Indique que les informations de version ne doivent pas être incluses.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Indique qu’une boîte de dialogue d’erreur ne doit pas s’afficher en cas d’échec.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Indique que les effets de l’appel de la fonction [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) avec l’indicateur SEM_FAILCRITICALERRORS doivent être substitués. Autrement dit, une boîte de dialogue d’installation doit s’afficher en cas d’échec, au lieu d’être supprimée.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Indique une demande d’informations sur une version compatible AMD-64 du Runtime.|  
|`RUNTIME_INFO_REQUEST_IA64`|Indique une demande d’informations sur une version compatible IA-64 du Runtime.|  
|`RUNTIME_INFO_REQUEST_X86`|Indique une demande d’informations sur une version compatible x86 du Runtime.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Indique que les informations de mise à niveau de version doivent être incluses.|  
  
## <a name="remarks"></a>Notes  
 Les indicateurs d’architecture de la plateforme suivants ne peuvent être spécifiés qu’une seule fois et ne peuvent pas être combinés :  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
