---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 2de417e4a4f5c6197551c1408da6907e2fa7c635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269000"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="177bc-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="177bc-102">PeerSecuritySettings</span></span>

<span data-ttu-id="177bc-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="177bc-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="177bc-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="177bc-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="177bc-105">Methods</span></span>  

 <span data-ttu-id="177bc-106">La classe PeerSecuritySettings ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="177bc-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="177bc-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="177bc-107">Properties</span></span>  

 <span data-ttu-id="177bc-108">La classe PeerSecuritySettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="177bc-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="177bc-109">Mode</span><span class="sxs-lookup"><span data-stu-id="177bc-109">Mode</span></span>  

 <span data-ttu-id="177bc-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="177bc-110">Data type: string</span></span>  
  
 <span data-ttu-id="177bc-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="177bc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="177bc-112">Utilisation ou non d'une sécurité au niveau du message et au niveau du transport par un point de terminaison configuré avec la liaison.</span><span class="sxs-lookup"><span data-stu-id="177bc-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="177bc-113">Transport</span><span class="sxs-lookup"><span data-stu-id="177bc-113">Transport</span></span>  

 <span data-ttu-id="177bc-114">Type de données : PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="177bc-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="177bc-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="177bc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="177bc-116">Paramètres de sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="177bc-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="177bc-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="177bc-117">Requirements</span></span>  
  
|<span data-ttu-id="177bc-118">MOF</span><span class="sxs-lookup"><span data-stu-id="177bc-118">MOF</span></span>|<span data-ttu-id="177bc-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="177bc-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="177bc-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="177bc-120">Namespace</span></span>|<span data-ttu-id="177bc-121">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="177bc-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="177bc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="177bc-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
