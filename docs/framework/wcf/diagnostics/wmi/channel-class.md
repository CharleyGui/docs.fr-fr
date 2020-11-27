---
title: Channel, classe
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: a920636e7df9609b12834366b1488c80122f9fca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274229"
---
# <a name="channel-class"></a><span data-ttu-id="b1763-102">Channel, classe</span><span class="sxs-lookup"><span data-stu-id="b1763-102">Channel class</span></span>

<span data-ttu-id="b1763-103">Channel</span><span class="sxs-lookup"><span data-stu-id="b1763-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1763-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1763-104">Syntax</span></span>  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b1763-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b1763-105">Methods</span></span>  

 <span data-ttu-id="b1763-106">La classe Channel ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="b1763-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b1763-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b1763-107">Properties</span></span>  

 <span data-ttu-id="b1763-108">La classe Channel possède les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="b1763-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="b1763-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="b1763-109">LocalAddress</span></span>  

 <span data-ttu-id="b1763-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="b1763-110">Data type: string</span></span>  
  
 <span data-ttu-id="b1763-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="b1763-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1763-112">Point de terminaison local du canal.</span><span class="sxs-lookup"><span data-stu-id="b1763-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b1763-113">ref</span><span class="sxs-lookup"><span data-stu-id="b1763-113">ref</span></span>  

 <span data-ttu-id="b1763-114">Type de données : point de terminaison</span><span class="sxs-lookup"><span data-stu-id="b1763-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="b1763-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="b1763-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1763-116">Référence au point de terminaison auquel le canal se connecte.</span><span class="sxs-lookup"><span data-stu-id="b1763-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="b1763-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="b1763-117">RemoteAddress</span></span>  

 <span data-ttu-id="b1763-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="b1763-118">Data type: string</span></span>  
  
 <span data-ttu-id="b1763-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="b1763-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1763-120">Adresse distante associée au canal.</span><span class="sxs-lookup"><span data-stu-id="b1763-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="b1763-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="b1763-121">SessionId</span></span>  

 <span data-ttu-id="b1763-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="b1763-122">Data type: string</span></span>  
  
 <span data-ttu-id="b1763-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="b1763-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1763-124">Id de session actuel, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="b1763-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="b1763-125">Type</span><span class="sxs-lookup"><span data-stu-id="b1763-125">Type</span></span>  

 <span data-ttu-id="b1763-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="b1763-126">Data type: string</span></span>  
  
 <span data-ttu-id="b1763-127">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="b1763-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1763-128">Type du canal.</span><span class="sxs-lookup"><span data-stu-id="b1763-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1763-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b1763-129">Requirements</span></span>  
  
|<span data-ttu-id="b1763-130">MOF</span><span class="sxs-lookup"><span data-stu-id="b1763-130">MOF</span></span>|<span data-ttu-id="b1763-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b1763-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b1763-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="b1763-132">Namespace</span></span>|<span data-ttu-id="b1763-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b1763-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1763-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1763-134">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
