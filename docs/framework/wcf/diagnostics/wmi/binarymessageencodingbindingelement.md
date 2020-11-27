---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: eb174d12731d7f1bc78f4d709cf043daf2346bd2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269793"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="023c3-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="023c3-102">BinaryMessageEncodingBindingElement</span></span>

<span data-ttu-id="023c3-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="023c3-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="023c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="023c3-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="023c3-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="023c3-105">Methods</span></span>  

 <span data-ttu-id="023c3-106">La classe BinaryMessageEncodingBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="023c3-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="023c3-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="023c3-107">Properties</span></span>  

 <span data-ttu-id="023c3-108">La classe BinaryMessageEncodingBindingElement a les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="023c3-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="023c3-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="023c3-109">MaxReadPoolSize</span></span>  

 <span data-ttu-id="023c3-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="023c3-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="023c3-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="023c3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023c3-112">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="023c3-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="023c3-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="023c3-113">MaxSessionSize</span></span>  

 <span data-ttu-id="023c3-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="023c3-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="023c3-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="023c3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023c3-116">Valeur qui spécifie la taille, en octets, de la mémoire tampon utilisée pour l'encodage.</span><span class="sxs-lookup"><span data-stu-id="023c3-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="023c3-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="023c3-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="023c3-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="023c3-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="023c3-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="023c3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023c3-120">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="023c3-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="023c3-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="023c3-121">ReaderQuotas</span></span>  

 <span data-ttu-id="023c3-122">Type de données : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="023c3-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="023c3-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="023c3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023c3-124">Quotas des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="023c3-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="023c3-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="023c3-125">Requirements</span></span>  
  
|<span data-ttu-id="023c3-126">MOF</span><span class="sxs-lookup"><span data-stu-id="023c3-126">MOF</span></span>|<span data-ttu-id="023c3-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="023c3-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="023c3-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="023c3-128">Namespace</span></span>|<span data-ttu-id="023c3-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="023c3-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="023c3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="023c3-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
