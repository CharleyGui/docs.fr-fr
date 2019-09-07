---
title: <windows>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399127"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="c33a2-102">\<> Windows de \<l’élément ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c33a2-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="c33a2-103">Spécifie les paramètres pour des informations d'identification Windows à utiliser pour représenter le client.</span><span class="sxs-lookup"><span data-stu-id="c33a2-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
<span data-ttu-id="c33a2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c33a2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c33a2-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c33a2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c33a2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c33a2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c33a2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c33a2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="c33a2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c33a2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="c33a2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c33a2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="c33a2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Windows**</span><span class="sxs-lookup"><span data-stu-id="c33a2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c33a2-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c33a2-111">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c33a2-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c33a2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c33a2-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c33a2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c33a2-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="c33a2-114">Attributes</span></span>  
  
|<span data-ttu-id="c33a2-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="c33a2-115">Attribute</span></span>|<span data-ttu-id="c33a2-116">Description</span><span class="sxs-lookup"><span data-stu-id="c33a2-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="c33a2-117">Définit la préférence d'emprunt d'identité que le client communique au serveur.</span><span class="sxs-lookup"><span data-stu-id="c33a2-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="c33a2-118">Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="c33a2-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="c33a2-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c33a2-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c33a2-120">Détermination Le serveur peut accéder à l’identité et aux privilèges du client, mais ne peut pas emprunter l’identité du client.</span><span class="sxs-lookup"><span data-stu-id="c33a2-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="c33a2-121">Emprunt d’identité Le serveur peut emprunter l’identité du contexte de sécurité du client sur le système local.</span><span class="sxs-lookup"><span data-stu-id="c33a2-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="c33a2-122">Délégation Le serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="c33a2-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="c33a2-123">Façon Le serveur ne peut pas emprunter l’identité ou identifier le client.</span><span class="sxs-lookup"><span data-stu-id="c33a2-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="c33a2-124">None Un niveau d’emprunt d’identité n’est pas assigné.</span><span class="sxs-lookup"><span data-stu-id="c33a2-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="c33a2-125">La valeur par défaut est Identification.</span><span class="sxs-lookup"><span data-stu-id="c33a2-125">The default is Identification.</span></span> <span data-ttu-id="c33a2-126">Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="c33a2-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="c33a2-127">L'affectation de la valeur `true` à cette propriété permet de rétrograder l'authentification à NTLM si Kerberos n'est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="c33a2-127">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="c33a2-128">Si vous affectez `false` la valeur à cette propriété, Windows Communication Foundation (WCF) est le meilleur effort pour lever une exception si NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c33a2-128">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="c33a2-129">Notez que l'affectation de la valeur `false` à cette propriété peut ne pas empêcher la transmission des informations d'identification NTLM.</span><span class="sxs-lookup"><span data-stu-id="c33a2-129">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c33a2-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c33a2-130">Child Elements</span></span>  
 <span data-ttu-id="c33a2-131">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c33a2-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c33a2-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c33a2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="c33a2-133">Élément</span><span class="sxs-lookup"><span data-stu-id="c33a2-133">Element</span></span>|<span data-ttu-id="c33a2-134">Description</span><span class="sxs-lookup"><span data-stu-id="c33a2-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c33a2-135">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="c33a2-135">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="c33a2-136">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="c33a2-136">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c33a2-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c33a2-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="c33a2-138">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="c33a2-138">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c33a2-139">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="c33a2-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c33a2-140">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="c33a2-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
