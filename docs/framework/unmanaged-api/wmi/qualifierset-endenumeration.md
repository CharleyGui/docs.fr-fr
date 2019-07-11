---
title: QualifierSet_EndEnumeration (fonction) (référence des API non managées)
description: La fonction QualifierSet_EndEnumeration met fin à une énumération.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 206d6448835b60c55b378636ff5daa5fa4f8b5d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782594"
---
# <a name="qualifiersetendenumeration-function"></a>QualifierSet_EndEnumeration (fonction)
Met fin à l’énumération commencée avec un appel à la [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) (fonction).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre n’est pas utilisé.

`ptr`   
[in] Un pointeur vers un [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

## <a name="return-value"></a>Valeur de retour

La valeur suivante est retournée par cette fonction est définie dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez la définir en tant que constante dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) (méthode).

Cet appel est recommandé, mais pas obligatoire. Il libère immédiatement les ressources associées à l’énumération.

## <a name="requirements"></a>Configuration requise  

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
**En-tête :** WMINet_Utils.idl  
  
**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
