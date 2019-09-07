---
title: Élément <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: f392ebf4eeb6a008952fd4d5ef4e301e57f6eb31
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397989"
---
# <a name="httpdigest-element"></a><span data-ttu-id="e6786-102">\<httpDigest >, élément</span><span class="sxs-lookup"><span data-stu-id="e6786-102">\<httpDigest> Element</span></span>
<span data-ttu-id="e6786-103">Spécifie une information d'identification de type condensé utilisée lors de l'authentification du client à un service.</span><span class="sxs-lookup"><span data-stu-id="e6786-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="e6786-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e6786-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6786-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e6786-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e6786-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6786-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e6786-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6786-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="e6786-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6786-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="e6786-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e6786-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="e6786-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpDigest >**</span><span class="sxs-lookup"><span data-stu-id="e6786-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6786-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6786-111">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6786-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e6786-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e6786-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e6786-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6786-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="e6786-114">Attributes</span></span>  
  
|<span data-ttu-id="e6786-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="e6786-115">Attribute</span></span>|<span data-ttu-id="e6786-116">Description</span><span class="sxs-lookup"><span data-stu-id="e6786-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="e6786-117">Définit la préférence d'emprunt d'identité que le client communique au serveur.</span><span class="sxs-lookup"><span data-stu-id="e6786-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="e6786-118">Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="e6786-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="e6786-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6786-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e6786-120">Détermination Le serveur peut accéder à l’identité et aux privilèges du client, mais ne peut pas emprunter l’identité du client.</span><span class="sxs-lookup"><span data-stu-id="e6786-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="e6786-121">Emprunt d’identité Le serveur peut emprunter l’identité du contexte de sécurité du client sur le système local.</span><span class="sxs-lookup"><span data-stu-id="e6786-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="e6786-122">Délégation Le serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="e6786-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="e6786-123">Façon Le serveur ne peut pas emprunter l’identité ou identifier le client.</span><span class="sxs-lookup"><span data-stu-id="e6786-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="e6786-124">None Un niveau d’emprunt d’identité n’est pas assigné.</span><span class="sxs-lookup"><span data-stu-id="e6786-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="e6786-125">La valeur par défaut est Identification.</span><span class="sxs-lookup"><span data-stu-id="e6786-125">The default is Identification.</span></span> <span data-ttu-id="e6786-126">Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="e6786-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6786-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e6786-127">Child Elements</span></span>  
 <span data-ttu-id="e6786-128">Aucun</span><span class="sxs-lookup"><span data-stu-id="e6786-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6786-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e6786-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e6786-130">Élément</span><span class="sxs-lookup"><span data-stu-id="e6786-130">Element</span></span>|<span data-ttu-id="e6786-131">Description</span><span class="sxs-lookup"><span data-stu-id="e6786-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6786-132">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e6786-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="e6786-133">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="e6786-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6786-134">Notes</span><span class="sxs-lookup"><span data-stu-id="e6786-134">Remarks</span></span>  
 <span data-ttu-id="e6786-135">Un condensat est un hachage déterminé à l’aide d’un algorithme et d’un jeu d’entrées.</span><span class="sxs-lookup"><span data-stu-id="e6786-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="e6786-136">L'authentificateur et l'authentifié acceptent un algorithme et échangent les données utilisées comme entrées.</span><span class="sxs-lookup"><span data-stu-id="e6786-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="e6786-137">Le client peut calculer le hachage et l'envoyer au service.</span><span class="sxs-lookup"><span data-stu-id="e6786-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="e6786-138">Le service calcule également le hachage et compare les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e6786-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="e6786-139">Une correspondance valide le client.</span><span class="sxs-lookup"><span data-stu-id="e6786-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="e6786-140">Cette fonction doit être activée avec Active Directory sur Windows et les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="e6786-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="e6786-141">Pour plus d’informations, consultez [authentification Digest dans IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="e6786-141">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6786-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6786-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="e6786-143">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="e6786-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e6786-144">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="e6786-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="e6786-145">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="e6786-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e6786-146">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e6786-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
