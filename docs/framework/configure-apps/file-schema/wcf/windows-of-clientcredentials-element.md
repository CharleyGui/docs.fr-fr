---
title: <windows>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399127"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="b62b4-102">\<windows>d' \<clientCredentials> élément</span><span class="sxs-lookup"><span data-stu-id="b62b4-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="b62b4-103">Spécifie les paramètres pour des informations d'identification Windows à utiliser pour représenter le client.</span><span class="sxs-lookup"><span data-stu-id="b62b4-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="b62b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b62b4-104">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b62b4-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b62b4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b62b4-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b62b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b62b4-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b62b4-107">Attributes</span></span>  
  
|<span data-ttu-id="b62b4-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b62b4-108">Attribute</span></span>|<span data-ttu-id="b62b4-109">Description</span><span class="sxs-lookup"><span data-stu-id="b62b4-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="b62b4-110">Définit la préférence d'emprunt d'identité que le client communique au serveur.</span><span class="sxs-lookup"><span data-stu-id="b62b4-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="b62b4-111">Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="b62b4-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="b62b4-112">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b62b4-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b62b4-113">-Identification : le serveur peut accéder à l’identité et aux privilèges du client, mais ne peut pas emprunter l’identité du client.</span><span class="sxs-lookup"><span data-stu-id="b62b4-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="b62b4-114">-Emprunt d’identité : le serveur peut emprunter l’identité du contexte de sécurité du client sur le système local.</span><span class="sxs-lookup"><span data-stu-id="b62b4-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="b62b4-115">-Delegation : le serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="b62b4-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="b62b4-116">-Anonymous : le serveur ne peut pas emprunter l’identité ou identifier le client.</span><span class="sxs-lookup"><span data-stu-id="b62b4-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="b62b4-117">-None : aucun niveau d’emprunt d’identité n’est assigné.</span><span class="sxs-lookup"><span data-stu-id="b62b4-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="b62b4-118">La valeur par défaut est Identification.</span><span class="sxs-lookup"><span data-stu-id="b62b4-118">The default is Identification.</span></span> <span data-ttu-id="b62b4-119">Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="b62b4-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="b62b4-120">L'affectation de la valeur `true` à cette propriété permet de rétrograder l'authentification à NTLM si Kerberos n'est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="b62b4-120">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="b62b4-121">Si vous affectez la valeur à cette propriété `false` , Windows Communication Foundation (WCF) est le meilleur effort pour lever une exception si NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b62b4-121">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="b62b4-122">Notez que l'affectation de la valeur `false` à cette propriété peut ne pas empêcher la transmission des informations d'identification NTLM.</span><span class="sxs-lookup"><span data-stu-id="b62b4-122">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b62b4-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b62b4-123">Child Elements</span></span>  
 <span data-ttu-id="b62b4-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b62b4-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b62b4-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b62b4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b62b4-126">Élément</span><span class="sxs-lookup"><span data-stu-id="b62b4-126">Element</span></span>|<span data-ttu-id="b62b4-127">Description</span><span class="sxs-lookup"><span data-stu-id="b62b4-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="b62b4-128">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="b62b4-128">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b62b4-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b62b4-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="b62b4-130">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="b62b4-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b62b4-131">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="b62b4-131">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b62b4-132">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="b62b4-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
