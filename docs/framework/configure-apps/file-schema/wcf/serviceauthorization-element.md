---
title: <serviceAuthorization>, élément
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834020"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="a679d-102">\<élément serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="a679d-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="a679d-103">Spécifie les paramètres qui autorisent l'accès pour l'entretien des opérations</span><span class="sxs-lookup"><span data-stu-id="a679d-103">Specifies settings that authorize access to service operations</span></span>

<span data-ttu-id="a679d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a679d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a679d-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a679d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a679d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**comportements**](behaviors.md)\<></span><span class="sxs-lookup"><span data-stu-id="a679d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a679d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**serviceBehaviors**](servicebehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="a679d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="a679d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](behavior-of-servicebehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="a679d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="a679d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**serviceAuthorization >**</span><span class="sxs-lookup"><span data-stu-id="a679d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a679d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a679d-110">Syntax</span></span>

```xml
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a679d-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a679d-111">Attributes and elements</span></span>

<span data-ttu-id="a679d-112">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents :</span><span class="sxs-lookup"><span data-stu-id="a679d-112">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="a679d-113">Attributes</span><span class="sxs-lookup"><span data-stu-id="a679d-113">Attributes</span></span>

|<span data-ttu-id="a679d-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a679d-114">Attribute</span></span>|<span data-ttu-id="a679d-115">Description</span><span class="sxs-lookup"><span data-stu-id="a679d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a679d-116">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="a679d-116">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="a679d-117">Valeur booléenne qui spécifie si toutes les opérations du service personnifient l'appelant.</span><span class="sxs-lookup"><span data-stu-id="a679d-117">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="a679d-118">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="a679d-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a679d-119">Lorsqu'une opération de service spécifique personnifie l'appelant, le contexte du thread est basculé sur le contexte de l'appelant avant d'exécuter le service spécifié.</span><span class="sxs-lookup"><span data-stu-id="a679d-119">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="a679d-120">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="a679d-120">principalPermissionMode</span></span>|<span data-ttu-id="a679d-121">Définit la principal de sécurité utilisée pour effectuer les opérations sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="a679d-121">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="a679d-122">Les valeurs sont notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a679d-122">Values include the following:</span></span><br /><br /> <span data-ttu-id="a679d-123">-Aucun</span><span class="sxs-lookup"><span data-stu-id="a679d-123">-   None</span></span><br /><span data-ttu-id="a679d-124">-   UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="a679d-124">-   UseWindowsGroups</span></span><br /><span data-ttu-id="a679d-125">-   UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="a679d-125">-   UseAspNetRoles</span></span><br /><span data-ttu-id="a679d-126">-Personnalisé</span><span class="sxs-lookup"><span data-stu-id="a679d-126">-   Custom</span></span><br /><br /> <span data-ttu-id="a679d-127">La valeur par défaut est UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="a679d-127">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="a679d-128">La valeur est de type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="a679d-128">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="a679d-129">Pour plus d’informations sur l’utilisation de cet attribut, consultez [Comment : restreindre l’accès avec la classe PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="a679d-129">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="a679d-130">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="a679d-130">roleProviderName</span></span>|<span data-ttu-id="a679d-131">Chaîne qui spécifie le nom du fournisseur de rôles, qui fournit des informations de rôle pour une application de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a679d-131">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="a679d-132">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="a679d-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="a679d-133">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="a679d-133">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="a679d-134">Chaîne qui contient le type du gestionnaire d'autorisations de service.</span><span class="sxs-lookup"><span data-stu-id="a679d-134">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="a679d-135">Pour plus d'informations, consultez <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="a679d-135">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="a679d-136">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a679d-136">Child elements</span></span>

|<span data-ttu-id="a679d-137">Élément</span><span class="sxs-lookup"><span data-stu-id="a679d-137">Element</span></span>|<span data-ttu-id="a679d-138">Description</span><span class="sxs-lookup"><span data-stu-id="a679d-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a679d-139">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="a679d-139">authorizationPolicies</span></span>|<span data-ttu-id="a679d-140">Contient une collection des types de la stratégie d'autorisation, qui peuvent être ajoutés à l'aide du mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="a679d-140">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="a679d-141">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="a679d-141">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="a679d-142">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="a679d-142">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="a679d-143">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="a679d-143">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="a679d-144">Pour plus d'informations, consultez <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a679d-144">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="a679d-145">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a679d-145">Parent elements</span></span>

|<span data-ttu-id="a679d-146">Élément</span><span class="sxs-lookup"><span data-stu-id="a679d-146">Element</span></span>|<span data-ttu-id="a679d-147">Description</span><span class="sxs-lookup"><span data-stu-id="a679d-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a679d-148">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a679d-148">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a679d-149">Contient une collection de paramètres pour le comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="a679d-149">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="a679d-150">Remarques</span><span class="sxs-lookup"><span data-stu-id="a679d-150">Remarks</span></span>

<span data-ttu-id="a679d-151">Cette section contient des éléments qui affectent l'autorisation, les fournisseurs de rôles personnalisés et l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="a679d-151">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="a679d-152">L'attribut `principalPermissionMode` spécifie les groupes d'utilisateurs à utiliser lors de l'autorisation d'utilisation d'une méthode protégée.</span><span class="sxs-lookup"><span data-stu-id="a679d-152">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="a679d-153">La valeur par défaut (`UseWindowsGroups`) spécifie qu'une identité essayant d'accéder à une ressource est recherchée dans les groupes Windows, comme Administrateurs ou Utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="a679d-153">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="a679d-154">Vous pouvez également spécifier `UseAspNetRoles` pour utiliser un fournisseur de rôles personnalisé configuré sous l’élément \<System. Web >, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a679d-154">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

```xml
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```
  
<span data-ttu-id="a679d-155">Le code suivant illustre l' `roleProviderName` utilisé avec l’attribut `principalPermissionMode` :</span><span class="sxs-lookup"><span data-stu-id="a679d-155">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="a679d-156">Pour obtenir un exemple détaillé de l’utilisation de cet élément de configuration, consultez autorisation de l' [accès aux opérations de service et à](../../../wcf/samples/authorizing-access-to-service-operations.md) la [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="a679d-156">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a679d-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a679d-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="a679d-158">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="a679d-158">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a679d-159">Autorisation de l’accès aux opérations de service</span><span class="sxs-lookup"><span data-stu-id="a679d-159">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="a679d-160">Guide pratique pour créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="a679d-160">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="a679d-161">Guide pratique pour restreindre l’accès avec la classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="a679d-161">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="a679d-162">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="a679d-162">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
