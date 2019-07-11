---
title: QualifierSet_Delete (fonction) (référence des API non managées)
description: La fonction QualifierSet_Delete supprime un qualificateur par nom.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 956abe8ddf8075b7b8f8c057db0aa7187982e1d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782612"
---
# <a name="qualifiersetdelete-function"></a>QualifierSet_Delete (fonction)
Supprime un qualificateur spécifié par nom.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre n’est pas utilisé.

`ptr`   
[in] Un pointeur vers un [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

`wszName`   
[in] Le nom du qualificateur à supprimer.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Le paramètre `wszName` n’est pas valide. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | La suppression de ce qualificateur est non conforme. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Le qualificateur spécifié est introuvable. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | La valeur de remplacement locale a été supprimé et le qualificateur d’origine à partir de l’objet parent a repris l’étendue. |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) (méthode).

En raison des règles de propagation d’un qualificateur de nom, un qualificateur particulier peut ont été hérité d’un autre objet et simplement de substitution dans la classe en cours ou l’instance. Dans ce cas, le `QualifierSet_Delete` méthode réinitialise le qualificateur à sa valeur d’origine hérité. Dans ce cas, la fonction retourne le code d’état `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
