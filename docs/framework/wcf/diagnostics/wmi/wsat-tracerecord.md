---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 0409277821a7cca3f97fcec1bb383aba9583a1f6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262214"
---
# <a name="wsat_tracerecord"></a><span data-ttu-id="ce4c3-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="ce4c3-102">WSAT_TraceRecord</span></span>

<span data-ttu-id="ce4c3-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="ce4c3-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce4c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce4c3-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ce4c3-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ce4c3-105">Methods</span></span>  

 <span data-ttu-id="ce4c3-106">La classe WSAT_TraceRecord ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="ce4c3-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ce4c3-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ce4c3-107">Properties</span></span>  

 <span data-ttu-id="ce4c3-108">La classe WSAT_TraceRecord a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce4c3-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="ce4c3-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="ce4c3-109">ActivityID</span></span>  

 <span data-ttu-id="ce4c3-110">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="ce4c3-110">Data type: object</span></span>  
<span data-ttu-id="ce4c3-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="ce4c3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce4c3-112">ID d'activité de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="ce4c3-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="ce4c3-113">EventID</span><span class="sxs-lookup"><span data-stu-id="ce4c3-113">EventID</span></span>  

 <span data-ttu-id="ce4c3-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="ce4c3-114">Data type: sint32</span></span>  
<span data-ttu-id="ce4c3-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="ce4c3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce4c3-116">ID d'événement de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="ce4c3-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="ce4c3-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="ce4c3-117">TraceRecord</span></span>  

 <span data-ttu-id="ce4c3-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ce4c3-118">Data type: string</span></span>  
<span data-ttu-id="ce4c3-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="ce4c3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce4c3-120">Enregistrement de suivi</span><span class="sxs-lookup"><span data-stu-id="ce4c3-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce4c3-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce4c3-121">Requirements</span></span>  
  
|<span data-ttu-id="ce4c3-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ce4c3-122">MOF</span></span>|<span data-ttu-id="ce4c3-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ce4c3-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ce4c3-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="ce4c3-124">Namespace</span></span>|<span data-ttu-id="ce4c3-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ce4c3-125">Defined in root\ServiceModel</span></span>|
