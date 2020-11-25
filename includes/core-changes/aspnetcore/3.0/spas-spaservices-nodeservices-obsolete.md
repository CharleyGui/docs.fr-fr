---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032676"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>SPAs : SpaServices et NodeServices marqués comme obsolètes

Le contenu des packages NuGet suivants a été inutile depuis ASP.NET Core 2,1. Par conséquent, les packages suivants sont marqués comme obsolètes :

- [Microsoft. AspNetCore. SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Microsoft. AspNetCore. NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Pour la même raison, les modules NPM suivants sont marqués comme dépréciés :

- [ASPNET-angulaire](https://www.npmjs.com/package/aspnet-angular)
- [ASPNET-prérendu](https://www.npmjs.com/package/aspnet-prerendering)
- [ASPNET-WebPack](https://www.npmjs.com/package/aspnet-webpack)
- [ASPNET-WebPack-réagir](https://www.npmjs.com/package/aspnet-webpack-react)
- [domaine-tâche](https://www.npmjs.com/package/domain-task)

Les packages précédents et les modules NPM seront supprimés ultérieurement dans .NET 5.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les packages déconseillés et les modules NPM étaient destinés à intégrer des ASP.NET Core avec différentes infrastructures d’application Single-Page (SPA). Ces infrastructures incluent l’angle, la réaction et la réaction avec Redux.

#### <a name="new-behavior"></a>Nouveau comportement

Un nouveau mécanisme d’intégration existe dans le package NuGet [Microsoft. AspNetCore. SpaServices. extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) . Le package reste la base des modèles de projet angulaire et REACT depuis ASP.NET Core 2,1.

#### <a name="reason-for-change"></a>Motif de modification

ASP.NET Core prend en charge l’intégration avec différentes infrastructures d’application Single-Page (SPA), y compris angulaires, réagir et réagir avec Redux. Initialement, l’intégration à ces frameworks a été effectuée avec des composants spécifiques à ASP.NET Core qui géraient des scénarios tels que le prérendu côté serveur et l’intégration à WebPack. À l’époque, les normes du secteur ont changé. Chacun des frameworks SPA a publié ses propres interfaces de ligne de commande standard. Par exemple, l’interface CLI angulaire et Create-REACT-App.

Lorsque ASP.NET Core 2,1 a été publié en mai 2018, l’équipe a répondu au changement de normes. Un moyen plus récent et plus simple d’intégrer les chaînes propres aux frameworks SPA a été fourni. Le nouveau mécanisme d’intégration existe dans le package `Microsoft.AspNetCore.SpaServices.Extensions` et reste la base des modèles de projet angulaires et réagi depuis ASP.NET Core 2,1.

Pour préciser que les anciens composants spécifiques à ASP.NET Core sont sans importance et déconseillés :

- Le mécanisme d’intégration antérieur à 2,1 est marqué comme obsolète.
- Les packages de NPM de prise en charge sont marqués comme dépréciés.

#### <a name="recommended-action"></a>Action recommandée

Si vous utilisez ces packages, mettez à jour vos applications pour qu’elles utilisent les fonctionnalités suivantes :

- Dans le `Microsoft.AspNetCore.SpaServices.Extensions` Package.
- Fourni par les infrastructures SPA que vous utilisez

Pour activer des fonctionnalités telles que le prérendu côté serveur et le rechargement des modules à chaud, consultez la documentation de l’infrastructure SPA correspondante. Les fonctionnalités dans ne `Microsoft.AspNetCore.SpaServices.Extensions` sont *pas* obsolètes et continuent d’être prises en charge.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
