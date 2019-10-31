---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198421"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP : modifications de l’infrastructure du corps de la réponse

L’infrastructure de stockage d’un corps de réponse HTTP a changé. Si vous utilisez `HttpResponse` directement, vous ne devez pas apporter de modifications au code. En savoir plus si vous encapsulez ou remplacez `HttpResponse.Body` ou que vous accédez à `HttpContext.Features`.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Trois API sont associées au corps de la réponse HTTP :

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Nouveau comportement

Si vous remplacez `HttpResponse.Body`, il remplace l’intégralité de `IHttpResponseBodyFeature` par un wrapper autour de votre flux donné à l’aide de `StreamResponseBodyFeature` pour fournir des implémentations par défaut pour toutes les API attendues. La réinitialisation du flux d’origine rétablit cette modification.

#### <a name="reason-for-change"></a>Motif de modification

La motivation consiste à combiner les API de corps de réponse en une seule nouvelle interface de fonctionnalité.

#### <a name="recommended-action"></a>Action recommandée

Utilisez `IHttpResponseBodyFeature` là où vous utilisiez précédemment `IHttpResponseFeature.Body`, `IHttpSendFileFeature` ou `IHttpBufferingFeature`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
