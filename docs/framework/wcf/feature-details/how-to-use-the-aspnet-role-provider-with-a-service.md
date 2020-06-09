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
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="4ac13-102">Comment : utiliser le fournisseur de rôle ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="4ac13-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="4ac13-103">Le fournisseur de rôle ASP.NET (conjointement au fournisseur d’appartenances ASP.NET) est une fonctionnalité qui permet aux développeurs ASP.NET de créer des sites Web qui permettent aux utilisateurs de créer un compte avec un site et d’être affectés à des rôles à des fins d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="4ac13-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="4ac13-104">Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d’un accès exclusif à celui-ci et à ses services.</span><span class="sxs-lookup"><span data-stu-id="4ac13-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="4ac13-105">Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="4ac13-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="4ac13-106">Au lieu de cela, tout utilisateur qui fournit ses informations d’identification (combinaison nom d’utilisateur/mot de passe) peut utiliser le site et ses services.</span><span class="sxs-lookup"><span data-stu-id="4ac13-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="4ac13-107">Pour obtenir un exemple d’application, consultez [appartenance et fournisseur de rôles](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4ac13-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="4ac13-108">Pour plus d’informations sur la fonctionnalité de fournisseur d’appartenances ASP.NET, consultez [Comment : utiliser le fournisseur d’appartenances ASP.net](how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4ac13-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="4ac13-109">La fonctionnalité de fournisseur de rôle utilise une base de données SQL Server pour stocker des informations utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4ac13-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="4ac13-110">Les développeurs Windows Communication Foundation (WCF) peuvent tirer parti de ces fonctionnalités à des fins de sécurité.</span><span class="sxs-lookup"><span data-stu-id="4ac13-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="4ac13-111">Lorsqu’ils sont intégrés à une application WCF, les utilisateurs doivent fournir une combinaison nom d’utilisateur/mot de passe à l’application cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="4ac13-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="4ac13-112">Pour permettre à WCF d’utiliser la base de données, vous devez créer une instance de la <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> classe, affecter à sa propriété la valeur <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> et ajouter l’instance à la collection de comportements au <xref:System.ServiceModel.ServiceHost> qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="4ac13-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="4ac13-113">Configurer le fournisseur de rôles</span><span class="sxs-lookup"><span data-stu-id="4ac13-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="4ac13-114">Dans le fichier Web. config, sous l' `system.web` élément < >, ajoutez un `roleManager` élément < > et affectez `enabled` à son attribut la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="4ac13-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="4ac13-115">Affectez à l'attribut `defaultProvider` la valeur `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="4ac13-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="4ac13-116">En tant qu’enfant de l' `roleManager` élément <>, ajoutez un `providers` élément <>.</span><span class="sxs-lookup"><span data-stu-id="4ac13-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="4ac13-117">En tant qu’enfant de l' `providers` élément <>, ajoutez un `add` élément <> avec les attributs suivants définis sur les valeurs appropriées : `name` , `type` , `connectionStringName` et `applicationName` , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4ac13-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="4ac13-118">Configurer le service pour utiliser le fournisseur de rôle</span><span class="sxs-lookup"><span data-stu-id="4ac13-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="4ac13-119">Dans le fichier Web. config, ajoutez un [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément.</span><span class="sxs-lookup"><span data-stu-id="4ac13-119">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="4ac13-120">Ajoutez un [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément à l' `system.ServiceModel` élément <>.</span><span class="sxs-lookup"><span data-stu-id="4ac13-120">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="4ac13-121">Ajoutez un [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l' `behaviors` élément <>.</span><span class="sxs-lookup"><span data-stu-id="4ac13-121">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="4ac13-122">Ajoutez un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) élément et affectez `name` à l’attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="4ac13-122">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="4ac13-123">Ajoutez un [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) à l' `behavior` élément <>.</span><span class="sxs-lookup"><span data-stu-id="4ac13-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="4ac13-124">Affectez à l'attribut `principalPermissionMode` la valeur `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="4ac13-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="4ac13-125">Affectez à l'attribut `roleProviderName` la valeur `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="4ac13-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="4ac13-126">L'exemple suivant présente un fragment de la configuration.</span><span class="sxs-lookup"><span data-stu-id="4ac13-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ac13-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ac13-127">See also</span></span>

- [<span data-ttu-id="4ac13-128">Membership and Role Provider</span><span class="sxs-lookup"><span data-stu-id="4ac13-128">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="4ac13-129">Comment : utiliser le fournisseur d'appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4ac13-129">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
