---
ms.openlocfilehash: 0c3876d30a80501a89f3a37ce24e2f71122c1b44
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497498"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="8b9b0-101">L’objet System.ServiceModel.Web.WebServiceHost n’ajoute plus de point de terminaison par défaut</span><span class="sxs-lookup"><span data-stu-id="8b9b0-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="8b9b0-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8b9b0-102">Details</span></span>

<span data-ttu-id="8b9b0-103">L’objet <xref:System.ServiceModel.Web.WebServiceHost> n’ajoute plus de point de terminaison par défaut si un point de terminaison explicite a été ajouté par le code de l’application.</span><span class="sxs-lookup"><span data-stu-id="8b9b0-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8b9b0-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8b9b0-104">Suggestion</span></span>

<span data-ttu-id="8b9b0-105">Si les utilisateurs s’attendent à pouvoir se connecter à un point de terminaison par défaut alors que d’autres points de terminaison explicites ont été ajoutés à <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, les points de terminaison par défaut doivent également être ajoutés explicitement (à l’aide d’<xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="8b9b0-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="8b9b0-106">Name</span><span class="sxs-lookup"><span data-stu-id="8b9b0-106">Name</span></span>    | <span data-ttu-id="8b9b0-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="8b9b0-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8b9b0-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="8b9b0-108">Scope</span></span>   |<span data-ttu-id="8b9b0-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="8b9b0-109">Minor</span></span>|
|<span data-ttu-id="8b9b0-110">Version</span><span class="sxs-lookup"><span data-stu-id="8b9b0-110">Version</span></span>|<span data-ttu-id="8b9b0-111">4,5</span><span class="sxs-lookup"><span data-stu-id="8b9b0-111">4.5</span></span>|
|<span data-ttu-id="8b9b0-112">Type</span><span class="sxs-lookup"><span data-stu-id="8b9b0-112">Type</span></span>|<span data-ttu-id="8b9b0-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="8b9b0-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8b9b0-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="8b9b0-114">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`

-->
