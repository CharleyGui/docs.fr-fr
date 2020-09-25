---
title: <windowsAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: bda375959b535ce5f2996d594f719893164b0bd4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194997"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="a7535-102">\<windowsAuthentication> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a7535-102">\<windowsAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="a7535-103">Spécifie les paramètres d'une information d'identification de service Windows.</span><span class="sxs-lookup"><span data-stu-id="a7535-103">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="a7535-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7535-104">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7535-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a7535-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a7535-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a7535-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7535-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a7535-107">Attributes</span></span>  
  
|<span data-ttu-id="a7535-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a7535-108">Attribute</span></span>|<span data-ttu-id="a7535-109">Description</span><span class="sxs-lookup"><span data-stu-id="a7535-109">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="a7535-110">Attribut à valeur booléenne facultatif qui spécifie si le système inclut des groupes Windows dans le contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a7535-110">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="a7535-111">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="a7535-111">The default is `true`.</span></span><br /><br /> <span data-ttu-id="a7535-112">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe.</span><span class="sxs-lookup"><span data-stu-id="a7535-112">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="a7535-113">Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a7535-113">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="a7535-114">Attribut à valeur booléenne facultatif qui spécifie si les appelants anonymes et non authentifiés sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a7535-114">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="a7535-115">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="a7535-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a7535-116">Lorsque l’attribut `clientCredentialType` d’une liaison a la valeur `Windows`, le système n’autorise pas d’appelants anonymes.</span><span class="sxs-lookup"><span data-stu-id="a7535-116">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="a7535-117">Cela signifie que seuls les appelants authentifiés du domaine ou du groupe de travail sont autorisés à accéder au système.</span><span class="sxs-lookup"><span data-stu-id="a7535-117">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="a7535-118">Vous pouvez substituer ce comportement en utilisant cet attribut.</span><span class="sxs-lookup"><span data-stu-id="a7535-118">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="a7535-119">N'utilisez ce paramètre qu'avec beaucoup de précaution.</span><span class="sxs-lookup"><span data-stu-id="a7535-119">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7535-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7535-120">Child Elements</span></span>  

 <span data-ttu-id="a7535-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a7535-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7535-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a7535-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a7535-123">Élément</span><span class="sxs-lookup"><span data-stu-id="a7535-123">Element</span></span>|<span data-ttu-id="a7535-124">Description</span><span class="sxs-lookup"><span data-stu-id="a7535-124">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="a7535-125">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="a7535-125">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7535-126">Notes</span><span class="sxs-lookup"><span data-stu-id="a7535-126">Remarks</span></span>  

 <span data-ttu-id="a7535-127">Utilisez cet élément pour autoriser l'accès d'utilisateurs Windows anonymes en définissant l'attribut `allowAnonymousLogons`.</span><span class="sxs-lookup"><span data-stu-id="a7535-127">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="a7535-128">Vous pouvez également indiquer s'il faut inclure des informations sur les groupes auxquels les utilisateurs appartiennent dans AuthorizationContext en définissant l'attribut `includeWindowsGroups`.</span><span class="sxs-lookup"><span data-stu-id="a7535-128">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="a7535-129">Si ce dernier a la valeur `true` (paramètre par défaut), le service peut déterminer les groupes Windows auxquels le client appartient.</span><span class="sxs-lookup"><span data-stu-id="a7535-129">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7535-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7535-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
