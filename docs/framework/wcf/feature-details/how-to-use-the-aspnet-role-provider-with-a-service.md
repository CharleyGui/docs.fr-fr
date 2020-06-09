---
title: 'Comment : utiliser le fournisseur de rôle ASP.NET avec un service'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595295"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Comment : utiliser le fournisseur de rôle ASP.NET avec un service

Le fournisseur de rôle ASP.NET (conjointement au fournisseur d’appartenances ASP.NET) est une fonctionnalité qui permet aux développeurs ASP.NET de créer des sites Web qui permettent aux utilisateurs de créer un compte avec un site et d’être affectés à des rôles à des fins d’autorisation. Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d’un accès exclusif à celui-ci et à ses services. Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows. Au lieu de cela, tout utilisateur qui fournit ses informations d’identification (combinaison nom d’utilisateur/mot de passe) peut utiliser le site et ses services.  
  
Pour obtenir un exemple d’application, consultez [appartenance et fournisseur de rôles](../samples/membership-and-role-provider.md). Pour plus d’informations sur la fonctionnalité de fournisseur d’appartenances ASP.NET, consultez [Comment : utiliser le fournisseur d’appartenances ASP.net](how-to-use-the-aspnet-membership-provider.md).  
  
La fonctionnalité de fournisseur de rôle utilise une base de données SQL Server pour stocker des informations utilisateur. Les développeurs Windows Communication Foundation (WCF) peuvent tirer parti de ces fonctionnalités à des fins de sécurité. Lorsqu’ils sont intégrés à une application WCF, les utilisateurs doivent fournir une combinaison nom d’utilisateur/mot de passe à l’application cliente WCF. Pour permettre à WCF d’utiliser la base de données, vous devez créer une instance de la <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> classe, affecter à sa propriété la valeur <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> et ajouter l’instance à la collection de comportements au <xref:System.ServiceModel.ServiceHost> qui héberge le service.  
  
## <a name="configure-the-role-provider"></a>Configurer le fournisseur de rôles  
  
1. Dans le fichier Web. config, sous l' `system.web` élément < >, ajoutez un `roleManager` élément < > et affectez `enabled` à son attribut la valeur `true` .  
  
2. Affectez à l'attribut `defaultProvider` la valeur `SqlRoleProvider`.  
  
3. En tant qu’enfant de l' `roleManager` élément <>, ajoutez un `providers` élément <>.  
  
4. En tant qu’enfant de l' `providers` élément <>, ajoutez un `add` élément <> avec les attributs suivants définis sur les valeurs appropriées : `name` , `type` , `connectionStringName` et `applicationName` , comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
## <a name="configure-the-service-to-use-the-role-provider"></a>Configurer le service pour utiliser le fournisseur de rôle  
  
1. Dans le fichier Web. config, ajoutez un [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément.  
  
2. Ajoutez un [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément à l' `system.ServiceModel` élément <>.  
  
3. Ajoutez un [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l' `behaviors` élément <>.  
  
4. Ajoutez un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) élément et affectez `name` à l’attribut une valeur appropriée.  
  
5. Ajoutez un [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) à l' `behavior` élément <>.  
  
6. Affectez à l'attribut `principalPermissionMode` la valeur `UseAspNetRoles`.  
  
7. Affectez à l'attribut `roleProviderName` la valeur `SqlRoleProvider`. L'exemple suivant présente un fragment de la configuration.  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Membership and Role Provider](../samples/membership-and-role-provider.md)
- [Comment : utiliser le fournisseur d'appartenances ASP.NET](how-to-use-the-aspnet-membership-provider.md)
