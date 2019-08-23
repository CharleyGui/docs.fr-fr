---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 399158632d5c17a35ded02691ba35a231e6cdc6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940537"
---
# <a name="usernameauthentication"></a><span data-ttu-id="c84c1-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="c84c1-101">\<userNameAuthentication></span></span>
<span data-ttu-id="c84c1-102">Spécifie les informations d'identification d'un service selon le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c84c1-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="c84c1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c84c1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c84c1-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c84c1-104">\<behaviors></span></span>  
<span data-ttu-id="c84c1-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c84c1-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c84c1-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="c84c1-106">\<behavior></span></span>  
<span data-ttu-id="c84c1-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c84c1-107">\<serviceCredentials></span></span>  
<span data-ttu-id="c84c1-108">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="c84c1-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c84c1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c84c1-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c84c1-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c84c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c84c1-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c84c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c84c1-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c84c1-112">Attributes</span></span>  
  
|<span data-ttu-id="c84c1-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="c84c1-113">Attribute</span></span>|<span data-ttu-id="c84c1-114">Description</span><span class="sxs-lookup"><span data-stu-id="c84c1-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="c84c1-115"><xref:System.TimeSpan> qui spécifie la durée maximale de mise en cache d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="c84c1-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="c84c1-116">La valeur par défaut est 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="c84c1-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="c84c1-117">Valeur booléenne qui spécifie si les jetons d'ouverture de session sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="c84c1-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="c84c1-118">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="c84c1-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="c84c1-119">Chaîne qui spécifie le type de validateur de mot de passe de nom d'utilisateur personnalisé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c84c1-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="c84c1-120">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="c84c1-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="c84c1-121">Valeur booléenne qui spécifie si les groupes Windows sont inclus au contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c84c1-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="c84c1-122">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="c84c1-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="c84c1-123">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe.</span><span class="sxs-lookup"><span data-stu-id="c84c1-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="c84c1-124">Affectez la valeur `false` à cette propriété s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c84c1-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="c84c1-125">Entier qui spécifie le nombre maximal de jetons d'ouverture de session à mettre en cache.</span><span class="sxs-lookup"><span data-stu-id="c84c1-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="c84c1-126">Cette valeur doit être supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="c84c1-126">This value should be larger than zero.</span></span> <span data-ttu-id="c84c1-127">La valeur par défaut est 128.</span><span class="sxs-lookup"><span data-stu-id="c84c1-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="c84c1-128">Lorsque l’attribut `clientCredentialType` d’une liaison a la valeur `username`, le nom d’utilisateur est mappé aux comptes Windows.</span><span class="sxs-lookup"><span data-stu-id="c84c1-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="c84c1-129">Vous pouvez substituer ce comportement à l’aide de cet attribut, qui est une chaîne contenant le nom de la valeur <xref:System.Web.Security.MembershipProvider> qui fournit le mécanisme de validation du mot de passe pertinent.</span><span class="sxs-lookup"><span data-stu-id="c84c1-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="c84c1-130">Spécifie la manière dont le mot de passe de nom d'utilisateur est validé.</span><span class="sxs-lookup"><span data-stu-id="c84c1-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="c84c1-131">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c84c1-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="c84c1-132">-   Windows</span><span class="sxs-lookup"><span data-stu-id="c84c1-132">-   Windows</span></span><br /><span data-ttu-id="c84c1-133">-   MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="c84c1-133">-   MembershipProvider</span></span><br /><span data-ttu-id="c84c1-134">-Personnalisé</span><span class="sxs-lookup"><span data-stu-id="c84c1-134">-   Custom</span></span><br /><br /> <span data-ttu-id="c84c1-135">Le paramètre par défaut est Windows.</span><span class="sxs-lookup"><span data-stu-id="c84c1-135">The default is Windows.</span></span> <span data-ttu-id="c84c1-136">Cet attribut est de type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="c84c1-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c84c1-137">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c84c1-137">Child Elements</span></span>  
 <span data-ttu-id="c84c1-138">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c84c1-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c84c1-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c84c1-139">Parent Elements</span></span>  
  
|<span data-ttu-id="c84c1-140">Élément</span><span class="sxs-lookup"><span data-stu-id="c84c1-140">Element</span></span>|<span data-ttu-id="c84c1-141">Description</span><span class="sxs-lookup"><span data-stu-id="c84c1-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c84c1-142">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c84c1-142">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="c84c1-143">Spécifie l’information d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l’information d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="c84c1-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c84c1-144">Notes</span><span class="sxs-lookup"><span data-stu-id="c84c1-144">Remarks</span></span>  
 <span data-ttu-id="c84c1-145">Si aucune des liaisons utilisées par un service n'est configurée pour l'authentification par nom d'utilisateur/mot de passe, les attributs de cet élément sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="c84c1-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="c84c1-146">Il s'agit notamment de `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName` et `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="c84c1-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="c84c1-147">Si aucun des liaisons utilisées par un service n’est configurée pour utiliser l’authentification Windows par nom d’utilisateur/mot de passe, les paramètres en rapport avec la mise en cache des jetons d’ouverture de session sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="c84c1-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="c84c1-148">Il s'agit notamment de `cacheLogonTokenLifetime`, `cacheLogonTokens` et `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="c84c1-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c84c1-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c84c1-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
