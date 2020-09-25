---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 30fd78d6c56e8b22e0e744a38f18ac076dc70162
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178032"
---
# \<userNameAuthentication>

<span data-ttu-id="ee1e0-101">Spécifie les informations d'identification d'un service selon le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-101">Specifies a service's credentials based on user name and password.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="ee1e0-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee1e0-102">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee1e0-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ee1e0-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ee1e0-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee1e0-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="ee1e0-105">Attributes</span></span>  
  
|<span data-ttu-id="ee1e0-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="ee1e0-106">Attribute</span></span>|<span data-ttu-id="ee1e0-107">Description</span><span class="sxs-lookup"><span data-stu-id="ee1e0-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="ee1e0-108"><xref:System.TimeSpan> qui spécifie la durée maximale de mise en cache d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-108">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="ee1e0-109">La valeur par défaut est 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-109">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="ee1e0-110">Valeur booléenne qui spécifie si les jetons d'ouverture de session sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-110">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="ee1e0-111">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-111">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="ee1e0-112">Chaîne qui spécifie le type de validateur de mot de passe de nom d'utilisateur personnalisé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-112">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="ee1e0-113">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-113">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="ee1e0-114">Valeur booléenne qui spécifie si les groupes Windows sont inclus au contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-114">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="ee1e0-115">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-115">The default is `true`.</span></span><br /><br /> <span data-ttu-id="ee1e0-116">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-116">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="ee1e0-117">Affectez la valeur `false` à cette propriété s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-117">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="ee1e0-118">Entier qui spécifie le nombre maximal de jetons d'ouverture de session à mettre en cache.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-118">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="ee1e0-119">Cette valeur doit être supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-119">This value should be larger than zero.</span></span> <span data-ttu-id="ee1e0-120">La valeur par défaut est 128.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-120">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="ee1e0-121">Lorsque l’attribut `clientCredentialType` d’une liaison a la valeur `username`, le nom d’utilisateur est mappé aux comptes Windows.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-121">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="ee1e0-122">Vous pouvez substituer ce comportement à l’aide de cet attribut, qui est une chaîne contenant le nom de la valeur <xref:System.Web.Security.MembershipProvider> qui fournit le mécanisme de validation du mot de passe pertinent.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-122">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="ee1e0-123">Spécifie la manière dont le mot de passe de nom d'utilisateur est validé.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-123">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="ee1e0-124">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="ee1e0-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="ee1e0-125">-Windows</span><span class="sxs-lookup"><span data-stu-id="ee1e0-125">-   Windows</span></span><br /><span data-ttu-id="ee1e0-126">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="ee1e0-126">-   MembershipProvider</span></span><br /><span data-ttu-id="ee1e0-127">-Personnalisé</span><span class="sxs-lookup"><span data-stu-id="ee1e0-127">-   Custom</span></span><br /><br /> <span data-ttu-id="ee1e0-128">Le paramètre par défaut est Windows.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-128">The default is Windows.</span></span> <span data-ttu-id="ee1e0-129">Cet attribut est de type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-129">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee1e0-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ee1e0-130">Child Elements</span></span>  

 <span data-ttu-id="ee1e0-131">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee1e0-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ee1e0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="ee1e0-133">Élément</span><span class="sxs-lookup"><span data-stu-id="ee1e0-133">Element</span></span>|<span data-ttu-id="ee1e0-134">Description</span><span class="sxs-lookup"><span data-stu-id="ee1e0-134">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="ee1e0-135">Spécifie l’information d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l’information d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-135">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee1e0-136">Notes</span><span class="sxs-lookup"><span data-stu-id="ee1e0-136">Remarks</span></span>  

 <span data-ttu-id="ee1e0-137">Si aucune des liaisons utilisées par un service n'est configurée pour l'authentification par nom d'utilisateur/mot de passe, les attributs de cet élément sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-137">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="ee1e0-138">Il s'agit notamment de `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName` et `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-138">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="ee1e0-139">Si aucun des liaisons utilisées par un service n’est configurée pour utiliser l’authentification Windows par nom d’utilisateur/mot de passe, les paramètres en rapport avec la mise en cache des jetons d’ouverture de session sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-139">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="ee1e0-140">Il s'agit notamment de `cacheLogonTokenLifetime`, `cacheLogonTokens` et `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="ee1e0-140">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1e0-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee1e0-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
