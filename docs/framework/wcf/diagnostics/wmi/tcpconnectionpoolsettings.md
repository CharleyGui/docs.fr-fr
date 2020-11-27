---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: de00cac851e4c6d0fd6df16f3a01b65bb5f43415
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294675"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="420ed-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="420ed-102">TcpConnectionPoolSettings</span></span>

<span data-ttu-id="420ed-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="420ed-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="420ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="420ed-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="420ed-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="420ed-105">Methods</span></span>  

 <span data-ttu-id="420ed-106">La classe TcpConnectionPoolSettings ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="420ed-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="420ed-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="420ed-107">Properties</span></span>  

 <span data-ttu-id="420ed-108">La classe TcpConnectionPoolSettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="420ed-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="420ed-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="420ed-109">GroupName</span></span>  

 <span data-ttu-id="420ed-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="420ed-110">Data type: string</span></span>  
  
 <span data-ttu-id="420ed-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="420ed-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="420ed-112">Nom de groupe du pool de connexions utilisé par l'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="420ed-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="420ed-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="420ed-113">IdleTimeout</span></span>  

 <span data-ttu-id="420ed-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="420ed-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="420ed-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="420ed-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="420ed-116">Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="420ed-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="420ed-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="420ed-117">LeaseTimeout</span></span>  

 <span data-ttu-id="420ed-118">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="420ed-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="420ed-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="420ed-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="420ed-120">Période maximale d'exécution de l'opération de bail avant expiration du délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="420ed-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="420ed-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="420ed-121">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="420ed-122">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="420ed-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="420ed-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="420ed-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="420ed-124">Nombre maximal de connexions sortantes pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="420ed-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="420ed-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="420ed-125">Requirements</span></span>  
  
|<span data-ttu-id="420ed-126">MOF</span><span class="sxs-lookup"><span data-stu-id="420ed-126">MOF</span></span>|<span data-ttu-id="420ed-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="420ed-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="420ed-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="420ed-128">Namespace</span></span>|<span data-ttu-id="420ed-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="420ed-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="420ed-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="420ed-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
