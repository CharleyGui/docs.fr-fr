---
title: <windows>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940310"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="01cda-102">\<> Windows de \<l’élément ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="01cda-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="01cda-103">Spécifie les paramètres pour des informations d'identification Windows à utiliser pour représenter le client.</span><span class="sxs-lookup"><span data-stu-id="01cda-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="01cda-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="01cda-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="01cda-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="01cda-105">\<behaviors></span></span>  
<span data-ttu-id="01cda-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="01cda-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="01cda-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="01cda-107">\<behavior></span></span>  
<span data-ttu-id="01cda-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="01cda-108">\<clientCredentials></span></span>  
<span data-ttu-id="01cda-109">\<windows></span><span class="sxs-lookup"><span data-stu-id="01cda-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01cda-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01cda-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01cda-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="01cda-111">Attributes and Elements</span></span>  
 <span data-ttu-id="01cda-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="01cda-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01cda-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="01cda-113">Attributes</span></span>  
  
|<span data-ttu-id="01cda-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="01cda-114">Attribute</span></span>|<span data-ttu-id="01cda-115">Description</span><span class="sxs-lookup"><span data-stu-id="01cda-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="01cda-116">Définit la préférence d'emprunt d'identité que le client communique au serveur.</span><span class="sxs-lookup"><span data-stu-id="01cda-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="01cda-117">Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="01cda-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="01cda-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="01cda-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="01cda-119">Détermination Le serveur peut accéder à l’identité et aux privilèges du client, mais ne peut pas emprunter l’identité du client.</span><span class="sxs-lookup"><span data-stu-id="01cda-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="01cda-120">Emprunt d’identité Le serveur peut emprunter l’identité du contexte de sécurité du client sur le système local.</span><span class="sxs-lookup"><span data-stu-id="01cda-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="01cda-121">Délégation Le serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="01cda-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="01cda-122">Façon Le serveur ne peut pas emprunter l’identité ou identifier le client.</span><span class="sxs-lookup"><span data-stu-id="01cda-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="01cda-123">None Un niveau d’emprunt d’identité n’est pas assigné.</span><span class="sxs-lookup"><span data-stu-id="01cda-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="01cda-124">La valeur par défaut est Identification.</span><span class="sxs-lookup"><span data-stu-id="01cda-124">The default is Identification.</span></span> <span data-ttu-id="01cda-125">Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="01cda-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="01cda-126">L'affectation de la valeur `true` à cette propriété permet de rétrograder l'authentification à NTLM si Kerberos n'est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="01cda-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="01cda-127">Si vous affectez `false` la valeur à cette propriété, Windows Communication Foundation (WCF) est le meilleur effort pour lever une exception si NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="01cda-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="01cda-128">Notez que l'affectation de la valeur `false` à cette propriété peut ne pas empêcher la transmission des informations d'identification NTLM.</span><span class="sxs-lookup"><span data-stu-id="01cda-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01cda-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="01cda-129">Child Elements</span></span>  
 <span data-ttu-id="01cda-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="01cda-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01cda-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="01cda-131">Parent Elements</span></span>  
  
|<span data-ttu-id="01cda-132">Élément</span><span class="sxs-lookup"><span data-stu-id="01cda-132">Element</span></span>|<span data-ttu-id="01cda-133">Description</span><span class="sxs-lookup"><span data-stu-id="01cda-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01cda-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="01cda-134">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="01cda-135">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="01cda-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01cda-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01cda-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="01cda-137">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="01cda-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="01cda-138">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="01cda-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="01cda-139">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="01cda-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
