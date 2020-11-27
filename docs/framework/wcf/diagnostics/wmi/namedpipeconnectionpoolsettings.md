---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8422e1adf9a8914b631431eba5c9c0ed058cd0f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258021"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="4a390-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4a390-102">NamedPipeConnectionPoolSettings</span></span>

<span data-ttu-id="4a390-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4a390-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a390-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a390-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4a390-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4a390-105">Methods</span></span>  

 <span data-ttu-id="4a390-106">La classe NamedPipeConnectionPoolSettings ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="4a390-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4a390-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4a390-107">Properties</span></span>  

 <span data-ttu-id="4a390-108">La classe NamedPipeConnectionPoolSettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a390-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="4a390-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="4a390-109">GroupName</span></span>  

 <span data-ttu-id="4a390-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="4a390-110">Data type: string</span></span>  
  
 <span data-ttu-id="4a390-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="4a390-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a390-112">Nom de groupe du pool de connexions utilisé par l'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="4a390-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="4a390-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="4a390-113">IdleTimeout</span></span>  

 <span data-ttu-id="4a390-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="4a390-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="4a390-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="4a390-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a390-116">Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="4a390-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="4a390-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="4a390-117">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="4a390-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="4a390-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a390-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="4a390-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a390-120">Nombre maximal de connexions sortantes pour chaque point de terminaison sur le client.</span><span class="sxs-lookup"><span data-stu-id="4a390-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a390-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4a390-121">Requirements</span></span>  
  
|<span data-ttu-id="4a390-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4a390-122">MOF</span></span>|<span data-ttu-id="4a390-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4a390-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4a390-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="4a390-124">Namespace</span></span>|<span data-ttu-id="4a390-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4a390-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a390-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a390-126">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
