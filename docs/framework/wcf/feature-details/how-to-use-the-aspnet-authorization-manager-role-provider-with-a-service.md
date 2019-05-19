---
title: 'Procédure : utiliser le fournisseur de rôle du Gestionnaire d’autorisations ASP.NET avec un service'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 778af929b4cfc96ce0683d304be5f8fb87a0e47b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880197"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Procédure : utiliser le fournisseur de rôle du Gestionnaire d’autorisations ASP.NET avec un service
Lorsqu’ASP.NET héberge un service Web, vous pouvez intégrer le Gestionnaire d’autorisations dans l’application puisse fournir l’autorisation au service. Le Gestionnaire d'autorisations permet à un développeur d'applications de définir des opérations individuelles qui peuvent être regroupées pour former des tâches. Un administrateur peut autoriser ensuite que les rôles exécutent des tâches spécifiques ou des opérations individuelles. Le Gestionnaire d’autorisations fournit un outil d’administration sous la forme d’un composant logiciel enfichable MMC (Microsoft Management Console) pour gérer des rôles, des tâches, des opérations et des utilisateurs. Les administrateurs configurent un magasin de stratégie du Gestionnaire d'autorisations dans un fichier XML, Active Directory, ou dans un magasin Active Directory en mode application (ADAM).  
  
 Le Gestionnaire d’autorisations est intégré dans l’application en configurant le fournisseur de rôles ASP.NET du Gestionnaire d’autorisations pour l’application ASP.NET qui héberge le service Web. Comme les autres fournisseurs de rôles ASP.NET, le fournisseur de rôles ASP.NET du Gestionnaire d’autorisations est configuré à l’aide de la <`providers`> élément.  
  
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
  
 Pour plus d’informations sur l’intégration d’un fournisseur de rôle ASP.NET avec une application WCF, consultez [Comment : Utiliser le fournisseur de rôle ASP.NET avec un Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Pour plus d’informations sur l’utilisation du Gestionnaire d’autorisations avec ASP.NET, consultez [Comment : Utilisez le Gestionnaire d’autorisations (AzMan) avec ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Utiliser le fournisseur de rôle ASP.NET avec un Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
