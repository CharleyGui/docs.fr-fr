---
title: "Comment : utiliser le fournisseur de rôle du Gestionnaire d'autorisations ASP.NET avec un service"
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 009b96defdf27591ddb98afaa684745b5fcbe0d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184811"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Comment : utiliser le fournisseur de rôle du Gestionnaire d'autorisations ASP.NET avec un service
Lorsque ASP.NET héberge un service Web, vous pouvez intégrer le gestionnaire d’autorisation dans la demande pour fournir une autorisation au service. Le Gestionnaire d'autorisations permet à un développeur d'applications de définir des opérations individuelles qui peuvent être regroupées pour former des tâches. Un administrateur peut autoriser ensuite que les rôles exécutent des tâches spécifiques ou des opérations individuelles. Le Gestionnaire d’autorisations fournit un outil d’administration sous la forme d’un composant logiciel enfichable MMC (Microsoft Management Console) pour gérer des rôles, des tâches, des opérations et des utilisateurs. Les administrateurs configurent un magasin de stratégie du Gestionnaire d'autorisations dans un fichier XML, Active Directory, ou dans un magasin Active Directory en mode application (ADAM).  
  
 Le gestionnaire de l’autorisation est intégré à la demande en configurant le gestionnaire d’autorisation ASP.NET fournisseur de rôle pour l’application ASP.NET qui héberge le service Web. Comme d’autres fournisseurs de rôles ASP.NET, le gestionnaire d’autorisation ASP.NET fournisseur `providers` de rôles est configuré à l’aide de l’élément <>.  
  
 L'exemple de code suivant représente une partie d'un fichier de configuration pour un service Web qui intègre le Gestionnaire d'autorisations dans l'application.  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 Pour plus d’informations sur l’intégration d’un fournisseur de rôles ASP.NET avec une application WCF, voir [Comment: Utilisez le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Pour plus d’informations sur l’utilisation de l’autorisation Manager avec ASP.NET, voir [Comment: Use Authorization Manager (AzMan) avec ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).  
  
## <a name="see-also"></a>Voir aussi

- [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
