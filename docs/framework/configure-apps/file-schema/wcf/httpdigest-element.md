---
title: Élément <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 0ffaba218d31a77407c598f8b7fa0260daa4e39c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556900"
---
# <a name="httpdigest-element"></a><span data-ttu-id="73514-102">Élément \<httpDigest></span><span class="sxs-lookup"><span data-stu-id="73514-102">\<httpDigest> Element</span></span>
<span data-ttu-id="73514-103">Spécifie une information d'identification de type condensé utilisée lors de l'authentification du client à un service.</span><span class="sxs-lookup"><span data-stu-id="73514-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="73514-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73514-104">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73514-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="73514-105">Attributes and Elements</span></span>  
 <span data-ttu-id="73514-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="73514-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73514-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="73514-107">Attributes</span></span>  
  
|<span data-ttu-id="73514-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="73514-108">Attribute</span></span>|<span data-ttu-id="73514-109">Description</span><span class="sxs-lookup"><span data-stu-id="73514-109">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="73514-110">Définit la préférence d'emprunt d'identité que le client communique au serveur.</span><span class="sxs-lookup"><span data-stu-id="73514-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="73514-111">Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="73514-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="73514-112">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="73514-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="73514-113">-Identification : le serveur peut accéder à l’identité et aux privilèges du client, mais ne peut pas emprunter l’identité du client.</span><span class="sxs-lookup"><span data-stu-id="73514-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="73514-114">-Emprunt d’identité : le serveur peut emprunter l’identité du contexte de sécurité du client sur le système local.</span><span class="sxs-lookup"><span data-stu-id="73514-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="73514-115">-Delegation : le serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="73514-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="73514-116">-Anonymous : le serveur ne peut pas emprunter l’identité ou identifier le client.</span><span class="sxs-lookup"><span data-stu-id="73514-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="73514-117">-None : aucun niveau d’emprunt d’identité n’est assigné.</span><span class="sxs-lookup"><span data-stu-id="73514-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="73514-118">La valeur par défaut est Identification.</span><span class="sxs-lookup"><span data-stu-id="73514-118">The default is Identification.</span></span> <span data-ttu-id="73514-119">Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="73514-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73514-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="73514-120">Child Elements</span></span>  
 <span data-ttu-id="73514-121">None</span><span class="sxs-lookup"><span data-stu-id="73514-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73514-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="73514-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73514-123">Élément</span><span class="sxs-lookup"><span data-stu-id="73514-123">Element</span></span>|<span data-ttu-id="73514-124">Description</span><span class="sxs-lookup"><span data-stu-id="73514-124">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="73514-125">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="73514-125">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73514-126">Notes</span><span class="sxs-lookup"><span data-stu-id="73514-126">Remarks</span></span>  
 <span data-ttu-id="73514-127">Un condensat est un hachage déterminé à l’aide d’un algorithme et d’un jeu d’entrées.</span><span class="sxs-lookup"><span data-stu-id="73514-127">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="73514-128">L'authentificateur et l'authentifié acceptent un algorithme et échangent les données utilisées comme entrées.</span><span class="sxs-lookup"><span data-stu-id="73514-128">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="73514-129">Le client peut calculer le hachage et l'envoyer au service.</span><span class="sxs-lookup"><span data-stu-id="73514-129">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="73514-130">Le service calcule également le hachage et compare les valeurs.</span><span class="sxs-lookup"><span data-stu-id="73514-130">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="73514-131">Une correspondance valide le client.</span><span class="sxs-lookup"><span data-stu-id="73514-131">A match validates the client.</span></span>  
  
 <span data-ttu-id="73514-132">Cette fonction doit être activée avec Active Directory sur Windows et les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="73514-132">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="73514-133">Pour plus d’informations, consultez [authentification Digest dans IIS 6,0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="73514-133">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73514-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73514-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="73514-135">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="73514-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="73514-136">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="73514-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="73514-137">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="73514-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="73514-138">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="73514-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
