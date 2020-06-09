---
title: "Comment : utiliser le fournisseur de rôle du Gestionnaire d'autorisations ASP.NET avec un service"
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 7c1076671512b33f115950cad684fba0b514abe9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595334"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Comment : utiliser le fournisseur de rôle du Gestionnaire d'autorisations ASP.NET avec un service
Quand ASP.NET héberge un service Web, vous pouvez intégrer le gestionnaire d’autorisations dans l’application pour fournir une autorisation au service. Le Gestionnaire d'autorisations permet à un développeur d'applications de définir des opérations individuelles qui peuvent être regroupées pour former des tâches. Un administrateur peut autoriser ensuite que les rôles exécutent des tâches spécifiques ou des opérations individuelles. Le Gestionnaire d’autorisations fournit un outil d’administration sous la forme d’un composant logiciel enfichable MMC (Microsoft Management Console) pour gérer des rôles, des tâches, des opérations et des utilisateurs. Les administrateurs configurent un magasin de stratégie du Gestionnaire d'autorisations dans un fichier XML, Active Directory, ou dans un magasin Active Directory en mode application (ADAM).  
  
 Le gestionnaire d’autorisations est intégré à l’application en configurant le fournisseur de rôle ASP.NET du gestionnaire d’autorisations pour l’application ASP.NET qui héberge le service Web. Comme les autres fournisseurs de rôle ASP.NET, le fournisseur de rôle ASP.NET du gestionnaire d’autorisations est configuré à l’aide de l' `providers` élément <>.  
  
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
  
 Pour plus d’informations sur l’intégration d’un fournisseur de rôle ASP.NET à une application WCF, consultez [Comment : utiliser le fournisseur de rôles ASP.net avec un service](how-to-use-the-aspnet-role-provider-with-a-service.md). Pour plus d’informations sur l’utilisation du gestionnaire d’autorisations avec ASP.NET, consultez [procédure : utiliser le gestionnaire d’autorisations (AzMan) avec ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).  
  
## <a name="see-also"></a>Voir aussi

- [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](how-to-use-the-aspnet-role-provider-with-a-service.md)
