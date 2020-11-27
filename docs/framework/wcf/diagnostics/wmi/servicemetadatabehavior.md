---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 921a880dad0d77558a70dff8a09f75c25a3cbb8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262279"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="15fcc-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="15fcc-102">ServiceMetadataBehavior</span></span>

<span data-ttu-id="15fcc-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="15fcc-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15fcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15fcc-104">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="15fcc-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="15fcc-105">Methods</span></span>  

 <span data-ttu-id="15fcc-106">La classe ServiceMetadataBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="15fcc-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="15fcc-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="15fcc-107">Properties</span></span>  

 <span data-ttu-id="15fcc-108">La classe ServiceMetadataBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="15fcc-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="15fcc-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="15fcc-109">ExternalMetadataLocation</span></span>  

 <span data-ttu-id="15fcc-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="15fcc-110">Data type: string</span></span>  
  
 <span data-ttu-id="15fcc-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="15fcc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15fcc-112">Définit l'emplacement vers lequel le service redirige les demandes de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="15fcc-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="15fcc-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="15fcc-113">HttpGetEnabled</span></span>  

 <span data-ttu-id="15fcc-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="15fcc-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="15fcc-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="15fcc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15fcc-116">Vérifie si le service publie son WSDL à l'adresse contrôlée par l'attribut `HttpGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="15fcc-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="15fcc-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="15fcc-117">HttpGetUrl</span></span>  

 <span data-ttu-id="15fcc-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="15fcc-118">Data type: string</span></span>  
  
 <span data-ttu-id="15fcc-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="15fcc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15fcc-120">Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTP.</span><span class="sxs-lookup"><span data-stu-id="15fcc-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="15fcc-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="15fcc-121">HttpsGetEnabled</span></span>  

 <span data-ttu-id="15fcc-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="15fcc-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="15fcc-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="15fcc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15fcc-124">Vérifie si le service publie son WSDL sur HTTPS à l'adresse contrôlée par l'attribut `HttpsGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="15fcc-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="15fcc-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="15fcc-125">HttpsGetUrl</span></span>  

 <span data-ttu-id="15fcc-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="15fcc-126">Data type: string</span></span>  
  
 <span data-ttu-id="15fcc-127">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="15fcc-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15fcc-128">Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="15fcc-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15fcc-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="15fcc-129">Requirements</span></span>  
  
|<span data-ttu-id="15fcc-130">MOF</span><span class="sxs-lookup"><span data-stu-id="15fcc-130">MOF</span></span>|<span data-ttu-id="15fcc-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="15fcc-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="15fcc-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="15fcc-132">Namespace</span></span>|<span data-ttu-id="15fcc-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="15fcc-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15fcc-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15fcc-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
