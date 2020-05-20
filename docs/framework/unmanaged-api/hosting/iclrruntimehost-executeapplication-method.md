---
title: ICLRRuntimeHost::ExecuteApplication, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
ms.openlocfilehash: 924d032c42dca95b253acea167d55dd6e2b811e5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703337"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication, méthode
Utilisé dans les scénarios de déploiement ClickOnce basés sur un manifeste pour spécifier l’application à activer dans un nouveau domaine. Pour plus d’informations sur ces scénarios, consultez [sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzAppFullName`  
 dans Nom complet de l’application, tel que défini pour <xref:System.ApplicationIdentity> .  
  
 `dwManifestPaths`  
 dans Nombre de chaînes contenues dans le `ppwzManifestPaths` tableau.  
  
 `ppwzManifestPaths`  
 [in] Facultatif. Tableau de chaînes qui contient des chemins d’accès de manifeste pour l’application.  
  
 `dwActivationData`  
 dans Nombre de chaînes contenues dans le `ppwzActivationData` tableau.  
  
 `ppwzActivationData`  
 [in] Facultatif. Tableau de chaînes qui contient les données d’activation de l’application, telles que la partie de la chaîne de requête de l’URL pour les applications déployées sur le Web.  
  
 `pReturnValue`  
 à Valeur retournée par le point d’entrée de l’application.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 `ExecuteApplication`est utilisé pour activer des applications ClickOnce dans un domaine d’application nouvellement créé.  
  
 Le `pReturnValue` paramètre de sortie est défini sur la valeur retournée par l’application. Si vous spécifiez une valeur null pour `pReturnValue` , `ExecuteApplication` n’échoue pas, mais elle ne retourne pas de valeur.  
  
> [!IMPORTANT]
> N’appelez pas la méthode [Start méthode](iclrruntimehost-start-method.md) avant d’appeler la `ExecuteApplication` méthode pour activer une application basée sur un manifeste. Si la `Start` méthode est appelée en premier, l’appel de la `ExecuteApplication` méthode échoue.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost, interface](iclrruntimehost-interface.md)
- [SetAppDomainManager, méthode](ihostcontrol-setappdomainmanager-method.md)
- [Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API de déploiement ClickOnce à l’aide du concepteur](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
