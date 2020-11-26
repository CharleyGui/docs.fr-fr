---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 45bfcd069391156bc85cc4c26f2b172770197a9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234841"
---
# <a name="transportbindingelement"></a><span data-ttu-id="a855e-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="a855e-102">TransportBindingElement</span></span>

<span data-ttu-id="a855e-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="a855e-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a855e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a855e-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a855e-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a855e-105">Methods</span></span>  

 <span data-ttu-id="a855e-106">La classe TransportBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="a855e-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a855e-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a855e-107">Properties</span></span>  

 <span data-ttu-id="a855e-108">La classe TransportBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a855e-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="a855e-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="a855e-109">ManualAddressing</span></span>  

 <span data-ttu-id="a855e-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="a855e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a855e-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="a855e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a855e-112">Valeur booléenne qui spécifie si l'utilisateur souhaite prendre le contrôle de l'adressage des messages.</span><span class="sxs-lookup"><span data-stu-id="a855e-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="a855e-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a855e-113">MaxBufferPoolSize</span></span>  

 <span data-ttu-id="a855e-114">Type de données : sint64</span><span class="sxs-lookup"><span data-stu-id="a855e-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="a855e-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="a855e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a855e-116">Taille maximale du pool de mémoires tampons pour la liaison.</span><span class="sxs-lookup"><span data-stu-id="a855e-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="a855e-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a855e-117">MaxReceivedMessageSize</span></span>  

 <span data-ttu-id="a855e-118">Type de données : sint64</span><span class="sxs-lookup"><span data-stu-id="a855e-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="a855e-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="a855e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a855e-120">Taille maximale d’un message traité par cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a855e-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="a855e-121">Schéma</span><span class="sxs-lookup"><span data-stu-id="a855e-121">Scheme</span></span>  

 <span data-ttu-id="a855e-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="a855e-122">Data type: string</span></span>  
  
 <span data-ttu-id="a855e-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="a855e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a855e-124">Schéma d'URI pour le transport.</span><span class="sxs-lookup"><span data-stu-id="a855e-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a855e-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a855e-125">Requirements</span></span>  
  
|<span data-ttu-id="a855e-126">MOF</span><span class="sxs-lookup"><span data-stu-id="a855e-126">MOF</span></span>|<span data-ttu-id="a855e-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a855e-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a855e-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="a855e-128">Namespace</span></span>|<span data-ttu-id="a855e-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a855e-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a855e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a855e-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>
