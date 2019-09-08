---
title: Fonction PutMethod (référence des API non managées)
description: La fonction PutMethod crée une méthode.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b41cbbade9da5c2095309b9039b8ce2758f6f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798364"
---
# <a name="putmethod-function"></a>PutMethod fonction)
Crée une méthode.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`  
dans Nom de la méthode à créer. 

`lFlags`  
[in] Réservée. Ce paramètre doit avoir la valeur 0.

`pSignatureIn`  
dans Pointeur vers une copie de la [classe système __Parameters](/windows/desktop/WmiSdk/--parameters) qui contient les `in` paramètres de la méthode. Ce paramètre est ignoré s’il est `null`défini sur.  

`pSignatureOut`  
dans  Pointeur vers une copie de la [classe système __Parameters](/windows/desktop/WmiSdk/--parameters) qui contient les `out` paramètres de la méthode. Ce paramètre est ignoré s’il est `null`défini sur.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Le `[in, out]` paramètre de méthode spécifié dans les deux objets *pInSignature* et *pOutSignature* a des qualificateurs différents.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Il manque un paramètre de méthode dans la spécification du qualificateur d' **ID** . |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | La série d’ID qui est assignée aux paramètres de méthode n’est pas consécutive ou ne commence pas à 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | La valeur de retour d’une méthode a un qualificateur d' **ID** . |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Une tentative de réutilisation d’un nom de méthode existant à partir d’une classe parente a été effectuée et les signatures ne correspondent pas. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi. |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemClassObject ::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

Cet appel de méthode est pris en `ptr` charge uniquement si est une définition de classe CIM. La manipulation de méthode n’est pas disponible à partir de pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers des instances CIM.

Les utilisateurs ne peuvent pas créer de méthodes avec des noms commençant ou se terminant par un trait de soulignement. Cela est réservé aux classes système et aux propriétés.

Pour une méthode, les `in` paramètres `out` et sont décrits comme propriétés dans les objets [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Un `[in/out]` paramètre peut être défini en ajoutant la même propriété aux objets pointés par les `pInSignature` paramètres et `pOutSignature` . Dans ce cas, les propriétés partagent la même valeur de qualificateur d' **ID** .

Chaque propriété d’un objet de classe [__Parameters](/windows/desktop/WmiSdk/--parameters) autre `ReturnValue` que doit avoir un qualificateur d' **ID** , une valeur numérique de base zéro qui identifie l’ordre dans lequel les paramètres apparaissent. Deux paramètres ne peuvent pas avoir la même valeur d' **ID** , et aucune valeur d' **ID** ne peut être ignorée. Si l’une des conditions se `PutMethod` produit, `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`la fonction retourne.

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la méthode [IWbemClassObject ::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
