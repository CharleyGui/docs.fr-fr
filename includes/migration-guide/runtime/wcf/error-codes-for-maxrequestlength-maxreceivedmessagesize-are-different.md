---
ms.openlocfilehash: 26facb645de175d7ef0432394fc2b84f59e8437d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496515"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="fc37b-101">Les codes d’erreur pour maxRequestLength ou maxReceivedMessageSize sont différents</span><span class="sxs-lookup"><span data-stu-id="fc37b-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

#### <a name="details"></a><span data-ttu-id="fc37b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fc37b-102">Details</span></span>

<span data-ttu-id="fc37b-103">Les messages dans les services web WCF hébergés dans les services IIS (Internet Information Services) ou sur le serveur de développement ASP.NET qui dépassent maxRequestLength (dans ASP.NET) ou maxReceivedMessageSize (dans WCF) ont un code d’erreur différent. Le code d’état HTTP est passé de 400 (Demande incorrecte) à 413 (Entité de demande trop grande), et les messages qui dépassent le paramètre maxRequestLength ou maxReceivedMessageSize lèvent une exception <xref:System.ServiceModel.ProtocolException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="fc37b-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="fc37b-104">Cela inclut les cas dans lesquels le mode de transfert est Transmis en continu.</span><span class="sxs-lookup"><span data-stu-id="fc37b-104">This includes cases in which the transfer mode is Streamed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fc37b-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fc37b-105">Suggestion</span></span>

<span data-ttu-id="fc37b-106">Cette modification facilite le débogage dans les cas où la longueur du message dépasse les limites autorisées par ASP.NET ou WCF. Vous devez modifier tout code qui effectue un traitement en fonction d’un code d’état HTTP 400.</span><span class="sxs-lookup"><span data-stu-id="fc37b-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>

| <span data-ttu-id="fc37b-107">Name</span><span class="sxs-lookup"><span data-stu-id="fc37b-107">Name</span></span>    | <span data-ttu-id="fc37b-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="fc37b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fc37b-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="fc37b-109">Scope</span></span>   |<span data-ttu-id="fc37b-110">Edge</span><span class="sxs-lookup"><span data-stu-id="fc37b-110">Edge</span></span>|
|<span data-ttu-id="fc37b-111">Version</span><span class="sxs-lookup"><span data-stu-id="fc37b-111">Version</span></span>|<span data-ttu-id="fc37b-112">4,5</span><span class="sxs-lookup"><span data-stu-id="fc37b-112">4.5</span></span>|
|<span data-ttu-id="fc37b-113">Type</span><span class="sxs-lookup"><span data-stu-id="fc37b-113">Type</span></span>|<span data-ttu-id="fc37b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="fc37b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fc37b-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="fc37b-115">Affected APIs</span></span>

<span data-ttu-id="fc37b-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="fc37b-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
