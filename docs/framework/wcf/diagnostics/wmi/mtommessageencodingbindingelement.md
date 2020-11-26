---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: b4d8503543c93d0112fc39e4b2dba5434bc56472
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237402"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="12f7f-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="12f7f-102">MtomMessageEncodingBindingElement</span></span>

<span data-ttu-id="12f7f-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="12f7f-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f7f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12f7f-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="12f7f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="12f7f-105">Methods</span></span>  

 <span data-ttu-id="12f7f-106">La classe MtomMessageEncodingBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="12f7f-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="12f7f-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="12f7f-107">Properties</span></span>  

 <span data-ttu-id="12f7f-108">La classe MtomMessageEncodingBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="12f7f-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="12f7f-109">Encodage</span><span class="sxs-lookup"><span data-stu-id="12f7f-109">Encoding</span></span>  

 <span data-ttu-id="12f7f-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="12f7f-110">Data type: string</span></span>  
  
 <span data-ttu-id="12f7f-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="12f7f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12f7f-112">Encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="12f7f-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="12f7f-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="12f7f-113">MaxReadPoolSize</span></span>  

 <span data-ttu-id="12f7f-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="12f7f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="12f7f-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="12f7f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12f7f-116">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="12f7f-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="12f7f-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="12f7f-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="12f7f-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="12f7f-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="12f7f-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="12f7f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12f7f-120">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="12f7f-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="12f7f-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="12f7f-121">ReaderQuotas</span></span>  

 <span data-ttu-id="12f7f-122">Type de données : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="12f7f-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="12f7f-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="12f7f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12f7f-124">Quotas des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="12f7f-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f7f-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="12f7f-125">Requirements</span></span>  
  
|<span data-ttu-id="12f7f-126">MOF</span><span class="sxs-lookup"><span data-stu-id="12f7f-126">MOF</span></span>|<span data-ttu-id="12f7f-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="12f7f-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="12f7f-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="12f7f-128">Namespace</span></span>|<span data-ttu-id="12f7f-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="12f7f-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12f7f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12f7f-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
