---
title: Fonction QualifierSet_Get (référence des API non managées)
description: La fonction QualifierSet_Get obtient un qualificateur nommé.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 751694985248346187eff016ef7a4a8054cb1212
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798303"
---
# <a name="qualifierset_get-function"></a>QualifierSet_Get fonction)
Obtient le qualificateur nommé spécifié.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`   
dans Ce paramètre n’est pas utilisé.

`ptr`   
dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`   
dans Nom du qualificateur dont la valeur est demandée.

`lFlags`   
[in] Réservée. Ce paramètre doit avoir la valeur 0.

`pVal`   
à En cas de réussite, le type et la valeur corrects pour le qualificateur. Si la fonction échoue, le `VARIANT` pointé par `pVal` n’est pas modifié. Si ce paramètre est `null`, le paramètre est ignoré.

`plFlavor`   
à Pointeur vers une valeur de type LONG qui reçoit les bits de version de qualificateur pour le qualificateur demandé. Si les informations de version ne sont pas souhaitées, `null`ce paramètre peut avoir la la. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Le qualificateur spécifié n’existe pas. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: obtenir](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) .

## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
