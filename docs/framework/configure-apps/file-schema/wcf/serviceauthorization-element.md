---
title: <serviceAuthorization> (élément)
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834020"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="ac0c5-102">\<serviceAuthorization>, élément</span><span class="sxs-lookup"><span data-stu-id="ac0c5-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="ac0c5-103">Spécifie les paramètres qui autorisent l'accès pour l'entretien des opérations</span><span class="sxs-lookup"><span data-stu-id="ac0c5-103">Specifies settings that authorize access to service operations</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

## <a name="syntax"></a><span data-ttu-id="ac0c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac0c5-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="ac0c5-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ac0c5-105">Attributes and elements</span></span>

<span data-ttu-id="ac0c5-106">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents :</span><span class="sxs-lookup"><span data-stu-id="ac0c5-106">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="ac0c5-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="ac0c5-107">Attributes</span></span>

|<span data-ttu-id="ac0c5-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ac0c5-108">Attribute</span></span>|<span data-ttu-id="ac0c5-109">Description</span><span class="sxs-lookup"><span data-stu-id="ac0c5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac0c5-110">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="ac0c5-110">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="ac0c5-111">Valeur booléenne qui spécifie si toutes les opérations du service personnifient l'appelant.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-111">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="ac0c5-112">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="ac0c5-113">Lorsqu'une opération de service spécifique personnifie l'appelant, le contexte du thread est basculé sur le contexte de l'appelant avant d'exécuter le service spécifié.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-113">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="ac0c5-114">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="ac0c5-114">principalPermissionMode</span></span>|<span data-ttu-id="ac0c5-115">Définit la principal de sécurité utilisée pour effectuer les opérations sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-115">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="ac0c5-116">Les valeurs sont notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ac0c5-116">Values include the following:</span></span><br /><br /> <span data-ttu-id="ac0c5-117">-Aucun</span><span class="sxs-lookup"><span data-stu-id="ac0c5-117">-   None</span></span><br /><span data-ttu-id="ac0c5-118">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="ac0c5-118">-   UseWindowsGroups</span></span><br /><span data-ttu-id="ac0c5-119">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="ac0c5-119">-   UseAspNetRoles</span></span><br /><span data-ttu-id="ac0c5-120">-Personnalisé</span><span class="sxs-lookup"><span data-stu-id="ac0c5-120">-   Custom</span></span><br /><br /> <span data-ttu-id="ac0c5-121">La valeur par défaut est UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-121">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="ac0c5-122">La valeur est de type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-122">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="ac0c5-123">Pour plus d’informations sur l’utilisation de cet attribut, consultez [Comment : restreindre l’accès avec la classe PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="ac0c5-123">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="ac0c5-124">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="ac0c5-124">roleProviderName</span></span>|<span data-ttu-id="ac0c5-125">Chaîne qui spécifie le nom du fournisseur de rôles, qui fournit des informations de rôle pour une application de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ac0c5-125">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ac0c5-126">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="ac0c5-127">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="ac0c5-127">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="ac0c5-128">Chaîne qui contient le type du gestionnaire d'autorisations de service.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-128">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="ac0c5-129">Pour plus d’informations, consultez <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-129">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="ac0c5-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ac0c5-130">Child elements</span></span>

|<span data-ttu-id="ac0c5-131">Élément</span><span class="sxs-lookup"><span data-stu-id="ac0c5-131">Element</span></span>|<span data-ttu-id="ac0c5-132">Description</span><span class="sxs-lookup"><span data-stu-id="ac0c5-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac0c5-133">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="ac0c5-133">authorizationPolicies</span></span>|<span data-ttu-id="ac0c5-134">Contient une collection des types de la stratégie d'autorisation, qui peuvent être ajoutés à l'aide du mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-134">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="ac0c5-135">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-135">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="ac0c5-136">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-136">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="ac0c5-137">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-137">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="ac0c5-138">Pour plus d’informations, consultez <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-138">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="ac0c5-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ac0c5-139">Parent elements</span></span>

|<span data-ttu-id="ac0c5-140">Élément</span><span class="sxs-lookup"><span data-stu-id="ac0c5-140">Element</span></span>|<span data-ttu-id="ac0c5-141">Description</span><span class="sxs-lookup"><span data-stu-id="ac0c5-141">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ac0c5-142">Contient une collection de paramètres pour le comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-142">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="ac0c5-143">Remarques</span><span class="sxs-lookup"><span data-stu-id="ac0c5-143">Remarks</span></span>

<span data-ttu-id="ac0c5-144">Cette section contient des éléments qui affectent l'autorisation, les fournisseurs de rôles personnalisés et l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-144">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="ac0c5-145">L'attribut `principalPermissionMode` spécifie les groupes d'utilisateurs à utiliser lors de l'autorisation d'utilisation d'une méthode protégée.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-145">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="ac0c5-146">La valeur par défaut (`UseWindowsGroups`) spécifie qu'une identité essayant d'accéder à une ressource est recherchée dans les groupes Windows, comme Administrateurs ou Utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ac0c5-146">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="ac0c5-147">Vous pouvez également spécifier `UseAspNetRoles` l’utilisation d’un fournisseur de rôles personnalisé configuré sous l' \<system.web> élément, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ac0c5-147">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="ac0c5-148">Le code suivant montre le `roleProviderName` utilisé avec l' `principalPermissionMode` attribut :</span><span class="sxs-lookup"><span data-stu-id="ac0c5-148">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="ac0c5-149">Pour obtenir un exemple détaillé de l’utilisation de cet élément de configuration, consultez autorisation de l' [accès aux opérations de service et à](../../../wcf/samples/authorizing-access-to-service-operations.md) la [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="ac0c5-149">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ac0c5-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac0c5-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="ac0c5-151">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="ac0c5-151">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ac0c5-152">Authorizing Access to Service Operations</span><span class="sxs-lookup"><span data-stu-id="ac0c5-152">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="ac0c5-153">Guide pratique pour créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="ac0c5-153">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="ac0c5-154">Guide pratique pour restreindre l’accès avec la classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="ac0c5-154">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="ac0c5-155">Authorization Policy</span><span class="sxs-lookup"><span data-stu-id="ac0c5-155">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
