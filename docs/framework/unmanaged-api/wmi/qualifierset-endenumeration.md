---
title: fonction QualifierSet_EndEnumeration (référence API non gestion)
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
ms.openlocfilehash: c606580ff2e02c5659c14b134b1a17a65651952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176745"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration, fonction
Termine l’énumération commencée par un appel à la fonction [QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)  

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
[dans] Ce paramètre n’est pas utilisé.

`ptr`[dans] Un pointeur à une instance [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

## <a name="return-value"></a>Valeur retournée

La valeur suivante retournée par cette fonction est définie dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez la définir comme une constante dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à la méthode [IWbemQualifierSet::EndEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)

Cet appel est recommandé, mais pas nécessaire. Il libère immédiatement les ressources associées à l’énumération.

## <a name="requirements"></a>Spécifications  

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
**En-tête:** WMINet_Utils.idl  
  
**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
