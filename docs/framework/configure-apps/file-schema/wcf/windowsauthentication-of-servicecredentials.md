---
title: <windowsAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 81793b0d58a95166bc23f98d46ce94a5f1e1d018
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940288"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="6027f-102">\<> WindowsAuthentication du \<> ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="6027f-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="6027f-103">Spécifie les paramètres d'une information d'identification de service Windows.</span><span class="sxs-lookup"><span data-stu-id="6027f-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="6027f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6027f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6027f-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="6027f-105">\<behaviors></span></span>  
<span data-ttu-id="6027f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6027f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6027f-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="6027f-107">\<behavior></span></span>  
<span data-ttu-id="6027f-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6027f-108">\<serviceCredentials></span></span>  
<span data-ttu-id="6027f-109">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="6027f-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6027f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6027f-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6027f-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6027f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6027f-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6027f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6027f-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="6027f-113">Attributes</span></span>  
  
|<span data-ttu-id="6027f-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="6027f-114">Attribute</span></span>|<span data-ttu-id="6027f-115">Description</span><span class="sxs-lookup"><span data-stu-id="6027f-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="6027f-116">Attribut à valeur booléenne facultatif qui spécifie si le système inclut des groupes Windows dans le contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="6027f-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="6027f-117">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="6027f-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="6027f-118">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe.</span><span class="sxs-lookup"><span data-stu-id="6027f-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="6027f-119">Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6027f-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="6027f-120">Attribut à valeur booléenne facultatif qui spécifie si les appelants anonymes et non authentifiés sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="6027f-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="6027f-121">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="6027f-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6027f-122">Lorsque l’attribut `clientCredentialType` d’une liaison a la valeur `Windows`, le système n’autorise pas d’appelants anonymes.</span><span class="sxs-lookup"><span data-stu-id="6027f-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="6027f-123">Cela signifie que seuls les appelants authentifiés du domaine ou du groupe de travail sont autorisés à accéder au système.</span><span class="sxs-lookup"><span data-stu-id="6027f-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="6027f-124">Vous pouvez substituer ce comportement en utilisant cet attribut.</span><span class="sxs-lookup"><span data-stu-id="6027f-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="6027f-125">N'utilisez ce paramètre qu'avec beaucoup de précaution.</span><span class="sxs-lookup"><span data-stu-id="6027f-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6027f-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6027f-126">Child Elements</span></span>  
 <span data-ttu-id="6027f-127">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6027f-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6027f-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6027f-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6027f-129">Élément</span><span class="sxs-lookup"><span data-stu-id="6027f-129">Element</span></span>|<span data-ttu-id="6027f-130">Description</span><span class="sxs-lookup"><span data-stu-id="6027f-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6027f-131">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6027f-131">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="6027f-132">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="6027f-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6027f-133">Notes</span><span class="sxs-lookup"><span data-stu-id="6027f-133">Remarks</span></span>  
 <span data-ttu-id="6027f-134">Utilisez cet élément pour autoriser l'accès d'utilisateurs Windows anonymes en définissant l'attribut `allowAnonymousLogons`.</span><span class="sxs-lookup"><span data-stu-id="6027f-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="6027f-135">Vous pouvez également indiquer s'il faut inclure des informations sur les groupes auxquels les utilisateurs appartiennent dans AuthorizationContext en définissant l'attribut `includeWindowsGroups`.</span><span class="sxs-lookup"><span data-stu-id="6027f-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="6027f-136">Si ce dernier a la valeur `true` (paramètre par défaut), le service peut déterminer les groupes Windows auxquels le client appartient.</span><span class="sxs-lookup"><span data-stu-id="6027f-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6027f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6027f-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
