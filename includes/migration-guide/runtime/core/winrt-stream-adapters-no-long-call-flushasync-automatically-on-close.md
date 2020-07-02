---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619997"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Les adaptateurs de flux WinRT n’appellent plus FlushAsync automatiquement lors de la fermeture

#### <a name="details"></a>Détails

Dans les applications du Windows Store, les adaptateurs de flux Windows Runtime n’appellent plus la méthode FlushAsync à partir de la méthode Dispose.

#### <a name="suggestion"></a>Suggestion

Cette modification devrait être transparente. Les développeurs peuvent rétablir le comportement précédent en écrivant du code comme le suivant :<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Mode transparent|
|Version|4.5.1|
|Type|Runtime|
