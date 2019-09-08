---
title: Fonction QualifierSet_EndEnumeration (référence des API non managées)
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
ms.openlocfilehash: 2c5a817174ec4c4e4407c19bb1d6d2d852d86dd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798320"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration fonction)
Termine l’énumération commencée par un appel à la fonction [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .  

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
dans Ce paramètre n’est pas utilisé.

`ptr`   
dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

## <a name="return-value"></a>Valeur de retour

La valeur suivante retournée par cette fonction est définie dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez la définir en tant que constante dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) .

Cet appel est recommandé, mais pas obligatoire. Il libère immédiatement les ressources associées à l’énumération.

## <a name="requirements"></a>Configuration requise  

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
**En-tête :** WMINet_Utils.idl  
  
**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
