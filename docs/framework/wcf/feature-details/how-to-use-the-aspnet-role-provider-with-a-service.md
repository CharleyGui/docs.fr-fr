---
title: 'Comment : utiliser le fournisseur de rôle ASP.NET avec un service'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184771"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Comment : utiliser le fournisseur de rôle ASP.NET avec un service

Le fournisseur de rôles ASP.NET (en collaboration avec le fournisseur d’adhésion ASP.NET) est une fonctionnalité qui permet aux développeurs ASP.NET de créer des sites Web qui permettent aux utilisateurs de créer un compte avec un site et d’être attribué des rôles à des fins d’autorisation. Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d’un accès exclusif à celui-ci et à ses services. Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows. Au lieu de cela, tout utilisateur qui fournit leurs informations d’identification (le nom d’utilisateur / combinaison mot de passe) peut utiliser le site et ses services.  
  
Pour une demande d’exemple, voir [Adhésion et Fournisseur de rôle](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Pour plus d’informations sur la fonction ASP.NET fournisseur d’adhésion, voir [comment : Utilisez le fournisseur d’adhésion ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
La fonctionnalité de fournisseur de rôle utilise une base de données SQL Server pour stocker des informations utilisateur. Les développeurs de la Windows Communication Foundation (WCF) peuvent profiter de ces fonctionnalités à des fins de sécurité. Lorsqu’ils sont intégrés dans une application WCF, les utilisateurs doivent fournir une combinaison nom d’utilisateur/mot de passe à l’application client WCF. Pour permettre à WCF d’utiliser la base <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> de données, <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>vous devez créer une instance de la <xref:System.ServiceModel.ServiceHost> classe, définir sa <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriété à , et ajouter l’instance à la collecte des comportements à celui qui héberge le service.  
  
## <a name="configure-the-role-provider"></a>Configurer le fournisseur de rôles  
  
1. Dans le fichier Web.config, sous `system.web` l’élément> <, ajoutez `roleManager` un élément <> `enabled` et `true`définissez son attribut à .  
  
2. Affectez à l'attribut `defaultProvider` la valeur `SqlRoleProvider`.  
  
3. Comme un enfant à l’élément `roleManager` <>, ajouter un `providers` élément <>.  
  
4. Comme un enfant à `providers` la <> élément, ajouter un `add` élément <> avec les attributs `name`suivants `type` `connectionStringName`définis `applicationName`à des valeurs appropriées: , , et , comme indiqué dans l’exemple suivant.  
  
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
  
1. Dans le fichier Web.config, ajoutez un [ \<élément>system.serviceModel.](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Ajoutez [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) un comportement>élément à l’élément `system.ServiceModel` <>.  
  
3. Ajouter un [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à l’élément `behaviors` <>.  
  
4. Ajoutez [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) un comportement>élément et `name` définissez l’attribut à une valeur appropriée.  
  
5. Ajouter un [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) à l’élément `behavior`> <.  
  
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

- [Fournisseur d’appartenances et de rôles](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [Comment : utiliser le fournisseur d'appartenances ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
