---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c63e1b3de464b306f46e2f0935b1208d7262925a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274190"
---
# <a name="clientcredentials"></a><span data-ttu-id="59073-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="59073-102">ClientCredentials</span></span>

<span data-ttu-id="59073-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="59073-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59073-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59073-104">Syntax</span></span>  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="59073-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="59073-105">Methods</span></span>  

 <span data-ttu-id="59073-106">La classe ClientCredentials ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="59073-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="59073-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="59073-107">Properties</span></span>  

 <span data-ttu-id="59073-108">La classe ClientCredentials a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59073-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="59073-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="59073-109">ClientCertificate</span></span>  

 <span data-ttu-id="59073-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="59073-110">Data type: string</span></span>  
  
 <span data-ttu-id="59073-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="59073-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59073-112">Certificat X.509 que le client utilise pour s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="59073-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="59073-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="59073-113">HttpDigest</span></span>  

 <span data-ttu-id="59073-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="59073-114">Data type: string</span></span>  
  
 <span data-ttu-id="59073-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="59073-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59073-116">Informations d’identification HTTP Digest actuelles.</span><span class="sxs-lookup"><span data-stu-id="59073-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="59073-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="59073-117">IssuedToken</span></span>  

 <span data-ttu-id="59073-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="59073-118">Data type: string</span></span>  
  
 <span data-ttu-id="59073-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="59073-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59073-120">Adresse de point de terminaison et liaison utilisées pour contacter le service de jetons de sécurité local.</span><span class="sxs-lookup"><span data-stu-id="59073-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="59073-121">Homologue</span><span class="sxs-lookup"><span data-stu-id="59073-121">Peer</span></span>  

 <span data-ttu-id="59073-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="59073-122">Data type: string</span></span>  
  
 <span data-ttu-id="59073-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="59073-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59073-124">Informations d'identification que le nœud d'homologue utilise pour s'authentifier auprès d'autres nœuds dans la maille.</span><span class="sxs-lookup"><span data-stu-id="59073-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="59073-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="59073-125">ServiceCertificate</span></span>  

 <span data-ttu-id="59073-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="59073-126">Data type: string</span></span>  
  
 <span data-ttu-id="59073-127">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="59073-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59073-128">Certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="59073-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="59073-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="59073-129">SupportInteractive</span></span>  

 <span data-ttu-id="59073-130">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="59073-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="59073-131">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="59073-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59073-132">Valeur booléenne qui spécifie si les informations d'identification prennent en charge la négociation interactive.</span><span class="sxs-lookup"><span data-stu-id="59073-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="59073-133">UserName</span><span class="sxs-lookup"><span data-stu-id="59073-133">UserName</span></span>  

 <span data-ttu-id="59073-134">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="59073-134">Data type: string</span></span>  
  
 <span data-ttu-id="59073-135">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="59073-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59073-136">Nom d'utilisateur et mot de passe que le client utilise pour s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="59073-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="59073-137">Windows</span><span class="sxs-lookup"><span data-stu-id="59073-137">Windows</span></span>  

 <span data-ttu-id="59073-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="59073-138">Data type: string</span></span>  
  
 <span data-ttu-id="59073-139">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="59073-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59073-140">Informations d'identification que le client utilise pour s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="59073-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59073-141">Spécifications</span><span class="sxs-lookup"><span data-stu-id="59073-141">Requirements</span></span>  
  
|<span data-ttu-id="59073-142">MOF</span><span class="sxs-lookup"><span data-stu-id="59073-142">MOF</span></span>|<span data-ttu-id="59073-143">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="59073-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="59073-144">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="59073-144">Namespace</span></span>|<span data-ttu-id="59073-145">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="59073-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59073-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59073-146">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
