---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: d3625865484568746888ef0638d9a8501e610bef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273202"
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior

ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe ServiceAuthorizationBehavior ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe ServiceAuthorizationBehavior a les propriétés suivantes :  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur qui contrôle si le service essaie d'emprunter l'identité à l'aide des informations d'identification fournies par le message entrant.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Principal de sécurité utilisée pour effectuer les opérations sur le serveur.  
  
### <a name="roleprovider"></a>RoleProvider  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Nom du fournisseur de rôles ASP.NET.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Gestionnaire d'autorisations utilisé pour l'autorisation personnalisée.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
