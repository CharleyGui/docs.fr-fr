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
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="358cb-102">Comment : utiliser le fournisseur de rôle ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="358cb-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="358cb-103">Le fournisseur de rôles ASP.NET (en collaboration avec le fournisseur d’adhésion ASP.NET) est une fonctionnalité qui permet aux développeurs ASP.NET de créer des sites Web qui permettent aux utilisateurs de créer un compte avec un site et d’être attribué des rôles à des fins d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="358cb-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="358cb-104">Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d’un accès exclusif à celui-ci et à ses services.</span><span class="sxs-lookup"><span data-stu-id="358cb-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="358cb-105">Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="358cb-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="358cb-106">Au lieu de cela, tout utilisateur qui fournit leurs informations d’identification (le nom d’utilisateur / combinaison mot de passe) peut utiliser le site et ses services.</span><span class="sxs-lookup"><span data-stu-id="358cb-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="358cb-107">Pour une demande d’exemple, voir [Adhésion et Fournisseur de rôle](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="358cb-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="358cb-108">Pour plus d’informations sur la fonction ASP.NET fournisseur d’adhésion, voir [comment : Utilisez le fournisseur d’adhésion ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="358cb-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="358cb-109">La fonctionnalité de fournisseur de rôle utilise une base de données SQL Server pour stocker des informations utilisateur.</span><span class="sxs-lookup"><span data-stu-id="358cb-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="358cb-110">Les développeurs de la Windows Communication Foundation (WCF) peuvent profiter de ces fonctionnalités à des fins de sécurité.</span><span class="sxs-lookup"><span data-stu-id="358cb-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="358cb-111">Lorsqu’ils sont intégrés dans une application WCF, les utilisateurs doivent fournir une combinaison nom d’utilisateur/mot de passe à l’application client WCF.</span><span class="sxs-lookup"><span data-stu-id="358cb-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="358cb-112">Pour permettre à WCF d’utiliser la base <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> de données, <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>vous devez créer une instance de la <xref:System.ServiceModel.ServiceHost> classe, définir sa <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriété à , et ajouter l’instance à la collecte des comportements à celui qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="358cb-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="358cb-113">Configurer le fournisseur de rôles</span><span class="sxs-lookup"><span data-stu-id="358cb-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="358cb-114">Dans le fichier Web.config, sous `system.web` l’élément> <, ajoutez `roleManager` un élément <> `enabled` et `true`définissez son attribut à .</span><span class="sxs-lookup"><span data-stu-id="358cb-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="358cb-115">Affectez à l'attribut `defaultProvider` la valeur `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="358cb-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="358cb-116">Comme un enfant à l’élément `roleManager` <>, ajouter un `providers` élément <>.</span><span class="sxs-lookup"><span data-stu-id="358cb-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="358cb-117">Comme un enfant à `providers` la <> élément, ajouter un `add` élément <> avec les attributs `name`suivants `type` `connectionStringName`définis `applicationName`à des valeurs appropriées: , , et , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="358cb-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="358cb-118">Configurer le service pour utiliser le fournisseur de rôle</span><span class="sxs-lookup"><span data-stu-id="358cb-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="358cb-119">Dans le fichier Web.config, ajoutez un [ \<élément>system.serviceModel.](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="358cb-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="358cb-120">Ajoutez [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) un comportement>élément à l’élément `system.ServiceModel` <>.</span><span class="sxs-lookup"><span data-stu-id="358cb-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="358cb-121">Ajouter un [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à l’élément `behaviors` <>.</span><span class="sxs-lookup"><span data-stu-id="358cb-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="358cb-122">Ajoutez [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) un comportement>élément et `name` définissez l’attribut à une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="358cb-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="358cb-123">Ajouter un [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) à l’élément `behavior`> <.</span><span class="sxs-lookup"><span data-stu-id="358cb-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="358cb-124">Affectez à l'attribut `principalPermissionMode` la valeur `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="358cb-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="358cb-125">Affectez à l'attribut `roleProviderName` la valeur `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="358cb-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="358cb-126">L'exemple suivant présente un fragment de la configuration.</span><span class="sxs-lookup"><span data-stu-id="358cb-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="358cb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="358cb-127">See also</span></span>

- [<span data-ttu-id="358cb-128">Fournisseur d’appartenances et de rôles</span><span class="sxs-lookup"><span data-stu-id="358cb-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="358cb-129">Comment : utiliser le fournisseur d'appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="358cb-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
