---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: dba4abd74cdddeb2b641feec5902413fe0704b1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262292"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="baf87-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="baf87-102">ServiceDebugBehavior</span></span>

<span data-ttu-id="baf87-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="baf87-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baf87-104">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="baf87-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="baf87-105">Methods</span></span>  

 <span data-ttu-id="baf87-106">La classe ServiceDebugBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="baf87-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="baf87-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="baf87-107">Properties</span></span>  

 <span data-ttu-id="baf87-108">La classe ServiceDebugBehavior possède les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="baf87-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="baf87-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="baf87-109">HttpHelpPageEnabled</span></span>  

 <span data-ttu-id="baf87-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="baf87-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="baf87-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="baf87-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="baf87-112">Vérifie si le service publie son WSDL à l'adresse contrôlée par l'attribut `HttpGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="baf87-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="baf87-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="baf87-113">HttpHelpPageUrl</span></span>  

 <span data-ttu-id="baf87-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="baf87-114">Data type: string</span></span>  
  
 <span data-ttu-id="baf87-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="baf87-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="baf87-116">Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTP.</span><span class="sxs-lookup"><span data-stu-id="baf87-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="baf87-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="baf87-117">HttpsHelpPageEnabled</span></span>  

 <span data-ttu-id="baf87-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="baf87-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="baf87-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="baf87-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="baf87-120">Vérifie si le service publie son WSDL sur HTTPS à l'adresse contrôlée par l'attribut `HttpsGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="baf87-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="baf87-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="baf87-121">HttpsHelpPageUrl</span></span>  

 <span data-ttu-id="baf87-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="baf87-122">Data type: string</span></span>  
  
 <span data-ttu-id="baf87-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="baf87-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="baf87-124">Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="baf87-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="baf87-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="baf87-125">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="baf87-126">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="baf87-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="baf87-127">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="baf87-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="baf87-128">Spécifie s'il convient d'inclure des informations d'exception gérées dans les détails des fautes SOAP renvoyées aux clients à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="baf87-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baf87-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="baf87-129">Requirements</span></span>  
  
|<span data-ttu-id="baf87-130">MOF</span><span class="sxs-lookup"><span data-stu-id="baf87-130">MOF</span></span>|<span data-ttu-id="baf87-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="baf87-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="baf87-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="baf87-132">Namespace</span></span>|<span data-ttu-id="baf87-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="baf87-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="baf87-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baf87-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
