---
title: Élément <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2ceefdd7fab82025e89ad08d8423d57524c2e4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925563"
---
# <a name="httpdigest-element"></a><span data-ttu-id="12e54-102">\<httpDigest >, élément</span><span class="sxs-lookup"><span data-stu-id="12e54-102">\<httpDigest> Element</span></span>
<span data-ttu-id="12e54-103">Spécifie une information d'identification de type condensé utilisée lors de l'authentification du client à un service.</span><span class="sxs-lookup"><span data-stu-id="12e54-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="12e54-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="12e54-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="12e54-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="12e54-105">\<behaviors></span></span>  
<span data-ttu-id="12e54-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="12e54-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="12e54-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="12e54-107">\<behavior></span></span>  
<span data-ttu-id="12e54-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="12e54-108">\<clientCredentials></span></span>  
<span data-ttu-id="12e54-109">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="12e54-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e54-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12e54-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12e54-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="12e54-111">Attributes and Elements</span></span>  
 <span data-ttu-id="12e54-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="12e54-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12e54-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="12e54-113">Attributes</span></span>  
  
|<span data-ttu-id="12e54-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="12e54-114">Attribute</span></span>|<span data-ttu-id="12e54-115">Description</span><span class="sxs-lookup"><span data-stu-id="12e54-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="12e54-116">Définit la préférence d'emprunt d'identité que le client communique au serveur.</span><span class="sxs-lookup"><span data-stu-id="12e54-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="12e54-117">Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="12e54-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="12e54-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="12e54-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="12e54-119">Détermination Le serveur peut accéder à l’identité et aux privilèges du client, mais ne peut pas emprunter l’identité du client.</span><span class="sxs-lookup"><span data-stu-id="12e54-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="12e54-120">Emprunt d’identité Le serveur peut emprunter l’identité du contexte de sécurité du client sur le système local.</span><span class="sxs-lookup"><span data-stu-id="12e54-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="12e54-121">Délégation Le serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="12e54-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="12e54-122">Façon Le serveur ne peut pas emprunter l’identité ou identifier le client.</span><span class="sxs-lookup"><span data-stu-id="12e54-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="12e54-123">None Un niveau d’emprunt d’identité n’est pas assigné.</span><span class="sxs-lookup"><span data-stu-id="12e54-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="12e54-124">La valeur par défaut est Identification.</span><span class="sxs-lookup"><span data-stu-id="12e54-124">The default is Identification.</span></span> <span data-ttu-id="12e54-125">Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="12e54-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12e54-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="12e54-126">Child Elements</span></span>  
 <span data-ttu-id="12e54-127">Aucun</span><span class="sxs-lookup"><span data-stu-id="12e54-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12e54-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="12e54-128">Parent Elements</span></span>  
  
|<span data-ttu-id="12e54-129">Élément</span><span class="sxs-lookup"><span data-stu-id="12e54-129">Element</span></span>|<span data-ttu-id="12e54-130">Description</span><span class="sxs-lookup"><span data-stu-id="12e54-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12e54-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="12e54-131">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="12e54-132">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="12e54-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12e54-133">Notes</span><span class="sxs-lookup"><span data-stu-id="12e54-133">Remarks</span></span>  
 <span data-ttu-id="12e54-134">Un condensat est un hachage déterminé à l’aide d’un algorithme et d’un jeu d’entrées.</span><span class="sxs-lookup"><span data-stu-id="12e54-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="12e54-135">L'authentificateur et l'authentifié acceptent un algorithme et échangent les données utilisées comme entrées.</span><span class="sxs-lookup"><span data-stu-id="12e54-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="12e54-136">Le client peut calculer le hachage et l'envoyer au service.</span><span class="sxs-lookup"><span data-stu-id="12e54-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="12e54-137">Le service calcule également le hachage et compare les valeurs.</span><span class="sxs-lookup"><span data-stu-id="12e54-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="12e54-138">Une correspondance valide le client.</span><span class="sxs-lookup"><span data-stu-id="12e54-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="12e54-139">Cette fonction doit être activée avec Active Directory sur Windows et les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="12e54-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="12e54-140">Pour plus d’informations, consultez [authentification Digest dans IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="12e54-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e54-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12e54-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="12e54-142">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="12e54-142">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="12e54-143">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="12e54-143">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="12e54-144">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="12e54-144">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="12e54-145">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="12e54-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
