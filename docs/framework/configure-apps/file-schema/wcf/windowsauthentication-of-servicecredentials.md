---
title: <windowsAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399109"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="cd9db-102">\<> WindowsAuthentication du \<> ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="cd9db-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="cd9db-103">Spécifie les paramètres d'une information d'identification de service Windows.</span><span class="sxs-lookup"><span data-stu-id="cd9db-103">Specifies the settings of a Windows service credential.</span></span>  
  
<span data-ttu-id="cd9db-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cd9db-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cd9db-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cd9db-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cd9db-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cd9db-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="cd9db-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cd9db-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="cd9db-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cd9db-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="cd9db-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="cd9db-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="cd9db-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> windowsAuthentication**</span><span class="sxs-lookup"><span data-stu-id="cd9db-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9db-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd9db-111">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd9db-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cd9db-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cd9db-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cd9db-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd9db-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="cd9db-114">Attributes</span></span>  
  
|<span data-ttu-id="cd9db-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="cd9db-115">Attribute</span></span>|<span data-ttu-id="cd9db-116">Description</span><span class="sxs-lookup"><span data-stu-id="cd9db-116">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="cd9db-117">Attribut à valeur booléenne facultatif qui spécifie si le système inclut des groupes Windows dans le contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="cd9db-117">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="cd9db-118">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="cd9db-118">The default is `true`.</span></span><br /><br /> <span data-ttu-id="cd9db-119">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe.</span><span class="sxs-lookup"><span data-stu-id="cd9db-119">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="cd9db-120">Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cd9db-120">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="cd9db-121">Attribut à valeur booléenne facultatif qui spécifie si les appelants anonymes et non authentifiés sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="cd9db-121">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="cd9db-122">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="cd9db-122">The default is `false`.</span></span><br /><br /> <span data-ttu-id="cd9db-123">Lorsque l’attribut `clientCredentialType` d’une liaison a la valeur `Windows`, le système n’autorise pas d’appelants anonymes.</span><span class="sxs-lookup"><span data-stu-id="cd9db-123">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="cd9db-124">Cela signifie que seuls les appelants authentifiés du domaine ou du groupe de travail sont autorisés à accéder au système.</span><span class="sxs-lookup"><span data-stu-id="cd9db-124">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="cd9db-125">Vous pouvez substituer ce comportement en utilisant cet attribut.</span><span class="sxs-lookup"><span data-stu-id="cd9db-125">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="cd9db-126">N'utilisez ce paramètre qu'avec beaucoup de précaution.</span><span class="sxs-lookup"><span data-stu-id="cd9db-126">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd9db-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cd9db-127">Child Elements</span></span>  
 <span data-ttu-id="cd9db-128">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cd9db-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd9db-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cd9db-129">Parent Elements</span></span>  
  
|<span data-ttu-id="cd9db-130">Élément</span><span class="sxs-lookup"><span data-stu-id="cd9db-130">Element</span></span>|<span data-ttu-id="cd9db-131">Description</span><span class="sxs-lookup"><span data-stu-id="cd9db-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd9db-132">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cd9db-132">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="cd9db-133">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="cd9db-133">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd9db-134">Notes</span><span class="sxs-lookup"><span data-stu-id="cd9db-134">Remarks</span></span>  
 <span data-ttu-id="cd9db-135">Utilisez cet élément pour autoriser l'accès d'utilisateurs Windows anonymes en définissant l'attribut `allowAnonymousLogons`.</span><span class="sxs-lookup"><span data-stu-id="cd9db-135">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="cd9db-136">Vous pouvez également indiquer s'il faut inclure des informations sur les groupes auxquels les utilisateurs appartiennent dans AuthorizationContext en définissant l'attribut `includeWindowsGroups`.</span><span class="sxs-lookup"><span data-stu-id="cd9db-136">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="cd9db-137">Si ce dernier a la valeur `true` (paramètre par défaut), le service peut déterminer les groupes Windows auxquels le client appartient.</span><span class="sxs-lookup"><span data-stu-id="cd9db-137">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9db-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd9db-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
