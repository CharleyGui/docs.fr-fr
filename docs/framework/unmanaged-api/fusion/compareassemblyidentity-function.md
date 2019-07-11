---
title: CompareAssemblyIdentity, fonction
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55d4e936c8b732e4cc4a60df8c11b37c86c4a415
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778484"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity, fonction
Compare deux identités d’assembly pour déterminer s’ils sont équivalents.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzAssemblyIdentity1`  
 [in] Identité de l’assembly premier dans la comparaison textuelle.  
  
 `fUnified1`  
 [in] Un indicateur booléen qui indique l’unification de spécifié par l’utilisateur pour `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [in] Identité de l’assembly deuxième dans la comparaison textuelle.  
  
 `fUnified2`  
 [in] Un indicateur booléen qui indique l’unification de spécifié par l’utilisateur pour `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] Indicateur booléen qui indique si les deux assemblys sont équivalentes.  
  
 `pResult`  
 [out] Un [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) énumération qui contient des informations détaillées sur la comparaison.  
  
## <a name="return-value"></a>Valeur de retour  
 `pfEquivalent` Retourne une valeur booléenne qui indique si les deux assemblys sont équivalentes. `pResult` Retourne une de la `AssemblyComparisonResult` valeurs, afin de donner une raison plus détaillée de la valeur de `pfEquivalent`.  
  
## <a name="remarks"></a>Notes  
 `CompareAssemblyIdentity` vérifie si `pwzAssemblyIdentity1` et `pwzAssemblyIdentity2` sont équivalentes. `pfEquivalent` a la valeur `true` sous un ou plusieurs des conditions suivantes :  
  
- Les identités de deux assembly sont équivalentes. Pour les assemblys à nom fort, l’équivalence implique le nom de l’assembly, version, jeton de clé publique et culture sont identiques. Pour les assemblys simplement nommés, l’équivalence implique une correspondance sur le nom de l’assembly et la culture.  
  
- Les deux identités d’assembly font référence aux assemblys qui s’exécutent sur le .NET Framework. Cette condition retourne `true` même si les numéros de version d’assembly ne correspondent pas.  
  
- Les deux assemblys ne sont pas des assemblys managés, mais `fUnified1` ou `fUnified2` a été défini sur `true`.  
  
 Le `fUnified` indicateur indique que tous les numéros de version jusqu'à le numéro de version de l’assembly de nom fort sont considérés comme équivalents à l’assembly de nom fort. Par exemple, si la valeur de `pwzAssemblyIndentity1` est « MyAssembly, version = 3.0.0.0, culture = neutral, publicKeyToken =... » et la valeur de `fUnified1` est `true`, cela indique que toutes les versions de MyAssembly à partir de la version 0.0.0.0 à 3.0.0.0 doivent être traitées comme étant équivalentes. Dans ce cas, si `pwzAssemblyIndentity2` fait référence au même assembly que `pwzAssemblyIndentity1`, sauf qu’il a un numéro de version inférieure, `pfEquivalent` est défini sur `true`. Si `pwzAssemblyIdentity2` fait référence à un numéro de version supérieur, `pfEquivalent` a la valeur `true` uniquement si la valeur de `fUnified2` est `true`.  
  
 Le `pResult` paramètre inclut des informations spécifiques sur la raison pour laquelle les deux assemblys sont considérés comme équivalents ou pas. Pour plus d’informations, consultez [AssemblyComparisonResult, énumération](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [AssemblyComparisonResult, énumération](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
